# SimpleBillyAPI

Simplebilly API - Bookkeeping, CRM, ERP. Multi-tenant API: a tenant is isolated and routed by subdomain (or a configured custom domain) under the base domain.  ## Rate limiting All endpoints are rate-limited per client IP: **100 requests per minute** on API routes and **5 requests per minute** on authentication routes. Exceeding a limit returns &#x60;429 Too Many Requests&#x60;; the window resets after 60 seconds.

## Building

To install the required dependencies and to build the elixir project, run:

```console
mix local.hex --force
mix do deps.get, compile
```

## Installation

If [available in Hex][], the package can be installed by adding `simple_billy_api` to
your list of dependencies in `mix.exs`:

```elixir
def deps do
  [{:simple_billy_api, "~> 1.0.0"}]
end
```

Documentation can be generated with [ExDoc][] and published on [HexDocs][]. Once published, the docs can be found at
[https://hexdocs.pm/simple_billy_api][docs].

## Configuration

You can override the URL of your server (e.g. if you have a separate development and production server in your
configuration files).

```elixir
config :simple_billy_api, base_url: "https://demo.simplebilly.com"
```

Multiple clients for the same API with different URLs can be created passing different `base_url`s when calling
`SimpleBillyAPI.Connection.new/1`:

```elixir
client = SimpleBillyAPI.Connection.new(base_url: "https://demo.simplebilly.com")
```

[exdoc]: https://github.com/elixir-lang/ex_doc
[hexdocs]: https://hexdocs.pm
[available in hex]: https://hex.pm/docs/publish
[docs]: https://hexdocs.pm/simple_billy_api
