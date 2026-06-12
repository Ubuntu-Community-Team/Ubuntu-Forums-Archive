---
title: "Running X with intel"
date: 2009-08-26
forum: Multimedia Software
---

### Post by SAS_Sam on 2009-08-26
Good morning, afternoon, evening,
 
My name is Sam and I'm new to Ubuntu. I've installed a panel PC with Ubuntu 9.04 desktop edition (Jaunty).
I've update & upgrade the system by using the apt-get command, so I have the latest kernel (2.6.28-15-generic)
 
**_My question:_**
 
I can't seem to run X with the intel driver, only the vesa driver works.
I have tried several drivers:
 
1) apt-get install xserver-xorg-video-intel
2) apt-get install xserver-xorg-video-intel-2.4
3) The drivers available from the intel.com website (they don't seem to compile on Jaunty)
 
Every time I start Ubuntu with **driver "intel"** I'm getting the message that ubuntu couldn't detect any usable settings, and that I can not boot (I can only boot in init 3)
 
Another weird thing is that when I go to **system** -> **preferences** -> **display **
I see in the display preferences: "Monitor: Unknown" (and my maximum resolution is 640x480)
 
It says that my monitor is detected, but no usable configuration found.
 
Anyone has any idea about this?
Thanks on advance,
 
Sam.
 
**_Xresprobe:_**
 
[COLOR=black]root@sas-desktop[/COLOR][COLOR=black]:~#[/COLOR] xresprobe vesa
id: 
res: 
freq: 
disptype: 
 
(Same result if I use xresprobe i810 or xresprobe intel)
 
**_Dccprobe:_**
 
root@sas-desktop:~# ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller Hardware Version 0.0
memory: 32576kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail
 
**_Xorg.conf:_**
 
See attachement (you can ignore the penmount block, it's for the touchscreen, that works)

---

### Post by SAS_Sam on 2009-08-26
bump

---

### Post by SAS_Sam on 2009-08-27
bump

---

### Post by SAS_Sam on 2009-08-28
and bump again, anyone that has ANY idea? Just a push it the right direction would be awesome.

---

### Post by MIKE SILVA on 2009-09-07
Hi,

I Don't if it helps, but you could try.

edit you xorg.conf

and enter this text:

Section "Device"
Identifier "Configured Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Device"
EndSection 


I have the same problem with "vesa".
If the driver don't appear, usually it works.

Regards

---

### Post by SAS_Sam on 2009-09-07
Hello,
 
thanks alot for the reply!
Buf unfortunately it doesn't work :(
 
I'm getting a dialog box that '**no usable configuration**' was found.
Then I can choose between repair, etc.
 
Grts,
Sam

---

### Post by erakko on 2009-09-07
I have this kind of problem too :( But luckily my max-resolution is 1024x768, but on 8.10 it was even 1280x960, and Compiz worked too. After upgrading to 9.04 everything was ****** up, now this computer can't even read discs. But still it's usable, it's just that developing games is a bit frustrating with such a small resolution.

So, when I have set Driver "intel", I get startup error that tells me that it failed to configure my device, and only way to use this computer is to select "use low-graphics mode". When I set Driver "vesa", it works greatly, but it's just that vesa has only standard resolutions, so I can't change it back. At least startup is faster by then...

I attach my Xorg.log, there was something fishy in the startup errors, but I don't know where those logs are :S

---

### Post by Whiffle on 2009-09-07
> **SAS_Sam said:**
> Hello,
 
thanks alot for the reply!
Buf unfortunately it doesn't work :(
 
I'm getting a dialog box that '**no usable configuration**' was found.
Then I can choose between repair, etc.
 
Grts,
Sam

Could you post up the contents of /var/log/Xorg.0.log ?

---

### Post by Whiffle on 2009-09-07
> **erakko said:**
> I have this kind of problem too :( But luckily my max-resolution is 1024x768, but on 8.10 it was even 1280x960, and Compiz worked too. After upgrading to 9.04 everything was ****** up, now this computer can't even read discs. But still it's usable, it's just that developing games is a bit frustrating with such a small resolution.

So, when I have set Driver "intel", I get startup error that tells me that it failed to configure my device, and only way to use this computer is to select "use low-graphics mode". When I set Driver "vesa", it works greatly, but it's just that vesa has only standard resolutions, so I can't change it back. At least startup is faster by then...

I attach my Xorg.log, there was something fishy in the startup errors, but I don't know where those logs are :S


Is there more to your xorg log?  There should me some more stuff at the end.

---

### Post by SAS_Sam on 2009-09-07
my xorg.conf is in the first post I've made (see attachement)

---

### Post by Whiffle on 2009-09-07
> **SAS_Sam said:**
> my xorg.conf is in the first post I've made (see attachement)

Not quite the same, I'm looking for the xorg.0.*log* file.  Its the log thats created every time X starts, placed in /var/log.  It should give a good hint as to whats going on.

---

### Post by SAS_Sam on 2009-09-07
Ok sorry my bad, see attachement of this post :)

---

### Post by Whiffle on 2009-09-07
> **SAS_Sam said:**
> Ok sorry my bad, see attachement of this post :)

I detect a case of the moooondays :-P   Might check that one again ;)

---

### Post by SAS_Sam on 2009-09-07
Jeezes Christ what am I doing?! :???: ](*,)
 
Ok it should be there now, if it's xorg.conf again then just ignore me from now on :P
 
Thanks allready for your time

---

### Post by erakko on 2009-09-07
> **Whiffle said:**
> Is there more to your xorg log?  There should me some more stuff at the end.

No. It was longer when I booted with "vesa" setting (like now), but with "intel" it's just that.

---

### Post by Whiffle on 2009-09-07
> **SAS_Sam said:**
> Jeezes Christ what am I doing?! :???: ](*,)
 
Ok it should be there now, if it's xorg.conf again then just ignore me from now on :P
 
Thanks allready for your time

```

(II) intel(0): Output VGA disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"


```  

It appears to be thinking that there is no VGA connected.  Is there?  Or is this a laptop (tablet?)?     


I think I would try adding:

```

Option "ForceSDVODetect" "on"

```

to the device section of your xorg.conf

---

### Post by Whiffle on 2009-09-07
> **erakko said:**
> I have this kind of problem too :( But luckily my max-resolution is 1024x768, but on 8.10 it was even 1280x960, and Compiz worked too. After upgrading to 9.04 everything was ****** up, now this computer can't even read discs. But still it's usable, it's just that developing games is a bit frustrating with such a small resolution.

So, when I have set Driver "intel", I get startup error that tells me that it failed to configure my device, and only way to use this computer is to select "use low-graphics mode". When I set Driver "vesa", it works greatly, but it's just that vesa has only standard resolutions, so I can't change it back. At least startup is faster by then...

I attach my Xorg.log, there was something fishy in the startup errors, but I don't know where those logs are :S


I think the fishy parts you speak of can be found in /var/log/kern.log, could you post that up ?

---

### Post by SAS_Sam on 2009-09-07
It's a tablet PC indeed, check my first post :P
 
I've added Option "ForceSDVODetect" "on" to xorg.conf, tried, but getting the "low graphics mode".

---

### Post by erakko on 2009-09-07
> **Whiffle said:**
> I think the fishy parts you speak of can be found in /var/log/kern.log, could you post that up ?

Here it is: [http://servut.us/erakko/kernlog.txt](http://servut.us/erakko/kernlog.txt)

---

### Post by BlackHecilopter on 2009-09-07
SAS_sam what kind of computer are you running with what chipset?

---

### Post by SAS_Sam on 2009-09-08
BlackHelicopter, in attachement of this post, my **lshw**

---

### Post by BlackHecilopter on 2009-09-09
Hey SAS_sam

Sorry I did a little writeup on how I did mine(we have the same Intel chipset) earlier but firefox crashed and I lost everything.  So here's a quick overview of what I did since it's late.

First update your kernal:   Follow the installation guide on this page.
[http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)
You can also download the .deb files he mentions from here.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/")

Second:
Update your video driver:
Follow this guide:
[http://webupd8.blogspot.com/2009/06/new-ubuntu-intel-graphics-drivers.html](http://webupd8.blogspot.com/2009/06/new-ubuntu-intel-graphics-drivers.html)
**When he says this:  To activate UXA, use ***Option AccelMethod "UXA"*** in the ***Section "Device"*** in ***/etc/x11/xorg.conf***. **
**He really meant:** [I]Option "AccelMethod" "UXA" in the "Device" section.   (Notice the quotes around "AccelMethod")
[/I]
So make it look like this:
[http://anothersysadmin.wordpress.com/2009/05/05/ubuntu-904-and-uxa-acceleration-in-xorg/](http://anothersysadmin.wordpress.com/2009/05/05/ubuntu-904-and-uxa-acceleration-in-xorg/)
(Later)Experiment with the "Device" section here after if you like:
[http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/](http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/)

After you're done with the xorg.conf get the key for adding some repositories.
[http://webupd8.blogspot.com/2009/05/ubuntu-script-to-automatically-install.html](http://webupd8.blogspot.com/2009/05/ubuntu-script-to-automatically-install.html)

Then finish through with the rest of this page (skip over the GPG key.. To do it automatically.. blah blah part cause you did that a second ago.) If you do it the other way around you get a key error when you add repositories in "Third Party Software"
[http://webupd8.blogspot.com/2009/06/new-ubuntu-intel-graphics-drivers.html](http://webupd8.blogspot.com/2009/06/new-ubuntu-intel-graphics-drivers.html)

You'll probably have some questions cause I wrote this quick and it's really late.  Just basically follow through with what the links say and report back with any questions.  
GL!

---

### Post by SAS_Sam on 2009-09-09
Hello again,
 
I've googled this issue too, and I've been on the same sites you just gave me.
I've tried everything suggested on there, but still the same.
 
My guess is that the Chipset / GPU is just to old for the Intel drivers, and that no matter what I try it won't work without the correct drivers (which don't exist)
 
I'll just have to live with the low resolution.
 
Thanks anyway for all the time & effort you've put into this.
 
Kind Regards,
Sam

---

### Post by BlackHecilopter on 2009-09-09
Hey no problem.  That's strange though.  I don't know what it could be.  I really don't think we're trying to do the impossible here.  

One thing you might want to try is using Karmic(9.10) instead of Jaunty(9.04). It has better support for intel graphics and drivers.  (Downloads are near the bottom.)
[http://www.ubuntu.com/testing/karmic/alpha5](http://www.ubuntu.com/testing/karmic/alpha5)

If you don't mind uninstalling and reinstalling you could try that and if you're not familiar with how that works here's a good tutorial.
[http://members.iinet.net.au/~herman546/p18.html]("http://members.iinet.net.au/%7Eherman546/p18.html")

I'll keep you posted if I find anything else that might work.

Later!

Edit: You mentioned you were using a touch screen correct? I wonder if it doesn't know what monitor size you're using.  That might be an issue.

---

