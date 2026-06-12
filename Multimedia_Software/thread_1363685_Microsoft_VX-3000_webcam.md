---
title: "Microsoft VX-3000 webcam"
date: 2009-12-24
forum: Multimedia Software
---

### Post by smithg86 on 2009-12-24
I am using Ubuntu 9.10. I have a microsoft vx-3000 usb webcam. All I get is static from it. Can anyone help me?

---

### Post by zerwas on 2009-12-26
Hi,

please follow 
[this]("http://swiss.ubuntuforums.org/showpost.php?p=8238570&postcount=4") posting.

Good luck,
zerwas

---

### Post by smithg86 on 2009-12-26
> **zerwas said:**
> Hi,

please follow 
[http://swiss.ubuntuforums.org/showpost.php?p=8238570&postcount=4]("this") posting.

Good luck,
zerwas
zerwas,

I can't really follow that post. I'm sorry, but I'm a complete noob when it comes to linux. Can you explain exactly what I'm supposed to do? Thanks :)

---

### Post by zerwas on 2009-12-28
Okay,

first we need to open a [terminal]("https://help.ubuntu.com/community/UsingTheTerminal"). To do this, go to Applications menu -> Accessories -> Terminal.

Now you enter these commands *(one by one)*:
```
cd /tmp
wget http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2
tar xvfj tip.tar.bz2
cd v4l*
make
```
Wait, until it is finished (it will finish with an error).
Now, execute this command to open a file with a text editor:
```
gksudo gedit /tmp/v4l*/v4l/.config
```
Search for the line 
> CONFIG_DVB_FIREDTV=m
and change it to
> CONFIG_DVB_FIREDTV=**n**
Now click on "Save", close the text editor and get back to the terminal where you enter:
```
make
sudo make install
```

Now reboot your computer and your webcam should work.

---

### Post by smithg86 on 2009-12-28
it works!!! thanks so much!

---

### Post by tachyian on 2010-05-13
Now I'm running Ubuntu 10.04 LTS and VX-3000 works out of box, but only for video. The mic still doesn't seem to work properly. Does the mic also work by following this method? I just want to know before I screw up my now-working video. Thanks in advance!!

---

### Post by xc3RnbFO8P on 2010-05-13
> **tachyian said:**
> Now I'm running Ubuntu 10.04 LTS and VX-3000 works out of box, but only for video. The mic still doesn't seem to work properly. Does the mic also work by following this method? I just want to know before I screw up my now-working video. Thanks in advance!!

Did you check in **Sound Preferences> Input**, if webcam mic is there?

---

### Post by tachyian on 2010-05-13
Wow! I didn't expect such a quick reply! Thanks!
I'm using pulseaudio, and checked the sound preference, pulse audio device configuration by padevchooser, and the default input device setting. I DO see the device (i.e., the mic of VX-3000) in all of the above. Also, I checked the volume settings and pumped it up to the maximum.  The problem is that I can't hear anything. All I can hear is a VERY week high pitch noise, and the mic volume level barely response to any sound that I make. It seems that the mic is recognized properly by the system, but somehow it doesn't gather sound. Any idea?

---

### Post by xc3RnbFO8P on 2010-05-13
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")
>  Microsoft Lifecam VX-3000 7.10 045e:00f5 gspca
The built-in microphone doesn't work, although it is seen by ALSA.
Install **Gnome-alsamixer** , try to activate capture, input or mic, and move sliders right and left.

---

### Post by tachyian on 2010-05-13
Thank you again for the quick reply!
I followed your suggestion, but it still hardly captures any sound. The only way that I can make it capture any sound is tapping it with my nail, and even doing so, the noise is louder than the tapping sound. Is there any workaround for this type of audio problem? Can it be remedied only by a new driver?

---

### Post by Skipopis on 2010-05-14
I am also running 9.10 with the same webcam and did all the steps above to no avail. please help.

---

### Post by sizkim on 2010-08-22
I have the same VX-3000 webcam while running Ubuntu 10.04. I Do have "LifeCam VX-3000 Analog Mono" item on the input device list, however, it doesn't have any input pulse when I select it. Not working for Skype testing call and the newly issued GTalk plugin.

I'v also tried Gnome-alsamixer, nothing get better.

Extension mic works fine when I plug in to the socket on my computer.

Just wish 10.10 could get any improved.

---

### Post by camiscrazy on 2011-09-01
zerwas:

hello.. okay so i followed all commands through the terminal then my computer restarted itself.. even when i tried to go back and enter in the CONFIG command there was no note to edit...? 

what should I do?

---

