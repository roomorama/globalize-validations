# globalize-validations

[![Build Status](https://travis-ci.org/roomorama/globalize-validations.png?branch=master)](https://travis-ci.org/roomorama/globalize-validations)

Provides a uniqueness validator which can be used with globalize translated models.

## Compatibility

Works with rails 3.1 and 3.2.

Rails 3.0 is not fully supported (case insensitive validation doesn't work).

The validator is based on the activerecord 3.2 uniqueness validator.


## Installation

Add this line to your application's Gemfile:

    gem 'globalize-validations'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install globalize-validations

## Usage

Provides a `GlobalizedUniquenessValidator` which checks whether
the value of the specified attributes are unique across the system.

See validates_uniqueness_of in ActiveRecord::Validations::ClassMethods for further explanation.
This validator basically works the same, but additionally respects globalize model translations.
Also, you can use :locale when specifying the :scope option. This will scope the validation to the current locale.

For instance, if you want to validate that a product title is unique in each locale:

    class Product < ActiveRecord::Base
      translates :title
      validates_globalized_uniqueness_of :title, :scope => :locale
    end

Or:

    class Product < ActiveRecord::Base
      translates :title
      validates :title, :globalized_uniqueness => {:scope => :locale}
    end

## Todo / Known Issues

* Doesn't work yet with rails 3.0 when case_sensitive is set to false
* Might not yet work correctly with serialized attributes which are translated (haven't tested that yet)

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
