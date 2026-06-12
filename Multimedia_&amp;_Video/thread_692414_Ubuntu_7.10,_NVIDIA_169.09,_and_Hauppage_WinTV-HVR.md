---
title: "Ubuntu 7.10, NVIDIA 169.09, and Hauppage WinTV-HVR-1600 oh my!"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by kody on 2008-02-09
DISCLAIMER:  I'm actually using Linux Mint.  But I guess this distro would have the same problem/solution as Ubuntu 7.10.

After successfully manually installing the latest 169.09 Nvidia drivers for my 8800 GT a while ago, I was feeling pretty cocky  and thought I'd give the beta drivers for my semi-supported Hauppage WinTV-HVR-1600 a whirl.

Yes, perhaps I was in a little over my newbie head, but here's what I did.

After much googling, I couldn't find a nice linux mint/ubuntuforum post about successfully installing the tuner card, but Hauppage now has nice install instructions on their website:
[http://www.hauppauge.com/pages/faq/support_faq_hvr1600.html#3a](http://www.hauppauge.com/pages/faq/support_faq_hvr1600.html#3a)

Here's what the page states: 
> Can I use the WinTV-HVR-1600 with Linux?

There is a new beta from LinuxTV.org with a Conexant cx23418 driver which supports the Hauppauge WinTV-HVR-1600 card.

The driver is available here:

[http://www.linuxtv.org/hg/~hverkuil/cx18](http://www.linuxtv.org/hg/~hverkuil/cx18)

The easiest way to build it is to get the tar.bz2 archive:

[http://www.linuxtv.org/hg/~hverkuil/cx18/archive/tip.tar.bz2](http://www.linuxtv.org/hg/~hverkuil/cx18/archive/tip.tar.bz2)

Unpack, 'make', 'make install' (as root), 'make unload' (as root) and run 'modprobe cx18'.

There is still a lot of work to be done, in particular there is nosupport for the ATSC stream. What is working is basic MPEG capturing, raw YUV capture and raw PCM capture. Also pretty much all of the controls that were also in ivtv are working with cx18.

The firmware needs to be extracted from the Windows Hauppauge HVR-1600 driver, available here:

[http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip](http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip)

Unzip, then copy the following files to the firmware directory and rename them as follows:

Drivers/Driver18/hcw18apu.rom -> v4l-cx23418-apu.fw Drivers/Driver18/hcw18enc.rom -> v4l-cx23418-cpu.fw Drivers/Driver18/hcw18mlC.rom -> v4l-cx23418-dig.fw


I was able to follow all those steps, and copied the renamed files to /lib/firmware/2.6.22-14-generic.  I took a shot in the dark about that directory, and maybe that's where I went wrong?

Anyway, I rebooted after all that, and upon reboot the xserver couldn't find the NVIDIA driver and would default to VESA (which I'm writing from now).  

I tried manually editing my xorg.conf file, but it still seemed intact.  

In a state of panic, I tried to manually re-install the NVIDIA driver, but it still sensed that the driver was already installed.  No matter, it uninstalled that one, and reinstalled the new one.

However, upon reboot, the same thing happens.  I can't access the NVIDIA display driver.

I suspect that I narfed my kernel somehow by installing the Hauppage driver, and since the proprietary NVIDIA driver needs some sort of special interface (I'm a newb) to the kernel, it can't find it?

Can anyone help me de-narf my display?   :oops: 

Thanks!!

---

### Post by timczer on 2008-02-11
I guess this reply will serve as a bump for you if nothing else.  I have the same issue.  Followed the instructions you listed as well, and ended up with the same problem.  I am using a previous Kernel (2.6.20) to boot into now.

I tried deleting the three firmware files that the instructions said to put into the firmware folder but that didn't help.

There is a last line of the instructions:
Note that if you get the message "Could not start the CPU" then edit cx18-firmware.c, go to line 350 and change the '#if 0' to '#if 1' and see if that helps. It is not clear to me whether that is needed or not, I get conflicting results.

I looked at this file, but line 350 does not contain that code.  Also, I don't know where that file was sent to when installing the driver.

I think the solution might be to remove the module that was inserted with the command  "modprobe cx18", just not sure how one goes about removing a module.

---

### Post by timczer on 2008-02-11
The solution to get your system back is to boot into the bad kernel, let it go until you get past the error message, get to the command line.  Then run "sudo modprobe -r cx18"  and you should be able to start the x-server.

The bigger question is how to get this tuner card working properly.

---

### Post by timczer on 2008-02-11
Spoke too soon on the solution.  After running the modprobe command, I ran a startx command and booted to my system fine.  When I restarted the computer, it would not boot into the login screen.  I deleted and reinstalled the nvidia driver and still no boot to login.  if I rerun the modprobe command and then run startx from the command line I get into the system.

Is there a way that even though I ran "modprobe -r cx18, this module would reload on the next start up?

---

### Post by kody on 2008-02-11
I also tried to modprobe -r cx18, and reinstall the NVIDIA drivers to no avail.

I also tried to MAKE UNINSTALL, but that didn't work either.

I'd love to figure out how to make this tuner card work, but in the meantime I think I may just reinstall my OS.  Really crappy solution though IMO.

---

### Post by kooldino on 2008-02-11
Just picked up this card today...I won't install it until there is a working solution.

---

### Post by kody on 2008-02-19
I tried a sudo make unload tonight, and that unloads all the modules related to cx18 quite nicely.  However, they return when you reboot! Even if you do a sudo modprobe -r cx18 afterwards. :(

Any way to remove these drivers once and for all?

---

### Post by rxbandit on 2008-02-23
I'm in the same boat i installed the beta driver it hosed my nvidia driver i believe.When i rebooted X is running at low res. Can't seem to uninstall the beta driver. Wasn't able to get any output from the card either, but it does get intialized according to dmesg. Anyone able to remove the driver? Another awesome thing, I updated some packages and that killed my audio....ubuntu and sound cards do not mix for some reason.

---

### Post by anth120 on 2008-03-02
I wish I took this post to heart. The same thing has happened to me. Anyone have any luck fixing it without reinstalling the OS?

I get an error about low resolution upon startup, and X is limited to VESA drivers and 800x600 resolution. I can't even get the video card to work. What a bust.

---

### Post by anth120 on 2008-03-02
I'm not sure which of these fixed it - but I did "make remove", "make clean" , and "make uninstall" and I deleted the firmware files. I also unchecked the v4 driver in the Restricted Drivers window.

My display is working now...

No go on the driver though. As far as I can tell, it's nonfunctional. Hopefully something better will surface soon.

---

### Post by Cresho on 2008-03-02
I tried installing the drivers on my hardy heron.  I get an error line something so thank godness I didn't go through any of you guys problem.  I can't believe I boot into windows just to get this none supported card under linux working.  I may get a new hd card in light of this situation.  I do watch tvtime using my old avermedia tv analog card.  It has worked for me just fine.

---

### Post by kahrytan on 2008-03-03
I installed the cx18 drivers and It worked for me. And I use official nvidia drivers.

 Though, tvtime won't work but that's known. cx18 hasnt been designed to work with it. Mythtv, I can't get to work but im newbie. 

Videolan sometimes works and sometimes doesn't


However, cat /dev/video0 > tv.mpg  works just fine.


In the end, the driver does work. It just need more work. after all, it is beta

---

### Post by gusman21 on 2008-03-24
> **kahrytan said:**
> 
However, cat /dev/video0 > tv.mpg  works just fine.


try ```
 cat /dev/video0 | mplayer - 
```

---

### Post by timczer on 2008-03-29
Kahrytan, How did you go about installing the driver?

---

### Post by Megatog615 on 2008-04-15
[quote=timczer]There is a last line of the instructions:
Note that if you get the message "Could not start the CPU" then edit cx18-firmware.c, go to line 350 and change the '#if 0' to '#if 1' and see if that helps. It is not clear to me whether that is needed or not, I get conflicting results.[/quote]That line is no longer at line 350. It is now at line 333.

Problem is I get a kernel panic when I modprobe cx18.

---

### Post by usererror on 2008-04-29
Perhaps someone here can save me.  I just bought this card to replace my aging Hauppage WinTV card from 1995-ish.

The drivers on Hauppage's website are a no go from linuxtv.org - dead links.

Where did you guys get the driver and what did you do to make it work?

Thanks in advance!

---

### Post by Spr0k3t on 2008-05-05
The drivers are still very much beta.  I was able to get it working for a little bit until I performed a kernel update.  You can find details of the beta driver on the myth & ivtv wiki

[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600)
[http://ivtvdriver.org/index.php/Cx18](http://ivtvdriver.org/index.php/Cx18)

Oh yeah, in case you have any problems with the firmware, it can be found in /libs/firmware/

With the standard build of Mythbuntu 8.04, you will need to have ncurses-dev, build-essentials, and linux-header-generic to compile the drivers.

---

### Post by willoconley on 2008-05-15
if you guys want both modules to load rebuild the nvidia driver by following this:
[http://tinyplanet.ca/~lsorense/debian/debian-nvidia-dri-howto.html](http://tinyplanet.ca/~lsorense/debian/debian-nvidia-dri-howto.html)

now can someone tell me how to tune some channels with this blasted thing:confused:

---

### Post by saedelaere on 2008-05-15
If somebody still in search for a frontend you could try to use TV-Viewer which I announced [here]("http://ubuntuforums.org/showthread.php?t=763698")

It makes use of the ivtv utils so not all functions may be supported on your hardware.

If it works for you please give me short feedback!

Thanks
Sadelaere

---

### Post by Megatog615 on 2008-06-27
If anyone is stuck at the console with the nvidia breakage, simply add "blacklist cx18" to your /etc/modprobe.d/blacklist. This will prevent cx18 from loading on startup and the nvidia driver will once again work for you.

---

