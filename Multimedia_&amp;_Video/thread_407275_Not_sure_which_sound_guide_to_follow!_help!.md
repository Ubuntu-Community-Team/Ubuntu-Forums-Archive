---
title: "Not sure which sound guide to follow! help!"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by linuxgajin on 2007-04-11
what I do know:

aplay -l reveals:

```
light@Deathnote:/$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have a laptop and I'm trying to get the sound to work. The sound isn't muted; I checked that. I've seen seceral guides but I really don't know what which to follow. What should I do?

---

### Post by renzokuken on 2007-04-12
best bet is to try and install/update to the latest alsa-driver. it has much better support for newer ALC soundchips than the default alsa-driver 0.1.0.12 that comes with ubuntu.

its a fairly painless procedure.

go to [www.alsa-project.org](www.alsa-project.org) and get the latest stable release of alsa-driver (0.1.0.13 i think)

then do the following in a terminal

```

sudo apt-get install build-essential
cd /folder/where/you/saved/alsa-driver
tar xjf alsa*
cd alsa*
./configure
make
sudo make install

```

then reboot and see how it goes.

i had the same issue as you, appeared to play files but nothing came out of speakers so i updated to alsa-driver 0.1.0.14rc2 and immediately fixed my sound. you may want to use .13 though as that is stable while 0.14 isnt yet

---

### Post by linuxgajin on 2007-04-12
Hmm i get an error here:

```
light@Deathnote:~/sound/alsa-driver-1.0.13$ tar xjf alsa*
tar: alsa-kernel: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Am I in the wrong directory? I'm still new at this. Thanks alot for your help though; if my experience ends up like yours it should work - but i don't know how to troubleshoot this error. Any suggestions?

---

### Post by aqualad on 2007-04-12
Hehe, he just got lazy, just do

```
tar xjf alsa-driver-1.0.13.tar.bz2
```

Where he put the '*' you should have hit tab to complete the file name

Follow the rest of his instructions

---

### Post by linuxgajin on 2007-04-12
Ok thank you :) as you can see i'm still new at this haha ok let's give this a try...

---

### Post by linuxgajin on 2007-04-12
Ok I'm not sure what happened but now it doesn't recognize my sound device!

aplay -l

```
light@Deathnote:~$ aplay -l
aplay: device_list:222: no soundcards found...

```


Now it realllly doesn't work... what do I do? @@

---

### Post by renzokuken on 2007-04-12
did you reboot?

---

### Post by linuxgajin on 2007-04-12
yup, i rebooted right after

---

