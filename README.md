# 🦀 wthrr-the-weathercrab

`wthrr` lives in your terminal and her passion is meteorology.

If you spent some time in the CLI it comes in handy to have a little companion nearby who knows about the weather.

## Contents

-  [How to use?](https://github.com/tobealive/wthrr-the-weathercrab#how-to-use)
-  [Requirements](https://github.com/tobealive/wthrr-the-weathercrab#requirements)
-  [Installation](https://github.com/tobealive/wthrr-the-weathercrab#installation)
-  [Outlook](https://github.com/tobealive/wthrr-the-weathercrab#outlook)

## How to use?

**Just call**

```
wthrr
```

When no arguments are specified wthrr will use the [config](https://github.com/tobealive/wthrr-the-weathercrab#config) that's saved as default.<br>
If you don't have anything configured yet, wthrr can try to search for a weather station close to you and save the last searched location as default.

**Its always possible specify a address with your call.** E.g.,

```
wthrr melbourne
```

Depending on the searched location, you might want to be be more specific.
For example, the call above will give you Melbourne in Australia. If you are aiming for Melbourne in the US, ask for `melbourne,florida`.
For cities containing spaces, write it separated with a dash or wrap it in quotation marks (e.g., `new-york` or `'new york'`).

If there is a default address configured, but you want wthrr to explicitly search for a nearby weather station, you can do so by calling:

```
wthrr auto
```

### Find further usage parameters in the help information

```
> wthrr -h

Usage: wthrr [OPTIONS] [ADDRESS]

Arguments:
  [ADDRESS]  Address to check the weather for

Options:
  -f, --forecast             Include the forecast for one week
  -u, --units [<UNITS>...]   Units for temperature and/or speed [possible values: (c)elsius, (f)ahrenheit, kmh, mph, (kn)ots, ms]
  -l, --language <LANGUAGE>  Output language
  -g, --greeting             Toggle greeting message
  -s, --save                 Save the supplied values as default
  -r, --reset                Wipe wthrr's configuration data
  -h, --help                 Print help information
  -V, --version              Print version information
```

---

### Showcase

_First run example asking to include the forecast of the week:_
<img src="preview/first-run-example.png" />

### Config

Adding the `-s` flag will save the values from a run as default.
E.g., on GNU/Linux the location of the config file usually is: `~/.config/weathercrab/wthrr.toml`

You probably don't have to bother with the config file itself, as you can save your defaults directly via the terminal.
For the sake of completeness, the config contents are as follows.

```toml
# Address to check the weather for
address = 'berlin,de'
# Measurement units. Temperature: [celsius, fahrenheit] Speed: [kmh, mph, knots, ms]
units = 'celsius,kmh'
# Greeting message display [true, false]
greeting = true
# Language of the output: [de, pl, ...]
language = 'en'
```

## Requirements

This app uses font icons and emojis. Therefore, a nerd variant of your font is required to correctly display the output.
https://github.com/ryanoasis/nerd-fonts

Some terminal emulators might require to additionally add/prioritize emojis in their font config.

<sub>If you are using brew, this gist contains easily digestible 🍝 copy-pasta for nerd-font installation.<br>
https://gist.github.com/davidteren/898f2dcccd42d9f8680ec69a3a5d350e</sub>

## Installation

Without the rust toolchain installed, grabbing a binary from the [release](https://github.com/tobealive/wthrr-the-weathercrab/releases) page might be your way to go.

Otherwise, rusts package manager is a simple way to install the binary crate:

```
cargo install wthrr
```

If you are on NetBSD, a package is available from the official repositories.
To install it, simply run:

```
pkgin install wthrr
```

A Nix flake is also avaiable:

```
nix profile install "github:tobealive/wthrr-the-weathercrab"
```

```
nix run "github:tobealive/wthrr-the-weathercrab"
```

### Build from source

Another way is to compile the app yourself.
Assuming the rust toolchain is installed on your system, just clone the repo and build the release version.

```
git clone https://github.com/tobealive/wthrr-the-weathercrab.git
cd wthrr-the-weathercrab
cargo build --release
```

When the build has finished, you'll find the `wthrr` binary inside the `./target/release` directory

## Outlook

-  [x] Multilang support
-  [ ] Allow to show more / customized meteorological data
   -  [ ] Custom forecast days
   -  [x] Modify speed units
-  [ ] Theme variants

<br>
Contributions like 🐛bug reports, ⭐️stars and 💡suggestions are welcome alike!

## Credits

-  The app uses the open-source weather API for non-commercial use provided by [Open Meteo](https://open-meteo.com/en)
