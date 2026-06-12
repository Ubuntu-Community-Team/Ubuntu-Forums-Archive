---
title: "Looking for a command line sound recorder application"
date: 2010-08-20
forum: Multimedia Software
---

### Post by MakOwner on 2010-08-20
I like to record a local radio show off the air and listen to it later, when I can hear the full show.

To do this, I have been using a fiesty installation (no X server installed, so no gnome or KDE) and using an application called 'sound-recorder'.

This is getting old and tends to break when I ask it to do a recording that results in an output file of 2,147,483,647 bytes or more.
I'm writing to an EXT3 on a 32 bit OS, so it may be a file system issue as opposed to the recorder.  I digress.

I'm looking for a command line to tool to record line/mic input from the sound card so that I can batch it in a cron job.

This is from the README in the package sound-recorder.
The links are dead and I don't see any mention in Google.

> 
sound-recorder for DEBIAN
----------------------

This package is maintained and created by B.Warmerdam. Sources are uploaded
to [ftp://sunsite.unc.edu/pub/Linux/apps/sound/recorder](ftp://sunsite.unc.edu/pub/Linux/apps/sound/recorder) and are also available
on [http://www.xs4all.nl/~bartw/recorder.html](http://www.xs4all.nl/~bartw/recorder.html) (Homepage author (me)).

Bart Warmerdam <BartW@Debian.org>, Sat,  1 Aug 1998 22:08:02 +0200



Is there a comparable utility that runs under 10.4 that I can use for batch jobs?

---

### Post by andrew.46 on 2010-08-22
Hi MakOwner,

> **MakOwner said:**
> I like to record a local radio show off the air and listen to it later, when I can hear the full show.

As do I every Sunday night:

Slackware and "For The God Who Sings"
[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

This does not use the sound card as you have mentioned, but I imagine you are referring to a streaming broadcast from a radio station? BTW just ignore all the slackware references on that page :).

Andrew

---

### Post by MakOwner on 2010-08-22
> **andrew.46 said:**
> Hi MakOwner,



As do I every Sunday night:

Slackware and "For The God Who Sings"
[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

This does not use the sound card as you have mentioned, but I imagine you are referring to a streaming broadcast from a radio station? BTW just ignore all the slackware references on that page :).

Andrew

In this case the broadcast is FM only; I use a small AM/FM receiver with a headphone out jack plugged into the line-in on the sound card.

---

### Post by ron999 on 2010-08-22
Hi

**arecord** will probably do the job.

This is the basic command for a (huge) wav file:-

```
arecord -f cd out.wav

```
A command like this will pipe it to an encoder instead:-
```
arecord -f cd - | lame - out.mp3
```

And gogo-no-coda is a faster mp3 encoder:-
```
arecord -f cd - | gogo stdin out.mp3
```
:D


It's a while since I've used this method.
I got the idea from
Here:-[http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/]("http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/")
**(This helps to set up alsamixer if needed).**
and 
Here:-[http://alsa.opensrc.org/index.php/Record_from_pcm]("http://alsa.opensrc.org/index.php/Record_from_pcm")

These days I use SoundRecorder or mp3DirectCut (with Wine).
But I don't know how to use either of them from the command line.

**gogo-no-coda** might be in the Ubuntu repo.
If not, google for it at RareWares.
8-)

---

### Post by texaswriter on 2010-08-23
```
aptitude search arecord
p qarecord
```

---

