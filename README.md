You should use protection!

This gem protects against typical web attacks.
Should work for all Rack apps, including Rails.

# Usage

Use all protections you probably want to use:

``` ruby
# config.ru
require 'rack/protection'
use Rack::Protection
run MyApp
```

Skip a single protection middleware:

``` ruby
# config.ru
require 'rack/protection'
use Rack::Protection, :except => :path_traversal
run MyApp
```

Use a single protection middleware:

``` ruby
# config.ru
require 'rack/protection'
use Rack::Protection::AuthenticityToken
run MyApp
```

# Prevented Attacks

## Cross Site Request Forgery

Prevented by:

* `Rack::Protection::AuthenticityToken` (not included by `use Rack::Protection`)
* `Rack::Protection::FormToken` (not included by `use Rack::Protection`)
* `Rack::Protection::JsonCsrf`
* `Rack::Protection::RemoteReferrer` (not included by `use Rack::Protection`)
* `Rack::Protection::RemoteToken`
* `Rack::Protection::HttpOrigin` (not included by `use Rack::Protection`)

## Cross Site Scripting

Prevented by:

* `Rack::Protection::EscapedParams` (not included by `use Rack::Protection`)
* `Rack::Protection::XSSHeader` (Internet Explorer only)

## Clickjacking

Prevented by:

* `Rack::Protection::FrameOptions`

## Directory Traversal

Prevented by:

* `Rack::Protection::PathTraversal`

## Session Hijacking

Prevented by:

* `Rack::Protection::SessionHijacking`

## IP Spoofing

Prevented by:

* `Rack::Protection::IPSpoofing`

# Installation

    gem install rack-protection

