---
title: "Movie player does not play video"
date: 2010-08-12
forum: Multimedia Software
---

### Post by lwalper on 2010-08-12
Newbie here . . .

When I insert a movie DVD into the drive, the disk is read, a window pops up asking what software do I want to use (Open Movie Player is the default). I click use Open Movie Player and get "An error occurred could not read from resource" dialog - and the movie does not play.

The file manager reads the disk without any problem, so don't think it's a bad disk (and it plays in my WinXP machine). I checked in Synaptic and it appears that Totem and all the stuff that needs to be installed with Totem is there. Is there another player or some front end for totem that I don't have? In that initial screen asking for software choice, totem is not an optio n.

I've looked around in Medibuntu and it looks like all the needed files are already installed. Is there a different DVD player that needs to be installed?

---

### Post by lwalper on 2010-08-12
Just restarted the system and tried the Gnome Mplayer. The player opened, went through some contortions reading the disk, flipped up a about a 0.1 second image of the FBI warning image and then quit.

---

### Post by howefield on 2010-08-12
Have you been through the stuff here ?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

You might also try VLC, a fine media player.

---

### Post by lwalper on 2010-08-12
I've looked at the packages for installing various plugins - it seems they area already installed. I'm now in the process of installing VLC. Will see how that goes.

---

### Post by lwalper on 2010-08-12
I suppose this is progress - at least there's a semblance of a screen filled with a variety of little colored squares. Not quite what I had in mind, but it did seem to read the disk.

---

### Post by Paul S on 2010-08-12
Some of us using older hardware have had problems with dvd playback that can't be resolved.  So, if you're using an older pc that precedes SATA hardware, you may have to use windows, or ubuntu hardy.  But, after hardy, the new pata drivers are not able to play DVD's on older ATA / ide type drives.  But, everything else seems to work ok.

---

### Post by lwalper on 2010-08-12
I have also installed regionset and reset my DVD player to (1) (USA). Have installed libdvdread4, tried

chmod 660 /dev/sr0; chgrp cdrom /dev/sr0

as described on that page and get the message

Operation not permitted

So, installed kaffeine and xine. Xine opens OK, but when I try to read the disk I get the error message

"The source can't be read. Maybe you don't have enough rights for this, or source does not contain data."

Maybe I don't, maybe it doesn't?? The initial FBI warning screen does come up for a few seconds before that error message displays. There is a "More" button that displays a whole slew of messages - one of which is "throwing away image ... because it's too old." Well, that could be. It's a Jimmy Stewart movie done originally in 1962 - Mr Hobbs Takes a Vacation - nearly 50 years old.

---

### Post by lwalper on 2010-08-12
Have tried a couple of other DVDs and they play fine - though not in Movie Player. They do play in VLC and xine.

The Jimmy Stewart disk is a 20th Century Fox distribution.
"A Civil Action" (John Travolta) is a Paramont/Buena Vista disto
Ratatouille comes from Buena Vista (Disney) too

Nothing will play in Movie Player.

Maybe something in the disk encryption?:(

---

### Post by howefield on 2010-08-12
Try running the movie via a terminal command, might give you some clue as to how to progress.


Open a terminal and type

```
vlc pathtodvd
```

eg, for me it would look like vlc /media/HUNTERS_D1_PAL

HUNTERS_D1_PAL being the name of the DVD.

---

### Post by Yellow Pasque on 2010-08-12
You can probably fix your Totem issue by running:
```
gstreamer-properties
```
Try different video outputs (under the video tab) and select one that works.

---

### Post by lwalper on 2010-08-12
I think I fixed it. Kept looking around 

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/545681](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/545681)

See post #5 in that thread.

I needed to install gstreamer0.1.0-plugins-bad from some "restricted" Ubuntu repository. Now the player seems to work. Why is this file so difficult to find? Seems like it ought to be right there in Synaptic with all the other gstreamer plugins??

---

### Post by Yellow Pasque on 2010-08-12
gst-plugins-bad is installable "out of the box"

---

### Post by lwalper on 2010-08-13
Oops, I spoke too soon. Other DVD videos play, but Mr Hobbs still can't go on vacation. Kinda strange?

Sorry, I don't understand "out of the box". Do you mean on initial installation it *should* have automatically installed, but for some reason didn't?

---

### Post by lwalper on 2010-08-13
When I run

sudo apt-get upgrade

I get a response that the mplayer will be "kept back" from the upgrade. Is that a problem?

---

### Post by lwalper on 2010-08-13
howfield

When I run VLC from the prompt this is what I get:

leslie@leslie-laptop:~$ vlc /media/MRHOBBSTAKESAVACATION
VLC media player 1.0.6 Goldeneye
[0x8531148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/MRHOBBSTAKESAVACATION for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/leslie/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000048a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000062e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000537d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00005521
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00006454
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000065f8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00017098
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0001723c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x000183ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00018590
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00053717
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00053bad
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[0xb74008b0] main input error: ES_OUT_RESET_PCR called
[0xb74008b0] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x88652f8] spudec decoder error: i_x overflowed, 721 > 720
leslie@leslie-laptop:~$ 

It's all gobbldygook to me.

---

### Post by spcmediaco on 2010-10-20
any luck with this?

---

