---
title: "Dual screen crash intel hd graphics"
date: 2011-06-22
forum: Multimedia Software
---

### Post by Havel on 2011-06-22
Hi,
After 2 months without any problems, my second screen plugged on my laptop has stopped working. It works on my windows partition. When I start the computer, I see the login screen on both screens. When I enter the password, both screen turn to black. If I unplug the extra monitor, the laptop start normally.

I'm on Ubuntu Natty, my laptop is a Thinkpad E420s with Intel HD graphics, i5 cpu, 4gb ram.

Help would really be appreciated

---

### Post by BicyclerBoy on 2011-06-23
It is most likely an update..

You could roll back the kernel at the GRUB startup/boot screen to a previous version(s).

If that fails to solve the problem I would look into the history log in synaptic package manager. This gives you a time & date of all update activities so you can bisect the problem.
Packages that are likely culprits are xorg, intel drivers & kernel updates.
Synaptic will allow you to force a specific version to install & then lock a version.

If is was the kernel, then synaptic manager lets you deal to it as well..

If you want to throw all caution to the wind... use the xorg-edgers ppa for the intel graphics driver.
There is a lot of development with intel Sandybridge & fixing up/completing the Nehalem/Westmere graphics (i3,i5).
I never got any intel graphics performance before using xorg-edgers.

---

### Post by Havel on 2011-06-23
Well, there were no recent xorg, intel drivers & kernel updates...I mean in the last 10 days. My problem started yesterday.

I tried the xorg-edgers ppa for the intel graphics driver, with no results.

As soon as I plug my second screen, everything turns to black. When I restart, i see the login screen on both screens...after entering password everything turns to black.

I also tried to reset my xorg config file with the command line:

sudo dpkg-reconfigure xserver-xorg

No luck...

Would a fresh install give more chances of going somewhere?

It makes me sick thinking I have to go to Windows to get my dual screen back. This is a big disappointement.

---

### Post by BicyclerBoy on 2011-06-23
From my web searches your laptop is a sandybridge i5 or the latest E420 is...

Have you enabled the intel driver in /etc/X11/xorg.conf ?

glxinfo | grep OpenGL

After adding the xorg-edgers ppa were there some 10-20 items updated ?

I have a feeling my natty box had some updates in the last couple days..

---

### Post by Havel on 2011-06-23
My laptop is indeed a sandybridge i5

What should I precisely do to enable the intel driver in /etc/X11/xorg.conf

Yes, after adding the xorg-edgers ppa there were some 10-20 items updated...I also added the other ppa related to intel graphics (ppa:sarvatt/intel-sna)... but got no changes with dual screen.

I went in the updates history...but in fact i forgot to say that my install iss about ten days old since I had to reinstall to add a Windows partition.

---

### Post by BicyclerBoy on 2011-06-23
glxinfo | grep OpenGL

I would suggest using synaptic to install the previous kernel..

---

### Post by Havel on 2011-06-23
This what "glxinfo | grep OpenGL" gives:

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
OpenGL extensions:

---

### Post by Havel on 2011-06-23
Since my install is ten days fresh, I dont have other kernels in Synaptic.

---

### Post by BicyclerBoy on 2011-06-23
Well my only other idea is to try different cabling to 2nd monitor..

I thought I had read about problems Intel & displayport or HDMI connected 2nd monitors..

You are running the intel driver.

You should be able to find older linux kernel packages in synaptic ?

What does 
```
uname -r
```
return ?

---

### Post by Havel on 2011-06-24
Thanks for trying to help, but I was so much out of ideas on what to do that I decided to reinstall. Finding a real solution would have been better, but I needed my dual screen setup and I did not want to choose Windows as my main desktop.

There seem to be a problem with the intel driver, so i decided to block updates on it. I did update the kernel without any damage. So far so good. I will leave it like that until the next release.

Thanks again.

---

### Post by Havel on 2011-06-24
Lets laugh a bit...
I'm back to square one. I lost my dual screen again...even if the intel driver update was blocked. I tried a previous kernel...it does'nt work.
My next step will be to try a vga out connection to my extra screen.

I am really ?&$*//&?$&%?%$

---

### Post by Havel on 2011-06-24
uname -r

gives

2.6.38-10-generic-pae

---

### Post by BicyclerBoy on 2011-06-24
We/you could try some xrandr cmd-line incantations..to set the 2nd monitor on.

If you made a working script with a desktop launcher..

xrandr -q
xrandr --prop

Does this show a 2nd monitor port with it disabled ?

Assuming 2nd monitor is called LVDS1 & has res 1920x1200 (24" 16:10).
xrandr --addmode LVDS1 1920x1200_60.00

xrandr --output LVDS1 --mode 1920×1200
or
xrandr --output LVDS1 --auto


[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by Havel on 2011-06-24
I will try your suggestion later on. For now I can say that vga to vga works. So its a HDMI problem with the Intel card. I would still want to go back to HDMI...image quality is not very good on vga.

---

### Post by BicyclerBoy on 2011-06-24
Good that you could confirm..& have a temporary work-around.

Others have reported (2 weeks ago) that simply using an HDMI-DVI (singlelink) cable solved this same/similar problem.

H/W was H67 chipset & sandybridge graphics

---

### Post by Havel on 2011-06-25
I was already using a HDMI to DVI connection.

---

### Post by BicyclerBoy on 2011-06-25
That just confirms that you can't believe everything you read on the web but only what you know/prove for yourself.

Electrically a single link DVI-D cable is identical to a HDMI cable.
The controller can only determine that a different output wired port was used & that was likely the solution.

---

### Post by Havel on 2011-06-25
Maybe I was not clear. The only thing that work now is VGA to VGA. My problematic connection is HDMI to DVI.

---

### Post by BicyclerBoy on 2011-06-25
I know that.
And it was suggested to try it on post #9.
Did you not get that ?

> Others have reported (2 weeks ago) that simply using an HDMI-DVI (singlelink) cable solved this same/similar problem.

My comments in the last 2 posts were not directed at you.
They were directed at the info I found on the web (2 posts ago)...

---

### Post by Havel on 2011-06-26
This is getting interesting, to say the least...

My vga to vga connection is down, no more dual screen...

---

### Post by Havel on 2011-06-26
Since I cannot use command line when second screen is plugged because it does'nt work,I tried the commands using startup programs menu.

So for HDMI to DVI I tried separately:

xrandr --addmode HDMI1 1680x1050_60.00

xrandr --output HDMI1 --mode 1680x1050

xrandr --output HDMI1 --auto

I did the same for VGA to VGA, replacing HDMI1 by VGA1

Without succes...

---

### Post by Havel on 2011-07-03
After reading left and right on the forum it seems like dual monitor is a big problem in Natty with Unity-Compiz. It illustrates once more how much Unity was'nt ready for prime time when released in april, it is in early beta stage at best. Canonical should have been more honest with that. It could have released Natty with gnome 2 as default desktop, saying you can try Unity but it still needs a lot of work, its not quite ready yet.

So what I did to get my second screen back was to use gnome classic with metacity compositing instead of compiz. Clearly Unity-compiz cannot handle dual screen monitor setups.

I like Unity very much. Lets hope its "really" ready for the next release.

---

### Post by Magnes on 2011-08-09
It's almost 11.10 but I don't see it fixed. What is worse - it was working for me (more or less) and broke after last update. Right now trying to turn off laptop screen turns off both screens (probably crashes Unity) - and I got to this point after much work because at first Unity wasn't working at all after the update. :|

---

