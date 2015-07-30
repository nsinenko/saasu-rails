## Ruby Software Development Kit for Saasu API
This repository is a version of the Saasu software development kit in the Ruby language, for working with the Saasu API.
For help on the API itself, you can look at the [help documentation](https://api.saasu.com/).

[![Gem Version](https://badge.fury.io/rb/saasu2.svg)](http://badge.fury.io/rb/saasu2)
[![Build Status](https://travis-ci.org/nsinenko/saasu-rails.svg?branch=master)](https://travis-ci.org/nsinenko/saasu-rails)

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'saasu2'
```

And then execute:

    $ bundle

Create an initializer file with your Saasu configuration eg config/initilizers/saasu.rb
```ruby
require 'saasu'

Saasu::Config.configure do |c|
  c.username = 'username@email.com'
  c.password = 'password'
  c.file_id = 1234 # Your Saasu FileId can be found at
end
```

You're now ready to connect your app to Saasu.

## Usage

You can access the following object types:
- Saasu::Account
- Saasu::Company
- Saasu::Contact
- Saasu::Invoice
- Saasu::InvoiceAttachment
- Saasu::Item
- Saasu::Payment
- Saasu::TaxCode

Usage examples:

```ruby
# get all contacts
contacts = Saasu::Contact.all

# find a contact by id
contact = Saasu::Contact.find(123)

# save.contact
contact.given_name = 'New Name'
contact.save

# delete contact
contact.delete

# create new contact
new_contact = Saasu::Contact.create({ GivenName => 'User' })

# filter records, for a list of available filters for each object see https://api.saasu.com
contact = Saasu::Contact.where(GivenName: 'John')

# get attributes
contact.id
contact['Id']

# set attributes
contact.given_name = 'Nick'
contact['GivenName'] = 'John'

# get all attributes
contact.attributes
```

Note - Saasu uses .NET naming convention for fields and filters eg GivenName, LastModifiedDate.

## Contributing

1. Fork it ( https://github.com/saasu/saasu2-ruby/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
