---
title: "Hauppauge WinTV PVR-250, completely baffled by this in Feisty!"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by mocha on 2007-06-16
For the life of me, is it possible to use some simple application such as kaffeine with the PVR-250?  All of the different howto's for MythTV and IVTV drivers are giving me a nervous breakdown just reading them.  This has got to be the most convoluted thing I've ever come across in Linux.

I don't care about MythTV.  I just want a simple application that can use the PVR-250's onboard MPEG2 encoder to recorder TV programs.

---

### Post by newlinux on 2007-06-16
You can watch the PVR-250 with mplayer and vlc. You coud use the "at" command  with cat /dev/video0 > filename. and ivtv-tune to schedule a recording commandline.


[http://ubuntuforums.org/showthread.php?t=431793](http://ubuntuforums.org/showthread.php?t=431793)

VLC:

Open VLC > File> Capture Device> PVR then select you video device. Or you can do it with vlc commandline.


mplayer:

```
mplayer /dev/video0
```

Change channels:

```
 ivtv-tune -c # -d /dev/video0
```
replace # with the channel you want to watch.


In Feisty the PVR-250 works right out of the box as ivtv drivers are already installed so setting up Myth in theory wouldn't be very difficult. If you already have a feisty desktop setup use this tutorial:

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O)

---

### Post by mocha on 2007-06-16
Hello.  Well I followed that link and got it working now.  I don't know why I couldn't do this yesterday.

Is there any other program that will work with the PVR-250's hardware MPEG2 encoder?  MythTV is kind of bulky for what I wanted to do.  I've tried xawtv and can't get it to show any video.

---

### Post by newlinux on 2007-06-16
Yeah, mplayer and VLC as mentioned in my earlier post. Did those not work for you?

---

### Post by jaw1959 on 2007-06-16
I have a PRV-250 that I bought in 2002.  Will that work with the current drivers?  Will I have to update the firmware?  What's the quickest way to check if it's working before I install mythTV?

---

### Post by superm1 on 2007-06-16
> **jaw1959 said:**
> I have a PRV-250 that I bought in 2002.  Will that work with the current drivers?  Will I have to update the firmware?  What's the quickest way to check if it's working before I install mythTV?
The firmware and drivers are included with feisty.  Pop the card in, and boot up.  If you want to do a test capture,

```
cat /dev/video0 > /tmp/test.mpg
```You can play it as described above.


---

### Post by mocha on 2007-06-17
> **newlinux said:**
> Yeah, mplayer and VLC as mentioned in my earlier post. Did those not work for you?

Okay.  You are not the only person telling me this.  So.... How do you get VLC (for example) to use the hardware MPEG2 encoder on the PVR-250?

---

### Post by superm1 on 2007-06-17
> **mocha said:**
> Okay.  You are not the only person telling me this.  So.... How do you get VLC (for example) to use the hardware MPEG2 encoder on the PVR-250?
See attached screenshot.  Basically open up from this tab on VLC.

---

### Post by mocha on 2007-06-17
What about changing channels?  Can it be done on the fly or do I have to enter the channel every time?

---

### Post by newlinux on 2007-06-17
use the ivtv-tune command at the terminal prompt that I specified earlier to change channels.

---

