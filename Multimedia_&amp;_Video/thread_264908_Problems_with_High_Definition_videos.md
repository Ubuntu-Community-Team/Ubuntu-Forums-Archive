---
title: "Problems with High Definition videos"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by haran_elessar on 2006-09-25
HI,

 I've been having problems playing High Def movies (be them quicktime or wmv) since I installed ubuntu. I downloaded the codecs from automatix and easyubunu (my brother did the same thing with his laptop and  he didn't have problems) and I still can't play the files.
 What happens is that when I open a high def file, Totem starts and just when it is about to play it closes automatically. I've been searching the forums for a similar problem but so far I've been unable to find one. Can someone please help me with this problem?? It's the only gripe I've had with Ubuntu, so far, I love the OS and have stopped using windows completely...but I want to watch HD videos on Ubuntu too!!!:-|

---

### Post by pseudonym on 2006-09-25
You might want to try mplayer instead of totem. It usually plays anything that other players have trouble with. For example, I usually use xine for video, but it had sound problems with some HD .wmvs. But mplayer played them back perfectly.

---

### Post by Malta paul on 2006-09-25
I use VLC Media Player with a 17 inch TFT/LCD monitor, works great for me,
Go to Applications>add/remove>sound and video, just look for VLC then tick the box,press apply and away you go.
Good luck, paul

---

### Post by haran_elessar on 2006-09-25
Hey thanks for the help...unfortunately neither mplayer nor vlc will work with the HD videos. Mplayer does exactly the same thing as totem (it closes just when it is about to play) and vlc plays the file but won't show any video...it also shows me a black screen with audio with all other videos...I checked the codecs I have installed in the add/remove section and I have them all. What the heck could it be?

 Again thanks for the help it is greatly appreciated!!

---

### Post by pseudonym on 2006-09-25
Try running mplayer from the command line if you haven't already. Also check that your video set up is correct ie. you are running the accelerated driver rather than the default one. Verify this by opening up /etc/X11/xorg.conf and making sure that 'nvidia' or 'fglrx' (or whichever driver is appropriate if you have neither a nvidia or ATI card) is listed in the 'Device' section. If it says 'vesa' or 'nv' or 'ati' you should check the forum howtos for installing graphics drivers if you're unsure how to do it.

Also, do you have playback problems with other formats as well?

---

### Post by psyke83 on 2006-09-27
> **haran_elessar said:**
> I've been having problems playing High Def movies ...Hey,

The problem is that your XV allocation is too low, either due to configuration or hardware restraints. Are you using Intel integrated graphics? Edit /etc/X11/xorg.conf and in the "Device" section, add:

```
Option "LinearAlloc" "6144"
```

See "man i810" to see if that option exists, otherwise you may need to upgrade your i810 driver (using a custom package from e.g. the (old) compiz.net repository, or upgrading to Edgy).

Try: ```
mplayer somevideo.wmv -vo x11
``` and see if it helps. If the video plays, but doesn't with "-vo xv", then you need to upgrade your driver. 

Follow the guide here: [http://www.ubuntuforums.org/showthread.php?t=253856]("http://www.ubuntuforums.org/showthread.php?t=253856")

OR, if you don't want compiz on your system just do this to upgrade xserver-xorg-driver-i810 (but you may need Xorg-air too, so consider installing from the instructions above instead):

Add to /etc/apt/sources.list: ```
deb http://www.beerorkid.com/compiz dapper aiglx
deb-src http://www.beerorkid.com/compiz dapper aiglx
```
Then:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Then restart X or reboot when the driver is upgraded, and try playing a movie with totem or mplayer -vo xv.

---

### Post by haran_elessar on 2006-09-28
Hey psike83 I do have an intel integrated graphics chip (915GM), and I also have compiz installed (it was very troublesome but after 4 re-installations](*,)  I got it running :) ...thanks mainly to this community :) ).
 After having ruined my X so many times by making modifications to it...I'm kinda scare to mess with that file so I treat it with a lot of respect lol.
I checked what you told me to and I noticed that the option  "LinearAlloc" "6144" is missing. I also saw that the drivers are i810 but it doesn't say "man i810".
  So I just want to make sure what I have to do... I know you already told me what to do but I want to make sure that nothing changes with the info I just gave you (having compiz installed),just in case because I don't want to mess this up again since it's running so great right now :)...thanks for the help!!

---

### Post by psyke83 on 2006-09-28
Hi,

Xorg's driver naming scheme can be a little confusing, but you should be using the i810 driver, yes. About compiz, what guide did you use? The reason why I ask is that you need newer drivers than what comes with Dapper, version 1.5.x or 1.6.x is what you need. You can check with (copy this into a terminal exactly):

```
dpkg -l | grep i810
```

Mine is ```
ii  xserver-xorg-video-i810                   1.6.5-0ubuntu3                       X.Org X server -- Intel i8xx, i9xx display d
``` which means that I have version 1.6.5. If you have lower than 1.5.x, then you need to follow the guide above so that you have an upgraded driver, and then add the LinearAlloc line to your config.

---

### Post by haran_elessar on 2006-09-28
OK I checked the drivers and I have the same as you 1.6.5...I proceeded to add the option allocation to the device section...then I entered the code for playing a video via the terminal and I got the following message:

CPU: Intel Pentium M Dothan (Family: 6, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing lair_tgs06_hd.wmv.
File not found: 'lair_tgs06_hd.wmv'
Failed to open lair_tgs06_hd.wmv


Exiting... (End of file)


:confused: :confused:  ... what does that mean? I'll try to do some more research but any more help will be greatly appreciated since my "research" time is seriously cut due to classes and I only use my laptop at college since they have wireless here...I have dial up at home and a stupid winmodem :( 

thanks for the help!!

---

### Post by psyke83 on 2006-09-28
The file wasn't found ;). You're probably in the wrong directory. Just click on the icon to open it in totem as it should work properly in that from now on (I asked for you to try mplayer as a troubleshooting measure, by default it uses Xv just like totem).

---

### Post by haran_elessar on 2006-09-29
YEAAHHHHH!!!! WOHOOOOOOO!! IT WORKS!!! I just played an HD video and it ran great...I also exclaimed "yeaahh" very loud and evryone here is sleeping right now so I hope I didn't wake anyone up :) .

 I actually forgot to say in the preivous reply that I actually tried playing a video (by clicking directly on tne file) after adding the allocation option and it didn't play...after that I tried from the terminal and I got that message. I turned off the laptop and now I turned it up and the video ran just fine...seems it needed to reboot.

 Well I give you all a big thank you for helping me out. The community aspect of linux is one of the main reasons I like the OS so much...everytime I tell someone else about it I talk a lot about the ideology behind it. It's something that, sadly, we don't see in many other places. Everywhere else everyone is so focused in competing with one another that they forget to help each one out...but anyway thanks a lot for the help...I hope that  by using the OS more I'll be able to learn more about how it works and that way I can help someone in the future just like you guys (or gals) did. Thanks!

---

