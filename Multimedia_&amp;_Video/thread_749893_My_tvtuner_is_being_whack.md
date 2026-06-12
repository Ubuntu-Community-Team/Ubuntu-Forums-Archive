---
title: "My tvtuner is being whack"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by Jiffyman on 2008-04-08
I just put an old TV tuner card in my computer a couple days ago and got it working by adding a line to modprobe.conf. The card starts up in Mythtv, but not TVtime since I can't get it to work for some reason. When I run Mythtv to watch it I get a screen thats split horizontally with the video mirrored. When I exit MytheTV the audio never quits, it just keeps going no matter what until reboot. The card is a Leadtek Winfast TV 2000/XP rm.  I would really like to get this card working properly since I  just installed  LinuxMCE  :-) Also this isn't really a biggie ,but the card comes with a remote. How may I go about getting that to work. 

card=34
tuner=43

Edit: This might be related to the sound issue. I had to use the CD-IN on my board cause I don't have an Auxiliary

---

### Post by wolfen69 on 2008-04-10
i believe it's because tv tuners use different drivers tied to the tv application. there are 2 offhand- ivtv and v4l. im not an expert, i just know how to get hauppauge pvr's working in vlc.

---

### Post by Jiffyman on 2008-04-11
> **wolfen69 said:**
> i believe it's because tv tuners use different drivers tied to the tv application. there are 2 offhand- ivtv and v4l. im not an expert, i just know how to get hauppauge pvr's working in vlc.

Alright is there a way I can force mythtv to use another driver. Also I'm having problems with TVtime loading. When I click the icon the window pops up really quick and disappears. When I execute tvtime in the terminal I get this 

```
geoff@dcerouter:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/geoff/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/geoff/.tvtime/tvtime.xml: Permission denied.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
```

---

### Post by wolfen69 on 2008-04-11
```
gksudo tvtime
```will open it.

---

