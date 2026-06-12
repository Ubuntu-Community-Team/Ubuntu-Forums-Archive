---
title: "Flexible slideshow app"
date: 2010-04-24
forum: Multimedia Software
---

### Post by jimhenry on 2010-04-24
I'm wondering what other image viewers out there might have better, more flexible slideshow functions than Eye of Gnome.  It's -s function takes the full screen and displays the images from files listed on the command line one after another until a key is pressed; but it lacks certain features:

1. It always shrinks huge images to fit the screen and stretches small images to fit the screen.  Usually the former behavior is desirable, and sometimes the latter; but stretching very small images makes them terribly blurry.  I'd like to turn these behaviors on and off with command line switches.

2. The amount of time each image is displayed seems to be hard-coded; if there's a way to change it, I haven't figured it out.

3. It always displays the files it's given on the command line in alphabetical (ASCII) order of filename, no matter what order they're actually listed in, and it doesn't have a randomize function.  I've coded a workaround wrapper script to make it show images in random order, so I no longer need this strictly, but it would be nice to have.

4. A random slideshow app my Dad has on his Windows machine has the option to show the full pathname of the image it's showing along with the image, semitransparently layered onto the image in a corner.  That would be nice when doing a random slideshow of /home/username/Pictures and all subdirectories.

Here's the workaround script I wrote to make eog -s show images in random order:

```

#!/bin/bash

if [ -z "$1" ] ; then
    # the entire list of 5000+ pictures in the ~/Pictures hierarchy is so long it
    # exceeds xargs' max command length and xargs will thus start eog three times successively
    # thus the --limit argument
    find ~/Pictures \( -iname \*.jpg -or -iname \*.png \) -print0 | make-random-linkset.pl -0 --limit=2000 --tempdir=/tmp/pics_$RANDOM | xargs --verbose -0 eog -s
else
    if ! pushd $1 ; then
    echo Directory $1 not found or not accessible
    exit
    else
    find  ./  \( -iname \*.jpg -or -iname \*.png \)  -print0  |  xargs -0 eog -s
    popd
    fi
fi

```The way this is coded, it does a random slideshow of the entire Pictures hierarchy if it's called with no arguments, or an ordered-by-filename slideshow of a specified directory and its subdirectories if called with a directory name argument.  That's usually the desired behavior; I've been thinking about adding an argument to allow forcing random behavior when working with a specified directory, too.  But getting a better slideshow app would be easier.

The make-random-linkset.pl referred to in the script above looks like this:

```

#! /usr/bin/perl -w

# reason for --limit option:
# when making a slideshow with >5000 pictures the total of filenames is over the limit for
# xargs to do a single eog -s command so it does it three or four times successively.
# not what we want.

use strict;

srand;

my $delim = "\n";

use Getopt::Long;
Getopt::Long::Configure('bundling');

my $nulldelim = 0;
my $files_limit = 0;
my $tmpbase = defined $ENV{TMPDIR}  ?  $ENV{TMPDIR}  :  "/tmp";
my $tmpdir = $tmpbase . "/randlinkset" . time() . "_" . int rand 1000;

GetOptions(
    '0|null' => \$nulldelim,
    'l|limit=i'  => \$files_limit,
        'd|tempdir=s' => \$tmpdir,
);

if ( $nulldelim ) {
    $/ = "\0";
    $delim = "\0";
}

mkdir $tmpdir     or die "can't create dir $tmpdir";

my @filenames = <>;

my $count = 0;
foreach ( sort { int ( rand 101 ) - 50 } @filenames ) {
    chomp;
    # match every nonslash char after the last slash on the line
    m/\/([^\/]+)$/i;
    my $fn = $1;
    if ( not defined $fn ) {
    $fn = $_;
    }
    my $tmplink = $tmpdir . "/" . int(rand(2000000000)) . "_" . $fn;
    symlink $_, $tmplink    or die "can't create symlink from $_ to $tmplink";
    print $tmplink . $delim;
    if ( $files_limit  &&  ++$count >= $files_limit ) {
    last;
    }
}

```These scripts are released under a Creative Commons license.

---

### Post by luopio on 2010-05-06
Valid points. What I've discovered is that gnome entirely misses a photo application that does a "pretty slideshow". Nothing too fancy, maybe just a fade between photos, perhaps a bit of ken burns here and there.

Eog would be perfect for this as I'd like to use something light to present my photos and in addition I need the ASCII-sorting as that gives me the option to put stuff in between. Use case here is map locations between holiday pics.

The Slideshow Shuffle didn't do the random thing you wanted? ([http://live.gnome.org/EyeOfGnome/Plugins](http://live.gnome.org/EyeOfGnome/Plugins))

I'm planning on writing a plugin for effects. A joke to do in something like p5, but dunno about eog. Hard to find any decent docs..

---

