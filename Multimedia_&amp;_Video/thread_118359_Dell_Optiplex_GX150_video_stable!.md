---
title: "Dell Optiplex GX150 video stable!"
date: 2006-01-16
forum: Multimedia &amp; Video
---

### Post by stream303 on 2006-01-16
Don't pull your hair out running one of these:

Ubuntu 5.10
Dell Optiplex GX150 desktop form-factor
19" LCD at 1280x1024 resolution

To cut a long story short:
1. Use only onboard i810/i815 video.  Disable AGP in Bios.
**2. Change default color depth down from 24 to 16**

(maybe edit xorg.conf manually, or run sudo dpkg-reconfigure xserver-xorg and use 16 color depth when prompted)

I've spent the last few weeks trying to use AGP video cards keeping in mind the power supply and form factor.  I've edited xorg.conf options and restarted init.d/gdm so many times I may have worn out my keyboard.  My vi skills are improving though..:) 

What was so frustrating was that AGP cards would work only 99% of the time before it would eventually hard-reboot the machine!  Gotta' love that ext3 filesystem for surviving 60 or so hard crashes as I tried to get it to work.

So now my gx150 is 100% stable!

---

### Post by tan on 2006-02-26
I had a similar problem with GX150 and the on-board video. When I try to set the resoluion to 1280x1024, random, vertical stripes (distortion) appear on the screen. On 1024x768 (and lower) the screen is OK. I was starting to get frustrated... but I found your solution. I think it solved the problem. Thank you!!!

---

### Post by cMadman on 2007-04-12
Sorted me out too. Much appreciated. Good guide.

---

### Post by joegeek on 2007-07-08
Thanks,...  worked great,..  just had to figure out the whole root password thing,...  lil different from redhat/fedora,...

---

### Post by TeeAhr1 on 2007-11-14
Thx!

---

### Post by gmandret on 2008-01-02
being VERY new to Ubuntu I'm having a hard time doing this?  What are the steps in getting rid of the lines ?:(

---

### Post by dmessier on 2008-01-11
Run sudo dpkg-reconfigure xserver-xorg from the terminal and accept the defaults. One of the last questions will be about color depth. Switch from 24 to 16. 

Reboot, and then you're good to go without lines.

---

### Post by HeinekenPissr on 2008-01-22
I can't even boot up the live cd to install on my GX 150

I get the following errors upon starting the live cd:

/etc/gdm/failsafeXServer line 47  "get edid not installed"
/etc/gdm/failsafeXServer Line 189 "Bus error"
could not generate /etc/X11/xorg.conf.failsafe for vesa driver

then it tells me to fix the xorg.conf and reboot

Problem is i don't even have it installed yet

I am running the integrated Intel 82815 graphics chipset

---

### Post by HeinekenPissr on 2008-01-27
Thanks a lot for all the great info.  Worked on my GX150 intel 82815 graphics card too.

I have two additional pieces of input to add
1) when i initially ran the live cd it booted up to an unusable light brown screen with flickering vertical lines.  It took some time to figure out how to get to the terminal to run 'sudo dpkg-reconfigure xserver-xorg'.  I will also explain that below
2) enabling direct 3d rendering - now supertux runs smooth for the nephews

The first problem:
I booted Xubuntu Live CD and i get an unusable screen of vertical lines.  As soon as this happens i hit Ctrl-Alt-Backspace to restart the x-server and bring you back to the login screen where you can visualize well enough to select session --> Failsafe Terminal and with ubuntu as the user name and no password

now at the terminal you type "sudo dpkg-reconfigure xserver-xorg" as noted earlier in this post and you use all the defaults except for the last value where you change from 24 bit color to 16 bit color.

following this the file will save and you will need to hit Ctrl-Alt-Backspace again to restart the xserver and now your graphics are perfect :) and you can install ubuntu.


2) ENABLING 3d direct rendering support so you can run opengl based applications like supertux

This took me many hours to figure out so let me save you the trouble
- first go into terminal and type "glxinfo |grep direct" you will receive output saying that 3D rendering is disabled.  If your 3d rendering is already enabled then don't continue.
-to find out why it is disabled type in terminal "export LIBGL_DEBUG=verbose" and then use the command "glxinfo |grep direct" again.  Now it should tell you that the driver is not loaded or not found.
-Now we install the driver by going into synaptic and searching for "libgl1-mesa-dri" marking the box and installing it.  Now restart your X-server with Ctrl-Alt-Backspace and your good to go.

---

### Post by doozy on 2008-03-14
Great tip re. the Gx150 Video line noise. I have just installed Ubuntu from a Linux Format cover disk and had the same issue on my Dell Optiplex.

Ran the Terminal command above and all worked well after restarting the system.

Checked the 3D rendering thing and the command output for the "glxinfo |grep direct" just gave back:

direct rendering: Yes

So I guess it's good to go. Now to see what this baby can do..

Thanks for the support.

---

### Post by likemindead on 2008-04-15
Perfect! Many thanks. My appreciation for this community is ever increasing exponentially.

(You might consider adding a "SOLVED" to this thread title.)

---

