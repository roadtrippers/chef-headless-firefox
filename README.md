headless-firefox Cookbook
=========================

Install and prepare firefox (or iceweasel) for cucumber testing.

Inspiration from [this blog
post](http://blog.aentos.com/post/4368402854/easy-setup-for-your-cucumber-scenarios-using-the).

Requirements
------------

Currently only tested on Debian.  Should also work on other Debian flavored
distros.

Usage
-----

Simply add ```recipe[headless-firefox]``` to your run list.  In your Cucumber
settings env setup you'll need to add:

    Before('@selenium') do
      if ENV["SELENIUM_HEADLESS"] == 'true'
        require "headless"
        @headless = Headless.new
        @headless.start
      end
    end
 
    After('@selenium') do
      @headless.destroy if @headless.present?
    end

Contributing
------------

1. Fork the repository on Github
2. Create a named feature branch (like `add_component_x`)
3. Write you change
4. Write tests for your change (if applicable)
5. Run the tests, ensuring they all pass
6. Submit a Pull Request using Github

License and Authors
-------------------

See [LICENSE](LICENSE).
