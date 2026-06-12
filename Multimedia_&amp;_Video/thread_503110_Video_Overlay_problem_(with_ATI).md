---
title: "Video Overlay problem (with ATI)"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by plux0r on 2007-07-17
Hello! 
I'm in need of some help here, I've tried searching the forum and google but I couldn't find any solution to my problem.

I recenently upgraded to Feisty (did a clean install actually) and also thought I would upgrade to the latest ATI drivers (fglrx 8.38.6) for my ATI Radeon X1950 Pro. Before the upgrade my video playback was ok. 

My problem is that since the upgrade Ubuntu won't playback my video properly. All video looks lowres and the playback is kind of choppy. I'm guess think is a problem with the hardware video overlay, it doesn't seem to be applying any filters to the video playback. I've tried using different players, but the result is always the same.

I think my drivers are installed correctly, because I tested the 3d hardware acceleration in Warsow.

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6474 (8.38.6)

$ Xorg -version
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
Module Loader present

I used atconfig to generate my xorg.conf, which looks like this:

[http://www.update.uu.se/~plux/files/xorg.conf](http://www.update.uu.se/~plux/files/xorg.conf)

If you have any idea of a solution to my problem, please don't be afraid of posting here! :)

I hope I will be able to get some help with this here at the forum, thanks!

---

### Post by leo_rockway on 2007-07-19
my video card is an ati x1400 mobility. i have the exact same problem.
i was doing fine w/ the old drivers, all videos were playing great but when i tried glest it asked me to upgrade my drivers, so I got the latest drivers from ati.com

now all the videos play choppy.
[edit]
only if i use vlc player. all the other players work fine, i just figured that.
[/edit]

if someone out there has any clue on how to fix this (rather than downgrading the video drivers, which i'll do if it comes down to that) plux0r and i will be really greateful!

---

### Post by GooglieS on 2007-07-20
I have the same problem...

---

### Post by leo_rockway on 2007-07-20
apparently there's no solution to our problem:

[http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26984](http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26984)

[edit] nevermind, it's only for the x1800 models. my bad. [/edit]

---

### Post by GooglieS on 2007-07-21
Wonderful.... How to roll-back to stable drivers?

---

### Post by GooglieS on 2007-07-21
plux0r   - did you solve your problem?

---

### Post by plux0r on 2007-07-22
> **GooglieS said:**
> plux0r   - did you solve your problem?

Nope :(

I haven't had time to try reverting my drivers to an older version yet, I guess that might solve the problem.
I can't think of any other solution. :(

Did you try it?

I'll post here if/when I've solved it.

---

### Post by GooglieS on 2007-07-22
I try it, but it does not help.
googlies@guggiland:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)


I forget which version was default in ubuntu :)

---

### Post by plux0r on 2007-07-22
Ouch.. so it won't solve the problem then :/

I hope someone has found a good solution for this :(

---

### Post by GooglieS on 2007-07-22
Try to install an older driver. Maybe you can do that :)

---

### Post by leo_rockway on 2007-07-22
when i tried to install an older driver i was sent back to the mesa ones...

---

### Post by thesmartace on 2007-07-25
I had the same problem when I tried to revert back to the previous (somewhat working) drivers. The only way I found to get a fully working video card was to ditch the ATI and get a Nvidia. Its amazing how much better you are taken care of by Nvidia :)

---

### Post by leo_rockway on 2007-07-25
we should all send emails to ati and tell them this is not a minor problem and that it not only applies to the x1800 models.

they'll probably just print our emails and wipe their asses with our complaints, but it'sworth a try...

---

### Post by leo_rockway on 2007-08-03
one thing that worked for me (but then again i had some media applications that still worked) was to manually set vlc's output module as X11 video output. VLC works great now


EDIT:
 ATI drivers v8.39.4 are out... you may want to try them and see if they work better for you. So far Regnum Online has been working way better for me.

---

### Post by plux0r on 2007-08-10
Hello again,

Just wanted to keep you guys updated on my (non-existing) progress.
I've tried the new release of the ati drivers, but the issue is still present. :(
I'm visiting my parents atm, so I don't have access to that box atm.
Going to try the VLC hack as soon as I get back, although I prefer using mplayer.

If anyone finds a solution to this problem, please post it here :)

---

### Post by leo_rockway on 2007-08-18
well... i installed the latest ati driver (8.40.4) and the problem is still there.

i used the VLC hack for other player too, telling them not to use overlay (ie. to use X11)

now i can use all my media players w/o the jerky image: kmplayer (with mplayer or xine), mplayer (for X and for CLI) and vlc they all work using the hack.

---

### Post by plux0r on 2007-08-19
Hey guys. 

Still haven't find a proper way to solve this problem, but changing the video overlay in the players seem to work fine! I use the opengl overlay.

It works for mplayer if you use this switch: -vo gl or -vo gl2, and simlairly set OpenGL as overlay in VLC.

I hope ATI can fix their damn drivers :P

---

### Post by leo_rockway on 2007-08-19
i modified ~/.mplayer/config and added the following line:

> vo = gl2

in that way i don't have to tell mplayer to change the video overlay each time.

x11 works as well, but is not as good.

---

