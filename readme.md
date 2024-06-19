# Guides to make your own gem

## Create gemspec file

**user.gemspec**
The gemspec defines what's in the gem, who made it, and the version of gem. It's also your interface to RubyGems.org

```
Gem::Specification.new do |s|
s.name        = "user_greeting"
s.version     = "0.0.1"
s.summary     = "User Greeting"
s.description = "Greet the user!"
s.authors     = ["Bikash Shrestha"]
s.email       = "shresthabikash2073@gmail.com"
s.files       = Dir["lib/*.rb"]
s.homepage    = "https://rubygems.org/gems/user_greeting"
s.license     = "MIT"
end
```

## Create file lib/user.rb

_lib/user.rb_

```
class User
  def self.greet name
     puts "Hello, #{name}"
  end
end
```

### Structure look like the following

```
.
├── lib
│   └── user.rb
├── .ruby-version
└── user.gemspec
```

# Specify local ruby version

`rbenv local 3.1.2` -> this creates `.ruby-version` file

# Create gem

After you've created a gemspec, you can build a ruby gem from it. Then you can install the generated gem locally to test it out.

To build gem run: `gem build user.gemspec`

To install gem run: `gem install user_greeting-0.0.1.gem`

# Testing your gem

Of course, the smoke test isn't over yet: the final step is to **require** the gem and use it:

```
$ irb
irb(main):004:0> require "user"
=> false
irb(main):005:0> User.greet "Bikash Shrestha"
Hello, Bikash Shrestha
=> nil
```

# Publish Gem

To publish your gem, you'll need to create an account on RubyGems.org.

After creating an account, you can push your gem to RubyGems.org using the following commands:

Sign in using `gem signin` (this will ask your email/username and password on command prompt)

`gem push user_greeting-0.0.1.gem`

Install your gem : `gem install user_greeting`

# References

[Ruby Gem Basics](https://guides.rubygems.org/make-your-own-gem/)

[Specification Ref.](https://guides.rubygems.org/specification-reference/)
