---
title: "[SOLVED] VHS to DVD"
date: 2007-07-05
forum: Multimedia Production
---

### Post by Super TWiT on 2007-07-05
I have been looking for an application to convert my VHS tapes to DVD.  I have already found the editing software I need (Avidemux) and the DVD authoring program (DeVeDe) and my TV card is already configured.  I have tested it on TVTime.  However, I haven't been able to find the capturing software.  I have tried Mythtv, but you can only schedule recordings on that.  I have also tried Xawtv, but the video is captured at 12 frames per second.

---

### Post by bridd on 2007-07-08
> **Super TWiT said:**
> I have been looking for an application to convert my VHS tapes to DVD.  I have already found the editing software I need (Avidemux) and the DVD authoring program (DeVeDe) and my TV card is already configured.  I have tested it on TVTime.  However, I haven't been able to find the capturing software.  I have tried Mythtv, but you can only schedule recordings on that.  I have also tried Xawtv, but the video is captured at 12 frames per second.

Have you tried Kino ? I'm not sure if that's just firewire or can do capture cards as well (as I don't have a capture card myself) but it's probably worth a try

---

### Post by newlinux on 2007-07-08
Do you have a hardware encoding card? If so you could just hit play on your vcr when it is plugged into the input of the capture card and then type:

```

cat /dev/video0 > file.mpg

```
and hit Ctrl-C when you are done (or use a script of the "at" command to kill the recording at the right time).

Replace video0 which whatever video device corresponds to your capture card.
Otherwise in myth you can schedule a manual recording to do the job.

---

### Post by fsman on 2007-07-09
I use mjpegtools/lavrec to capture the video via analogue capture card (via composite input) and line-in (sound).
Then simply open with avidemux - apply the dvd autoformat to create the dvd compatable mpeg and you are done.

PS - I create a DVD iso from the mpeg using dvdstyler - keeps everything GTK/Gome

---

### Post by Super TWiT on 2007-07-10
Thanks for posting!:KS  Sorry I took so long to respond.  My capture card is only analogue and doesn't have hardware encoding on it. (It was cheap $20 on Tigerdirect:))  And I have no idea how to use mpegtools.  Is it command line only?

---

### Post by dabl on 2007-07-10
Trying my new PVR-150.  Hardware Device manager screenshot attached.  The device shows up in 4 lines:

/dev/vbi0
/dev/video0
/dev/video24
/dev/video32

I tried newlinux's advice, ```
cat /dev/video0 > test.mpg
``` and the output file plays like a videotape, but black and noisy (no picture or audio).  I've changed the VCR from Channel 4 to 3 and back again -- I think they said the PVR-150 defaults to Channel 4.  Makes no difference.  I tried the other devices, and got outputs that don't appear to be analog video -- not sure what it is.

I tried using a nice RF coax cable, and also the composite video input -- doesn't seem to matter.

Anyone got a clue what I can do to get this thing working? Thank you!

dabl

---

### Post by Super TWiT on 2007-07-10
Have you tried testing the configuration with TVtime?  If you get a picture and sound here, than you know that the capture card is configured properly and is functional.  TVtime is in the universe repositories.

---

### Post by dabl on 2007-07-10
I'm on it ....

---

### Post by Super TWiT on 2007-07-17
I have found an application!:KS  It is called Gv4l.  It seems to be working pretty well.  Except for the fact that I can't get it to capture at any resolution higher than 384x288 or else it gives me a green screen.  However, I have started another thread on that issue: [http://ubuntuforums.org/showthread.php?t=502770](http://ubuntuforums.org/showthread.php?t=502770)

---

### Post by dabl on 2007-07-17
Thanks for that -- I'm gonna try it.  Been beating my brains out on my PVR-150 for days.  I think it is set up correctly -- scantv works, ivtv-tune works, did enough research to realize that tvtime will never run it (tvtime won't play mpeg2), mplayer appears not to decode mpeg2 by default, and I dunno what it takes to make it do that on the fly.

Anyway, I'm trying it your way tonight!

Thanks!  :popcorn:

---

### Post by dabl on 2007-07-21
Here is how I finally got my PVR-150 to capture from a VHS VCR:

[http://kubuntuforums.net/forums/index.php?topic=3085164.msg80411#msg80411](http://kubuntuforums.net/forums/index.php?topic=3085164.msg80411#msg80411)

:)

---

