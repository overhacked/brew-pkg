# brew-pkg

brew-pkg is a Homebrew external command that builds an OS X installer package from a formula. The formula must first already be installed on the system.

## Usage

Assuming nginx is already installed:

`brew pkg nginx`
<code><pre>==> Creating package staging root using Homebrew prefix /usr/local
==> Staging formula nginx
==> Plist found at homebrew.mxcl.nginx, staging for /Library/LaunchDaemons/homebrew.mxcl.nginx.plist
==> Building package nginx-1.2.6.pkg</pre></code>

It can also automatically include the formula's dependencies:

`brew pkg --with-deps ffmpeg`
<code><pre>==> Creating package staging root using Homebrew prefix /usr/local
==> Staging formula ffmpeg
==> Staging formula pkg-config
==> Staging formula texi2html
==> Staging formula yasm
==> Staging formula x264
==> Staging formula faac
==> Staging formula lame
==> Staging formula xvid
==> Building package ffmpeg-1.1.pkg</pre></code>

## Installing it

brew-pkg is available from my [formulae tap](https://github.com/timsutton/homebrew-formulae). Add the tap:

`brew tap timsutton/formulae`

Then install as any other formula:

`brew install brew-pkg`

## Extras

If a formula has defined a launchd plist, brew-pkg will also install this to the package's root in `/Library/LaunchDaemons`.

You can also define a custom identifier prefix in the reverse-domain convention with the `--identifier-prefix` option, ie. `brew pkg --identifier-prefix org.nagios nrpe`. If there is a launchd plist defined, this same prefix is currently _not_ applied to the plist.

You can set the path to custom preinstall and postinstall scripts with the `--scripts` option. It is similar to the `--scripts`option of `pkgbuild`.
