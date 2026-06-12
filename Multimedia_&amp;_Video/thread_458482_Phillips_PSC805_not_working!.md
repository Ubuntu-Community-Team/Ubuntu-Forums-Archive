---
title: "Phillips PSC805 not working!"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by general.chaos on 2007-05-29
ok, my on board sound didn't completely work with Linux, so I decided to go and get a USB sound card as people here told me it would work fine.   I get home, connect it, boot windows, etc, etc, and it works.  Reboot to linux, no dice.

It doesn't even light up!  I tried to make it the default sound device in System > Preferences > Sounds but it's not one of my choices.   It is, however, the only choice under Device.

So anyway, when I go to sound playback, regardless of what I pick when hit test I get this error. (unless I pick autodetect, then it just closes itself out)

auidotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open resource for writing

Anyone know what I can do to make this work?  The only reason I even had to buy this card was to get 5.1 support in Linux and move away from windows.  Figures....

---

### Post by general.chaos on 2007-05-29
ok, disregard my first post.  Apparently you can't have it plugged into a USB hub, has to be strait into the PC.

Still doesn't do 5.1 tho... Still better than it was tho

---

### Post by general.chaos on 2007-05-30
well, I have discovered that it wasn't the USB hub at all.  It seems in order to make it work each time I reboot I have to unplug it and then plug it back in.

Still only getting 3 channels + the sub instead of all 5...

Any ideas on how I can make it "just work"?

---

### Post by general.chaos on 2007-05-30
Bump.  Please help if you can.

---

### Post by staticsage on 2007-07-09
Mine works when plugged in through the USB hub. Sometimes I have to replug it back in, but I think that's a problem related to a bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746)

As for 5.1.... it only puts out 5.1 if the source is 5.1. If you open a movie it works for me on both 5.1 and AC3 passthrough (I have deconding on my speakers as well). Give it a test run with a video, and make sure you set the player to use 5.1

---

### Post by loboc on 2007-11-05
See this Thread about getting (digitial) spdif and surround working as outputs.
 
[http://ubuntuforums.org/showthread.php?p=371358](http://ubuntuforums.org/showthread.php?p=371358)

Theres more to alsa that may get upchannel mixing and surround working for everything but I am not an alsa guru and dont know all the syntax of the .asoundrc file.

---

