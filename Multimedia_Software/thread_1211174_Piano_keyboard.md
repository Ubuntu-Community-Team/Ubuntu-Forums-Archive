---
title: "Piano keyboard"
date: 2009-07-12
forum: Multimedia Software
---

### Post by luiznetto on 2009-07-12
I am a music student, and I need a nice piano keyboard that will help me read musical scores. After a lot of searching, I found this:

[http://www.bgfl.org/bgfl/custom/resources_ftp/client_ftp/ks2/music/piano/index.htm](http://www.bgfl.org/bgfl/custom/resources_ftp/client_ftp/ks2/music/piano/index.htm)

It works fine, to a certain extent, but I was looking for a wider range (this one has one octave and a half) and a program that told me the exact pitch of the note (whether it is, for instance, C1 or C4, etc; and if possible the frequency of the sound in hertz too). So I found and installed vkeybd. The problem is, it shows a nice piano keyboard onscreen, but no sound comes out of it. I googled "linux virtual keyboard", and it tells me to read 1000 pages of documentation, and perhaps the answer will be found somewhere in the middle of it, which is very discouraging.

So, does anybody have any idea how to make vkeybd to actually produce sound? Why is it that vkeybd doesn't work, and the virtual online keyborad in the link I show above works?

Thank you for your help.
Luiz

---

### Post by raboofje on 2009-07-12
> I found and installed vkeybd. The problem is, it shows a nice piano keyboard onscreen, but no sound comes out of it.

This is correct: vkeybd is a MIDI keyboard, and produces MIDI messages. You need some kind of synth to produce actual sounds.

A commonly-suggested synth is 'zynaddsubfx'. Install it, start it, and connect vkeybd to it.

To make the connection, you can for example use the 'alsa' tab of the 'connections' window of qjackctl.

> **luiznetto said:**
> I was looking for a wider range (this one has one octave and a half) and a program that told me the exact pitch of the note (whether it is, for instance, C1 or C4, etc; and if possible the frequency of the sound in hertz too).

Shouldn't be too hard to write a script to print that from the information from aseqdump - look at [http://www.linuxmusicians.com/viewtopic.php?f=4&t=1518&st=0&sk=t&sd=a&hilit=amarok#p6714](http://www.linuxmusicians.com/viewtopic.php?f=4&t=1518&st=0&sk=t&sd=a&hilit=amarok#p6714) for an example if you're familiar with Perl.

---

### Post by raboofje on 2009-07-14
> **raboofje said:**
> This is correct: vkeybd is a MIDI keyboard, and produces MIDI messages. You need some kind of synth to produce actual sounds.

A commonly-suggested synth is 'zynaddsubfx'. Install it, start it, and connect vkeybd to it.

To make the connection, you can for example use the 'alsa' tab of the 'connections' window of qjackctl.

Described in more detail at [https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo)

> **luiznetto]I was looking for a wider range (this one has one octave and a half)[/quote]

Start vkeybd with '--octave' to specify the number of octaves - for example 'vkeybd --octave 5' for 5 octaves.

[quote=raboof][quote=luiznetto]a program that told me the exact pitch of the note (whether it is, for instance, C1 or C4, etc said:**
> 
Shouldn't be too hard to write a script to print that from the information from aseqdump

Getting back on that old promise:

```
#!/usr/bin/perl

use strict;

use IO::Pty;
use IPC::Open2;

my $pty = IO::Pty->new;
open2(">&" . fileno($pty), my $in, "aseqdump");
my $s = $pty->slave;

my @notenames = ( 'C-', 'C#', 'D-', 'Eb', 'E-', 'F-', 'F#', 'G-', 'G#', 'A-', 'Bb', 'B-' );

# taken from MIDI::Pitch - didn't want to add that dependency.
my $base_freq = 440;
sub pitch2freq {
    my $p = shift;

    return undef unless defined $p && $p =~ /^-?(\d+|\d*(\.\d+))$/;
    return exp((($p - 69) / 12) * log(2)) * $base_freq;
}


while (<$s>)
{
        if ($_ =~ /Note on(\w|\s)+\s+(\d+)(\w|\s)+\s+(\d+)/)
        {
                my $channel = $1;
                my $note = $2;

                my $notename = $notenames[$note % 12];
                my $octave = int($note / 12);
                my $freq = pitch2freq($note);

                print "Read note name $notename$octave, pitch $note, frequency $freq\n";
        }
}

```

Not as short and sweet as I hoped, but nice enough. Requires alsa-utils and IO::Pty, usually found in a package named something like libio-pty-perl (i'm not on ubuntu right now)

---

