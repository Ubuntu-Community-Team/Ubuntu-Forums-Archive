---
title: "Dapper ati radeon xpress 200 freeze on logout"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by redjim on 2006-06-06
I used breezy and got the video working perfectly on my hp amd athlon x2 mediacenter machine.  I tried to upgrade to dapper using the upgrade distro option on upgrade manager, but it got stuck on pcmcia so I just did a clean install of dapper.

I have been messing with the dapper install and the video for about 4 days now.  If I use the vesa driver or ati driver in my xorg.conf.  I can only get 640x480, but I can log in  and out.  
Now I have followed the instructions in the howto 

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
reboot

Now my video looks great, but when I log out, my screen freezes and I have to power off my computer.  I have read everything, but I don't know what to do.
Does anyone have a suggestion for me??

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

$ dmesg | grep fglrx
[4294698.648000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294698.649000] [fglrx] Maximum main memory to use for locked dma buffers: 866 MBytes.
[4294698.649000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294699.116000] [fglrx] total      GART = 67108864
[4294699.116000] [fglrx] free       GART = 51118080
[4294699.116000] [fglrx] max single GART = 51118080
[4294699.117000] [fglrx] total      LFB  = 59699200
[4294699.117000] [fglrx] free       LFB  = 49213440
[4294699.117000] [fglrx] max single LFB  = 49213440
[4294699.117000] [fglrx] total      Inv  = 0
[4294699.117000] [fglrx] free       Inv  = 0
[4294699.117000] [fglrx] max single Inv  = 0
[4294699.117000] [fglrx] total      TIM  = 0

---

### Post by gmcauley on 2006-06-06
Hi redjim,

I hate to be the bearer of bad news but this is a bug:

[https://launchpad.net/distros/ubuntu/+source/xorg-driver-fglrx/+bug/30447]("https://launchpad.net/distros/ubuntu/+source/xorg-driver-fglrx/+bug/30447")

---

### Post by titus1950 on 2006-06-06
I have the same problem (when I log out, my screen freezes)
What I am doing for now is to click on System>Quit,whitout moving the mouse for 2 seconds after that and then  I can move it whitout freezing problems,then turn pc off, reboot or else....
Hope they fix this soon....

---

### Post by redjim on 2006-06-06
[QUOTE=gmcauley]Hi redjim,

I hate to be the bearer of bad news but this is a bug:

[https://launchpad.net/distros/ubuntu/+source/xorg-driver-fglrx/+bug/30447]("https://launchpad.net/distros/ubuntu/+source/xorg-driver-fglrx/+bug/30447")[/QUOTE]

You ruined my day ;)  I had hoped it was just my usual lack of knowing what I am doing.

Thanks, for the link

SO Do I understand correctly that I should just go back and re-install breezy????

---

### Post by deadgobby on 2006-06-06
[QUOTE=redjim]You ruined my day ;)  I had hoped it was just my usual lack of knowing what I am doing.

Thanks, for the link

SO Do I understand correctly that I should just go back and re-install breezy????[/QUOTE]
 There is a artical at Distrowatch how to work around the bug for now.
[http://distrowatch.serve-you.net/weekly.php?issue=20060605#news](http://distrowatch.serve-you.net/weekly.php?issue=20060605#news)
(Exerpt)
[COLOR="Red"]I want to end this mini-review on a happy-happy note, so let's get the negative stuff out of the way first. The most noticeable problem was with the video driver. I currently have two (only two?) computers, a laptop and a desktop. Coincidentally, both machines use the "ati" driver, and with Dapper both machines display what looks like "snow" in the "radio buttons" (those "OK" and "Cancel" buttons) in certain applications. This is a minor annoyance, but not fatal. Unfortunately, (on the laptop only) I also experience fatal screen crashes at the login screen whenever I move the mouse cursor. Interestingly, this only occurs if I login and logout at least one time after bootup - it will not occur at the first login. I can only recover from the crash with a hard reset, which means pulling the plug and removing the laptop's battery, since this machine has no reset button. This bug did not occur in Ubuntu Breezy, or any other distro I've used to date.

I reported this bug and received a polite response from the developers. While waiting for a fix, I've found a reasonable workaround. I edited file /etc/X11/xorg.conf and replaced the "ati" driver with "vesa". The vesa driver works with just about any hardware, but it's a noticeably slow driver. I no longer experience crashes, but I can forget about playing PlanetPenguin-Racer (ppracer, formerly known as TuxRacer).[/COLOR]

---

### Post by twstokes on 2006-06-06
I had the same problem in Breezy also - with acceleration. Without acceleration it never locked up, so if you don't need OpenGL support and extra "smoothness" you'll be free from those hard lock ups. 

I recently upgraded to Dapper also, but it wasn't working with my dual screens correctly. It also screwed up sometimes just like in Breezy when I went to reboot.

After getting so fed up with the never ending "sudo vi /etc/xorg.conf" followed by a CTRL+ALT+BKSPC and never getting anything to work right, I debugged it all for $94 bucks and bought an NVIDIA.

Maybe I could get in there and fix the problems myself, but how will I ever learn how to do that stuff if I can't get Linux to run right in the first place?

---

### Post by red0menace on 2007-02-05
Hey all, first post here

I just recently put Dapper on a box at home (athlon 64, 3200+ with integrated radeon xpress 200).  I installed the xorg-driver-fglrx driver (8.25 according to fglrxinfo) for decent resolutions with my ATI card, but ran into the logout freeze problem.

I didn't see a solution posted, but I think the error was fixed in the 8.26 release of the fglrx drivers from ATI.  Here's the post on how to install them:

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

---

