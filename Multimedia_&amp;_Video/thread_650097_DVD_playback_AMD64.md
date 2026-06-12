---
title: "DVD playback AMD64"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by scamper_22 on 2007-12-25
HI all,

I just can't get DVD playback working on 64bit 7.10.

I have searched all over, and tried many things.

installing/reinstalling
gxine
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

Nothing seems to work.  At one point I did get the DVD to play, but then it would just quit after it got to to the title menu.  I haven't been able to get it to that state again.

If I use gxine and try to open a dvd, I just get 
The xine engine failed to start.
No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

Anyone think of anything I can do?
Or what diagnostic commands I can run?

Thanks

---

### Post by cor2y on 2007-12-25
yes i too seem to have run into a block on dvds using the default ubuntu media player (totem-gstreamer) however using totem-xine works for it ,however i don't like xine because it renders some asf (wmv) files with video artifacts,  if the xine library doesn't work theres mplayer and the videolan player both can play dvds, with what you already have installed libdvdcss2 etc.

---

### Post by scamper_22 on 2007-12-25
I've tried both mplayer as well as VLC.  

with mplayer, i get this error: Failed to open DVD://1
a similar error occurs with vlc.

I don't think it's the dvd drive, as if i put in a dvd with avis on it, I can play it fine.

Anything with permissions...?

---

### Post by cor2y on 2007-12-25
how many dvd drives do you have?
And if more than one which drive did you use when installing Ubuntu from the cd/dvd.
Heres a tip to see if its permissions etc
Insert the dvd in the drive and via the terminal type this
```

mplayer dvd://
```Note there is no number 1 and dvd is not in caps
if you still get an error then i don't know if it plays then you were telling mplayer to look somewhere where there was no disc to be played.
for vlc its the same simply replace mplayer with vlc
```

vlc dvd://
```

---

### Post by scamper_22 on 2007-12-26
Hi,

I only have 1 dvd drive.

This is the output from VLC
---------------------
vlc dvd://
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/hdc with libdvdcss.
libdvdread: Can't open /dev/hdc for reading
libdvdnav: vm: faild to open/read the DVD
[00000298] dvdread demuxer error: DVDRead cannot open source: /dev/hdc
[00000296] main input error: no suitable access module for `dvd://'
[00000287] main playlist: nothing to play
-----------------------------------

---

### Post by cor2y on 2007-12-26
Every needed file seems to be in place
try to change the permission

```

sudo chmod 666 /dev/hdc
```
And see what happens when you try to play again.

---

### Post by scamper_22 on 2007-12-26
same thing.

I tried 3 retail dvds...same result.

i thought it might be the region code?
regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.


i don't know.  looks like its having trouble reading the dvds, when its a video dvd.  if i insert a data dvd, it works fine.  so i don't think its permissions or anything like that.   Could it have something to do with dvd encryption?

---

### Post by scamper_22 on 2007-12-26
okay, not sure if this is a clue or not.

If I insert a data DVD, the DVD is recognized and the icon pops up on the desktop.  I can also see the dvd in Places.

When I put in a retain movie dvd, it just tries to load, but the icon never pops up and it does not show up in places...I can't open the dvd and see the folder (Video_TS...)

Even if the codecs are not installed correctly, I shold still be able to see the basic dvd folder info right?  Or would this be a problem with encryption?

Thanks,

Y

---

### Post by scamper_22 on 2007-12-27
Okay, after much investigation, I think this is more a mounting problem.

For some reason, I cannot mount retail video DVDs.
data DVDs work
CDs work

Any ideas?
I've tried changed my /etc/fstab from udf,iso9660 to auto, but that has not solved the problem.

---

### Post by LowSky on 2007-12-27
This should get all your codec fixed

Below are the instructions to add the Medibuntu repository to your system's list of APT repositories for Gusty if you need Fiesty look here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

Then, add the GPG Key
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

then reinstall lidvdcss2
```
sudo apt-get install libdvdcss2

```

then install w64codecs
```
sudo apt-get install w64codecs

```

Then restart the machine

---

### Post by scamper_22 on 2007-12-27
hi LowSky,

I've already added the repro and the codecs.
I've also checked my region code (set to 1)

no such luck.

Not sure if you would know...but I'm trying to isolate the problem.
Could anyone try and clarify the following:

If the codecs are not installed correctly, would I still be able to mount a retail video dvd?  I ask this so I know which path to follow.  It's possible, due to my trying to get this to work, I installed the codecs in the wrong order or whatever so perhaps an uninstall/reinstall would be in order... Anyone ever hear of the order mattering?

I've read in some forums that ubuntu is 'less tolerant' of faulty DVD drives.  I don't know about that, but is there any truth to this.  The drive worked fine in windows xp (only about a month back).  Could the drive by physically broken?  It's possible there are different lasers, but I find it weird how it reads data DVDs perfectly fine.  I've tried 3 different retail dvds...all the same result.  This is why i suspect the drive is not the problem.


One forum post I read said their problem was from the dvd drive not being unmounted correctly.  Does anyone know how I would check to see if this is a problem.  I've tried rebooting the laptop, putting in a data dvd and rebooting... no result.  I'm going to try a cold boot (always good to try...surprised I didn't do it before).  Any comments on this possibility.

---

### Post by scamper_22 on 2007-12-28
alright, well i seem to have gotten it working...most of time :)
It's a bit flaky, but once it mounts the drive, it plays flawlessly.
I upgraded the firmeware on my drive.

It is a NEC 5100A which was loaded with v 1.22 firmware
I upgraded to 5500 1.51 firmware.

---

### Post by vgrisham on 2007-12-31
> **scamper_22 said:**
> HI all,

I just can't get DVD playback working on 64bit 7.10.

I have searched all over, and tried many things.

installing/reinstalling
gxine
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

Nothing seems to work.  At one point I did get the DVD to play, but then it would just quit after it got to to the title menu.  I haven't been able to get it to that state again.

If I use gxine and try to open a dvd, I just get 
The xine engine failed to start.
No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

Anyone think of anything I can do?
Or what diagnostic commands I can run?

Thanks

Scamper_22, I'm running Gutsy 64-bit as well, and as near as I can tell, the only difference between what you've tried and what is working on my system is that you're using gxine. You might want to try removing gxine, and installing libxine1. Make sure libdvdcss is installed. Then, try installing Ogle. It's the only player I've seen for Linux that supports DVD menu navigation, and it's been really stable for me. 

Just a heads up. I had a similar problem last summer and it wound up being my DVD drive. It worked fine for data, wouldn't rip or encode audio cds or play DVDs. Thinking it was an Ubuntu issue, I wrestled with it for quite a while. I then bought a new drive, et voila, it worked.

---

### Post by zsobin on 2008-02-08
i've used this on a wide variety of hardware, seems to always work.

First install the gstreamer plugin when it prompts you when you first try to play a dvd.

Use these 3 lines... it will inform you that it is experimental to compile for the amd64, hit enter to continue.

sudo apt-get install libdvdread3 totem-xine libxine1-ffmpeg
sudo apt-get install debhelper fakeroot
sudo apt-get install build-essential
sudo /usr/share/doc/libdvdread3/install-css.sh

If you've messed around with css, libdvdread before doing this it probably won't work.  This needs to be done from a clean install.  I havne't found a good way to make it clean like a new install.

---

### Post by Kivech on 2008-03-03
> **zsobin said:**
> i've used this on a wide variety of hardware, seems to always work.

First install the gstreamer plugin when it prompts you when you first try to play a dvd.

Use these 3 lines... it will inform you that it is experimental to compile for the amd64, hit enter to continue.

sudo apt-get install libdvdread3 totem-xine libxine1-ffmpeg
sudo apt-get install debhelper fakeroot
sudo apt-get install build-essential
sudo /usr/share/doc/libdvdread3/install-css.sh

If you've messed around with css, libdvdread before doing this it probably won't work.  This needs to be done from a clean install.  I havne't found a good way to make it clean like a new install.

You sir, are now my official hero! Finally I can watch DVDs in Totem. Thanks!

Kivech

---

### Post by SGAZ on 2008-03-16
zsobin, That is extremely helpful!  I was in the exact same situation as Kivech and your solution fixed me right up!   

I was having this problem on a brand new install:

Gutsy7.10
Phenom 9600
HD3850 vid card
SATA2 DVD Player

Thanks,
SGAZ

---

### Post by cypherpunks on 2008-06-18
I had the exact same problem as you guys. With dvd and amd64. I did everythin you suggested and it did not do it (was not enough)

Then I unmounted the DVD and started totem. It worked. Ubuntu automounts DVDs but totem/vcl etc. need to read it from device. 

SOLUTION: install all the stuff previous messages explain how. Then unmount drive and start your player.

---

