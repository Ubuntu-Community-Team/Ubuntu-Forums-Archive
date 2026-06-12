---
title: "Multimedia Headaches"
date: 2009-02-09
forum: Multimedia Software
---

### Post by jondska on 2009-02-09
OK. I've spent the last 3 days working on this system and I haven't gained any ground. My wife thinks I'm purposely avoiding her but I'm obsessed with making this work. Ubuntu 8.10 installed perfectly and works great except for dvd player and soundcard. I've been through every google search and forum post and have tried everything I could find but still no sound and no dvd. One thing at a time. Dvd first. Went through the multimedia sticky and installed all that was recommended. Did the medibuntu thing. Totem gives me this: Internal data flow error. Mplayer tells me :no stream found to handle url dvd://1. I did set the cdrom to 1 in preferences and still the same result. Not sure where to go from here and I have to work again tomorrow.

---

### Post by redroad55 on 2009-02-09
so when you say sticky you mean this one I assume :[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

If so you did this step: 
> --PART 4/5, DVD PLAYBACK/RIPPING/BURNING--


DVD PLAYBACK


Note: I recommend disabling the CD/DVD-ROM source before completing this section, as you will receive numerous prompts if you need to run the "install-css.sh" command. If you're not sure whether it's disabled or not, take a look at the preparation instructions in Part 1.

For the best DVD playback in Ubuntu, including menu support, install the following packages:

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc

You can also use the Xine engine in Ubuntu (default engine in Kubuntu and Xubuntu) for video/DVD playback. This can be done without having to change the back-end of Totem - just install an alternative GNOME front-end for Xine called Gxine (this is optional, VLC will do just fine):

sudo apt-get install gxine libxine1-ffmpeg

Now you can test a DVD with VLC, Kaffeine, Gxine or whatever your favourite media player is. Enable deinterlacing ("VLC > Video > Deinterlacing > Blend") if playback is choppy or if you notice artifacts.

Note: Those of you still having DVD playback issues after installing the above packages should try the solutions in the troubleshooting section, which you can find at the end of this howto.


 Post back

---

### Post by mc4man on 2009-02-09
Here's a few things you can try
With a dvd in the drive run this to ck. /dev/links and more importantly see if the dvd is mounted properly

```
sudo lshw -C disk
```

This is some of what you want to see in the *-cdrom: listing at the bottom
> ..........clipped
configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
clipped..........

Then read here about checking if a region has been set on the drive

[http://ubuntuforums.org/showthread.php?p=5451540#post5451540](http://ubuntuforums.org/showthread.php?p=5451540#post5451540)

and here is a basic set up dvd playback, skip medibuntu stuff if done already 

[http://ubuntuforums.org/showthread.php?p=6223490#post6223490](http://ubuntuforums.org/showthread.php?p=6223490#post6223490)

---

### Post by jondska on 2009-02-10
You got me on that one. Didn't install vlc and it plays fine on that. Still doesn't play on the others. My goal is to eventually install myth so if this will get me there, then OK. 

Since that was so easy for you guys, the sound card is a Montego DDL and the turtlebeach website says it should work with ubuntu out of the box. I've made sure that it is not muted and in volume control preferences, I changed it from intel 8201db-ich4 (alsa mixer) to cmedia cm18768 (alsa mixer). When I did that, I got light output out of the optical cable but still no sound. Any ideas.

Past my bedtime, will check back tomorrow after work.

---

### Post by mc4man on 2009-02-10
Don't know about that sound card, as far as your other players for dvd they'll all probably default to /dev/dvd.
Check the output of the lshw and adjust in the players settings if needed.
The other possibility is your other players may be failing due to wrong audio output.
If you have the r*epo mplayer* starting it from the terminal can prove informative
```
gmplayer
```

---

### Post by markbuntu on 2009-02-10
I have a c-media 8768 though it is not a turtle beach card and it works great. You probably just need some sound server troubleshooting and configuration help which you can find here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Before you go there (things can get rather long and involved there, it is very extensive) you should try this first

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by jondska on 2009-02-10
mc4man, here's what gmplayer gives me, do I need to reinstall?:
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

markbuntu, I have started working through that troubleshooter. I will let you know if it works. thanks.

---

### Post by mc4man on 2009-02-11
Get your sound squared away first and then post your sudo lshw -C disk, there should be no reason to re install mplayer.
If you post your lshw, after pasting in then highlight the text and then click on the little 'quote' box in the reply panel, better for reading

---

### Post by jondska on 2009-02-15
Have to try to find time to work on this. Just discovered that the sound is coming out of the card installed on the mobo. How do I switch to the cmedia sound card. 
> **** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by markbuntu on 2009-02-15
You do that n the pulseaudio volume control, as explained in the links i posted before.

---

### Post by jondska on 2009-02-15
Going around in circles with this. Now it says connection failed when I start the pulseaudio volume control.

---

### Post by markbuntu on 2009-02-16
That means the pulseaudio daemon is not running. You can start it with

pulseaudio -D

---

### Post by jondska on 2009-02-27
[HTML] pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.[/HTML]

---

### Post by markbuntu on 2009-02-27
Could you please start pulseaudio from a terminal with

pulseaudio -vvv

and post the results.

---

