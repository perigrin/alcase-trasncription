# Install Perl

First if you're on a unix system (MacOS users this includes you) check to see
if `perl` is already installed. It might actually be. It was pretty ubiquitous
at one point in time. Open up a Terminal and run:

```
which perl
````

If you get something like the following you're good.

```
[perigrin@miho alcase-trasncription]$ which perl
/usr/bin/perl
```

If not then you'll need to install Perl. If you know how to install packages on
your system, please do that. If not you may want to take a moment and read
through the following instructions for your platform and make sure you
understand them. Things can get much more complicated from here and having a
good grasp on the command line is important.


## Installing for Unix-like Operating Systems (inclusing OSX)

Copy and run the following lines. These are adapted from the [plenv instructions](https://github.com/tokuhirom/plenv).
```
git clone https://github.com/tokuhirom/plenv.git ~/.plenv
echo 'export PATH="$HOME/.plenv/bin:$PATH"' >> ~/.bash_profile
git clone https://github.com/tokuhirom/Perl-Build.git ~/.plenv/plugins/perl-build/
echo 'eval "$(plenv init -)"' >> ~/.bash_profile
exec $SHELL -l
plenv install perl-5.32.0
plenv rehash
plenv use perl-5.32.0
```

This will install the latest (at the time of this writing) version of perl and
the plenv utility to manage custom perl installations, making it easier to
update as new versions are released.

## Installing for Windows

[TODO: Install instructions for Strawberry]

## Perl Utilities

There are a couple tools that don't come with Perl that are useful to have and
that we will use copiously in this book. First we will install a simple CPAN
client, we're going with `cpanm`. If you installed perl using the `plenv`
instructions above you can have plenv install it for you:

````
plenv install-cpanm
````

Otherwise you can just download the script from it's website:

```
curl https://cpanmin.us -o cpanm
chmod +x cpanm
mv cpanm /usr/local/bin/cpanm
```

### Carton

Perl by long tradition tries to install things at the system level, that is for
the whole computer. This can be problematic when you have several different
Perl applications with different requirements going at the same time. We're
going to use `Carton` to keep local copies of our dependencies and track them
in a single file named `cpanfile`. We will install carton globally so we can
use it everywhere.

```
cpanm Carton
```

### perltidy

Next is `perltidy`, a code formatter for Perl. This helps us ensure that the
code all matches a common style. If you look at the documentation for
`perltidy` you'll see it is very configurable but for now we'll just use the
defaults. Let's use `cpanm` to install it globally as well. The package the
command belongs to is named `Perl::Tidy`.

```
cpanm Perl::Tidy
```

## Editor

You may notice I haven't reccomended an IDE or an editor for Perl. That's
because there isn't a single reccomendation I can make, lots of perl
programmers use lots of different things. I use vim, if you don't have a
preference I've heard good things about
[Visual Studio Code](https://code.visualstudio.com/) recently.
