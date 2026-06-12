---
title: "tv-record : a set of scripts to record and convert dvb or analog TV"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by Jose Catre-Vandis on 2007-01-13
tv-record-convert scripts
~~~~~~~~~~~~~~~~~~~~~~~~

Version 0.02

Having enjoyed the audio-convert and video-convert scripts I thought
I would have a go at coming up with some scripts that would provide me
with a quick and dirty method of recording and encoding tv programs, having
been disappointed with the offering from programs in the Ubuntu repos,
with only Kaffeine coming close (and I use Ubuntu!).

To use these scripts I am assuming that you are running Ubuntu, already have a dvb/analog card
installed and up and running, to a greater or lesser degree, and that you are prepared
to do a little bit of work to get set up.

There are three main scripts, and you would use them depending on the type
of tv card you have on board. My card, an ASUS P7131 Dual, does both dvb
and analog, so I can make use of all three, but if you have only the analog,
you just use the analog script, and if you only have dvb, you use the dvb script.
The third script simply gives you options for either at the start, so you can use it
if you only have one type, but there is not much point in doing so!

You can have more than once instance of the scripts running (e.g. set up to record
different programs at different times in advance) but you cannot record two programs at the same
time, nor use analog and dvb at the same time, unless you have two or more cards on board,
even then, I can't test nor say if this would work?

The scripts use mplayer/mencoder to do most of the work, and most of the encoding is
in mpeg4 to avi files, but there is an option to save dvbstreams in their native ts format 

All files are saved to the installation directory by default.

There is a bit of work to do to get the scripts working in an environment other than mine:

You will need to edit the scripts to your channel listings, and although you can run from the CLI
you should set up a launcher. You will need zenity and mplayer/mencoder installed, and I suggest
you use something like Automatix/Automatix2 to install all the necessary codecs.

You can always edit the encoding scripts to your liking.

I can't see why anything in these scripts might make a mess of your system, but you will have to take them
as they are, fairly basic, and probably buggy, without a great deal of error checking,
but they work well on my Dapper machine. I cannot accept any responsibility for any problems or damage
caused to your hardware or software through use of this script.

Installation:

```
* Install any necessary programs and codecs
* Untar the file to a directory of your choosing.
* Make all the scripts executable
* Edit the dvb and / or analog script to adjust the channels
* Edit the analog script and adjust the chanlist setting
  in the encoding script (last line of file) to your region
* Ensure you have a channels.conf in your mplayer directory
  for dvb use. Edit the channels.conf to remove any spaces
  from channel names
* Set up a launcher to the tv-record-convert_0.02 script
  or
  for either of the two other scripts to suit your tv card
* Assumes you already have a working dvb or analog card
* make sure your PC clock is telling the right time and keeping time
  in order for delayed recordings to work well
```

Files:

```
tv-record-convert_0.02
dvb-record-convert_0.02
analogtv-record-convert_0.02
readme 
```

Future Development:

Probably not much, would be nice to get it all in one script
might improve the error checking and escapes, and will most
likely build a player script, to complement the recording scripts
May switch to VLC in order to allow for simultaneous watch and record

Bugs: please report to this forum thread on Ubuntuforums

Enjoy
Download here: [ATTACH]22936[/ATTACH]

---

