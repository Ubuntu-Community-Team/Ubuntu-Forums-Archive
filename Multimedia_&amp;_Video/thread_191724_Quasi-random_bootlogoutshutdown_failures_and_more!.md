---
title: "Quasi-random boot/logout/shutdown failures and more!"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by aniceyoungman on 2006-06-07
(*note, I haven't much idea what I'm doing, but am I willing to learn and/or be yelled at for not knowing enough preliminary basics*)

Hey all,


Problem 1:

I have a somewhat fresh dapper install (dual-booting w/XP, but trying to convert permanently).  Install went well enough on my homemade box.  But...I am having random boot failures.  What seems to happen is that the boot screen gets to when the progress bar is almost full and then...my lcd goes into sleep mode and nothing else happens.  I have to hit the hardware reset switch and the system may or may not do it again.  Sometimes it will boot several times without issue, others it will require several attempts for it to finally make it.

Also, when logging off (shutting down too), it will sometimes just go into the sleep-mode of despair, never to respond again until the whole reset-it-and-forget-it routine.  I noticed as well some weird coloring on buttons occasionally too...only goes normal upon mouse-over...

Is it a video card issue?  I'm running an ATI AIW 8500DV with whatever default drivers (I think).

Problem 2:

Asside from the whole boot-up crap-shoot issue, once I get 'er running everything is mostly awesome.  I got all the media-codecs to work, but I am having trouble with dvd's.  Half the time, I will put in a DVD and totem will automatically start up (as expected, I believe?) and play the video with no issues.  Say I get done with the first movie and I go insert another.  It seems to mount fine (the whole desktop shortcut appears), but totem will not play (even if I point it at the file).  This seems to happen only with subsequent movies (not the first).  A reboot (which on my system can take awhile - see Problem 1) will solve the problem (the movie will again play fine).  Is this a known issue?  Anyway to restart totem?  Is it a mounting issue?  Where should I begin?

Any help would be greatly appreciated fellas.  Thanks in advance,

J.

---

### Post by an.echte.trilingue on 2006-06-08
You are having hard crashes more than likely related to your video card.

Maybe this will work (at least, it can't hurt):

First, be sure you know your screen resolution and refresh rate.  In a terminal:
```
sudo aptitude install linux-modules-restricted-386 (or whatever your kernel is)
sudo aptitude install xorg-driver-fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
```
Select the options that fit for you in dpkg (including the fglrx driver), then restart X with CTRL+ALT+BACKSPACE.

If this leaves you with a lock or black screen, reset and boot into the recovery console and then type this:
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo init 6
```

Repeat until you find the settings that are right for your setup.  If all else fails, go ahead and post the contents of your original xorg.conf file and we will try to work from there.

Let us know how it goes and good luck!

---

### Post by an.echte.trilingue on 2006-06-08
I had some similar issues to this.  Are you using totem-xine or totem-gstreamer?

---

### Post by aniceyoungman on 2006-06-08
Thanks for the responses guys,

I'm currently at work and thus cannot try the video card troubleshooting right away, but I'll give it a try later.  

I actually think I fixed the issue with totem (it is totem-xine).  What I noticed was that *sometimes* when I inserted a back-up dvd (dvd-r or +r), I would try to locate the video-ts/audio-ts folders in the cdrom folder and nothing would be there.  They would show up in the "cd/dvd recorder" folder.  I surmised that the default program for cd burning (which is set to start-up upon insertion of a "blank" disc I believe) was "hijacking" the files post mount, and interfering with totem's autoplay.  Thus, I removed the autoplay of the cd/dvd recording when "blank" discs are inserted, and lo-and-behold, totem now autoplays every disc every time with NO issues.  I don't know if this is an issue with the way the default burning software detects if a disc is blank or not, or what, but this fix seems to have solved the issue.  I tried like 6 different discs in a row, and totem-xine played each one right away with no detection issues.  

I'll try the video troubleshooting and get back to you all.  Thanks for the input!

J.

---

