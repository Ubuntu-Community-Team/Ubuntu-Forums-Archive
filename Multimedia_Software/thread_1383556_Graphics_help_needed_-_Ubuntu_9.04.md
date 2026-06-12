---
title: "Graphics help needed - Ubuntu 9.04"
date: 2010-01-17
forum: Multimedia Software
---

### Post by mhmyersnc on 2010-01-17
Hi:
 
I have had Ubuntu 9.04 successfully running on the PC whose monitir i changed. I replaced an old Sony monitor with a new LG 22" monitor. Because the then current configuration wouldn't take advantage of the capabilities of the new monitor, I looked to upgrade that. On Google, I found references to envyNG and since my didplay adapter is an ATI Radeon 2100, I thought this might get me the right driver. After installing the recommended driver and rebooting, I can't login to Ubuntu. I get a mess of squeezed lines at the top of the screen which are unreadable. 
 
When I run the live disk, it uses the monitor perfectly in the 16:9 mode that I was hoping for, but I have not found a successful way to use it to repair the insatlled system on the hard drive. 
 
What do i need to do to replace the corrupt driver and configuration files with ones that will either get me back to the old configuration that would work but would not give me the resolution I wanted, or, preferebly, replace it with one that emulates the live disk without having to completely reinstall Ubuntu and lose the applications I have already installed?
 
Mike Myers

---

### Post by rowbird on 2010-01-17
Hi, Envyng won't work on 9.04 with ATI. Your card is running on open sourced drivers on the live cd. ATI doesn't supply drivers for X84 Linux anymore. You could copy the xorg.conf file from the live cd, then write it to your installed /etc/X11/xord.conf.

---

### Post by mhmyersnc on 2010-01-17
Well, that didn't work. I verified that the xorg.conf files are identical (both seem to be very vanilla - no specifics as to depth, rate, etc.) .  I'm still getting the same unredable screen at startup.
 
Mike

---

### Post by sports.car.guy on 2010-01-17
> **mhmyersnc said:**
> Hi:
 
I have had Ubuntu 9.04 successfully running on the PC whose monitir i changed. I replaced an old Sony monitor with a new LG 22" monitor. Because the then current configuration wouldn't take advantage of the capabilities of the new monitor, I looked to upgrade that. On Google, I found references to envyNG and since my didplay adapter is an ATI Radeon 2100, I thought this might get me the right driver. After installing the recommended driver and rebooting, I can't login to Ubuntu. I get a mess of squeezed lines at the top of the screen which are unreadable. 
 
When I run the live disk, it uses the monitor perfectly in the 16:9 mode that I was hoping for, but I have not found a successful way to use it to repair the insatlled system on the hard drive. 
 
What do i need to do to replace the corrupt driver and configuration files with ones that will either get me back to the old configuration that would work but would not give me the resolution I wanted, or, preferebly, replace it with one that emulates the live disk without having to completely reinstall Ubuntu and lose the applications I have already installed?
 
Mike Myers

You are having xorg.conf isues.

When grub is loading it gives a count down. Press escape and bring up it's boot menu. Choose to boot the system into it's recovery mode and on the screen you are presented with it gives a choice to fix graphics. Try that I and I think it should solve your problem and get you back up and running.

---

### Post by mhmyersnc on 2010-01-17
Thanks. I had tried that earlier and it didn't solve the problem. But, I tried it again as suggested and I get a differeent unreadable display.

---

### Post by sports.car.guy on 2010-01-17
> **mhmyersnc said:**
> Thanks. I had tried that earlier and it didn't solve the problem. But, I tried it again as suggested and I get a differeent unreadable display.


Then odds are you have the incorrect driver for your video card. Get rid of it and go back to the one you had. Or find another version of this one if it is the correct one for your card, run the configuration like i said again after that, and that should solve it.

---

### Post by mhmyersnc on 2010-01-17
Thanks. i like the idea, but where/how do i find the driver? I was looking for a tool in Ubuntu that would give me that information, but don't seem to be able to find one.

---

### Post by sports.car.guy on 2010-01-17
> **mhmyersnc said:**
> Thanks. i like the idea, but where/how do i find the driver? I was looking for a tool in Ubuntu that would give me that information, but don't seem to be able to find one.


If you physically didn't overwrite the file it should be in with your modules.

This driver is it an older ATI / AMD driver that supports your GPU? if so go in under the command line similarly to how you got to the graphics fix option and type (As root):

aticonfig --initial -f

that will tell your system the proper info about the card after a reboot your X should be back up if using an older ATI / AMD driver and not the open source one.

---

### Post by mhmyersnc on 2010-01-17
OK, I'll try that.
 
But, I don't know where the driver is, and I don't know how to identify it (there are lots of modules and places to look for them in the system - what directory would I look for it in?). 
 
Since I don't know what driver I actally have, I can't answer your question about what it supports.

---

### Post by mhmyersnc on 2010-01-17
I tried the aticonfig --initial -f comand and got the reply:
 
No supported adapters detected 
 
This is supposed to be an ATI Radeon 2100 adapter.

---

### Post by sports.car.guy on 2010-01-17
It is either going to use one of two drivers. Here is the page for the Radeon on xorg.

[http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)

It will either use:

[I]xf86-video-radeonhd or xf86-video-ati
[/I]

---

### Post by sports.car.guy on 2010-01-17
> **mhmyersnc said:**
> I tried the aticonfig --initial -f comand and got the reply:
 
No supported adapters detected 
 
This is supposed to be an ATI Radeon 2100 adapter.

There is your problem. Remove the ATI / AMD drivers. You are using too new of a version and it does not support your video card any longer. The open source drivers will fix that.

Go to /etc/xorg.conf and change fgrlx to one of the open source drivers I put in my previous post. Just make sure it is the right one for your carf. The newer cards can use the non HD driver but not sure the other way around with older ones. It depends on the model.

---

### Post by mhmyersnc on 2010-01-17
Well, there was no fglrx anywhere in the xorg.conf, so nothing to remove. 
 
I tried both the driver names you suggested in the Device section, adding the line:
 
          Driver    "name_as suggested" 
 
and tried both, with the same resulting garbage display.

---

### Post by mhmyersnc on 2010-01-17
You told me to delete the drivers. That can mean one of two things: a) find the driver modules and delete them, 2) remove the Driver statement from xorg.conf that identifies the driver. 
 
There were no Driver statements in xorg.conf to begin with, is that sufficient? Or, do I have to do a search and destroy on some specific modules? If that is the case, how/where do i find them?
 
Also, do the statements in xorg.conf have their values separated by spaces or tabs? If it's tabs, would they still work with spaces?

---

### Post by sports.car.guy on 2010-01-17
> **mhmyersnc said:**
> You told me to delete the drivers. That can mean one of two things: a) find the driver modules and delete them, 2) remove the Driver statement from xorg.conf that identifies the driver. 
 
There were no Driver statements in xorg.conf to begin with, is that sufficient? Or, do I have to do a search and destroy on some specific modules? If that is the case, how/where do i find them?
 
Also, do the statements in xorg.conf have their values separated by spaces or tabs? If it's tabs, would they still work with spaces?

You need to remove the fglrx on your system. There is probably conflicting libraries happening. It has to be on your system. That is the only way aticonfig could be on your system. It is an application distributed with their drivers and would not be installed with a default system that does not have a GPU requiring fglrx.

There not being a reference to it in xorg.conf should be enough but like I said it sounds like a library issue.

---

### Post by mhmyersnc on 2010-01-17
OK, I did a find on fglrx and got a lot of hits. Everything seems to be in either:
 
disk/var/lib/dpkg/info     - I suspect this is apt-get info
 
and
 
disk/var/lib/dkms/fglrx    - I suspect this is the installed package
 
and others, such as:
 
di-sk/lib/modules
disk/usr/share
etc.
 
I am guessing I should use apt-get remove fglrx or something like it to get rid of this stuff. Should I then do an apt-get remove ati.. (whatever) as well to clean this up?

---

### Post by sports.car.guy on 2010-01-17
I would think that should solve your problem but you need to make sure that it removes all the files, including the configuration that can and is usually left behind. I am not sure the command for it via a terminal though.

I googled it and here is the example I found on how to get apt-get to do it.

apt-get --purge remove mozilla-firefox

---

### Post by mhmyersnc on 2010-01-17
Removing Firefox seems strange to me. Why Firefox? 
 
Of course I can re-install it afterwards, but why not use the same to purge (remove) fglrx instead (especially if it's that driver that's causing the problem)?

---

### Post by sports.car.guy on 2010-01-17
That was an example I found on the net directly on how to get apt-get to remove the configuration files.. Replace firefox with fgrlx

---

### Post by mhmyersnc on 2010-01-18
I found fglrx in a couple of different packages (fglrx-kernel-source and xorg-driver-fglrx) and I removed both of them. That got things back to mostly correct. 
 
After getting started again and making a vanilla xorg.conf, everything was back to normal and exactly the way i wanted, with the workspace taking full advantage of the display's capabilities. 
 
Many thanks. It was a painful lesson, but one in which I learned a lot about recovery. 
 
Thanks again for all your help. 
 
Mike

---

### Post by sports.car.guy on 2010-01-18
> **mhmyersnc said:**
> I found fglrx in a couple of different packages (fglrx-kernel-source and xorg-driver-fglrx) and I removed both of them. That got things back to mostly correct. 
 
After getting started again and making a vanilla xorg.conf, everything was back to normal and exactly the way i wanted, with the workspace taking full advantage of the display's capabilities. 
 
Many thanks. It was a painful lesson, but one in which I learned a lot about recovery. 
 
Thanks again for all your help. 
 
Mike


Mike it was not a problem. You have been someone willing to try to figure this out and help yourself. I am glad it worked.

There might be some other packages still floating around your install for fgrlx. Just check to be safe.

---

