---
title: "ATI 8.28.8 help pls"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by Dropknee on 2006-08-18
I recently try to update my driver with [this]("http://www.ubuntuforums.org/showthread.php?t=204910") how-to, but when I try to recompile the kernel module with ```
sudo module-assistant build,install fglrx 
``` 

 I got this 
```
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Target package file 
/usr/src/fglrx-kernel-2.6.15-26-386_8.28.8-1+2.6.15-26.46_i386.deb already 
exists, not rebuilding!
Version 8.28.8-1+2.6.15-26.46 of fglrx-kernel-2.6.15-26-386 already installed, skipping.

```

and when I try to execute 
```
 sudo aticonfig --initial 
Found fglrx primary device section
Nothing to do, terminating.

```

I do all step by step but when I reboot and do the fglrxinfo got this
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

 Like I wirte before im trying to upgrade my driver from 8.27.10

can anyone can help me here??pls!! any method to uninstall completely the old driver???? thx

---

### Post by catlett on 2006-08-18
```
sudo rm /usr/src/fglrx-kernel*.deb
```

---

### Post by Dropknee on 2006-08-19
> **catlett said:**
> ```
sudo rm /usr/src/fglrx-kernel*.deb
```

This dont work, Im still getting this

```
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Target package file 
/usr/src/fglrx-kernel-2.6.15-26-386_8.28.8-1+2.6.15-26.46_i386.deb already 
exists, not rebuilding!
Version 8.28.8-1+2.6.15-26.46 of fglrx-kernel-2.6.15-26-386 already installed, skipping.
```

---

### Post by catlett on 2006-08-19
Try going in Synaptic Package Manager. (System<Administration<Synaptic Package Manager) Search for the fglrx-kernel. It should be there. If it is, righ5t-click and select "mark for removal" when the option menu appears. Then hit appply.

---

### Post by Dropknee on 2006-08-19
Synaptic is broken now :( I get this when I try to run from terminal

synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory

I think I mess something, but the only I do is try to install latest driver.

 I dont want to re-install all the system because of this :(

---

### Post by bouvittel on 2006-08-19
Hi

for Synaptic thing do
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
is posted somewhere in the forum.

fglrx driver issue i can't help

---

### Post by Dropknee on 2006-08-19
> **bouvittel said:**
> Hi

for Synaptic thing do
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
is posted somewhere in the forum.

fglrx driver issue i can't help

Thx with the Synaptic issue, this work great. I really cant undestand why this happen to synaptic, but im glad is resolved, thx once again for help

---

### Post by catlett on 2006-08-19
I install the ati driver with fitzman's how to. [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)  You won't be able to cut and paste the commands because you are installing a newer version. The name of the file/driver will be different.

---

### Post by Dropknee on 2006-08-19
> **catlett said:**
> I install the ati driver with fitzman's how to. [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)  You won't be able to cut and paste the commands because you are installing a newer version. The name of the file/driver will be different.


Im not copy-paste with the command with old version, I remplace for example 

```
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
```

with 

```
chmod +x ati-driver-installer-8.28.8.run
./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
```

so is suppose to work that way...... I guess....

---

### Post by catlett on 2006-08-19
Yes. That should be all you have to do.
 Whatever the file's name is that you downloaded, use that instead of 8.26.18-x86. The only thing you should have to change is the version number. Everything else will be copy/paste.

---

### Post by Dropknee on 2006-08-19
Everything goes ok until this

```
sudo aticonfig --initial 
Found fglrx primary device section
Nothing to do, terminating.

```

---

### Post by Dropknee on 2006-08-19
maybe need to reconfig the xorg to make sudo aticonfig --initial to work but im not sure of it

---

### Post by catlett on 2006-08-19
check to see if it installed```
 fglrxinfo
```That will givew an output like this
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series Generic
OpenGL version string: 2.0.5879 (8.26.18)
```
It may have installed and the message you got just meant that the part of xorg.conf with the primary device was already created with the proper info.

---

### Post by Dropknee on 2006-08-19
```
fglrxinfo
```

this is the output

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

---

### Post by Dropknee on 2006-08-19
Dont know why this happen the old driver work, this happen when I try to update the drivers.

---

### Post by catlett on 2006-08-19
You're loosing the driver somehow. What method did you use to install the old version? 
In the thread with the how to, there is a bunch of people with this issue but I haven't seen any replies with a solution.

You migth want to try it like this but I don't think it will give you the latest driver. Jusr make sure you have "restricted" repository enabled in your sources list.



```
sudo apt-get update
```
```
sudo apt-get install linux-restricted-modules-$(uname -r)
```
 #Okay if it is already installed
```
sudo apt-get install xorg-driver-fglrx
```
```
sudo depmod -a
```
```
sudo aticonfig --initial
```
```
sudo aticonfig --overlay-type=Xv
```


This is how I use to install the ATI driver before I found fitzman's how to. It is from the Dapper Guide [http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29](http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29)

---

### Post by moosepic on 2006-08-19
Hi Guys and Gals,

Just trying to figure out what's going on with my ATi setup. 

I just switched to 6.06 on one of my machines (my mythtv machine).   I have an ATi radeon 9600.   As far as I can tell, my ATi set-up worked, BUT went I run TV-out, it works fine until I want to use mplayer or mythtv on my TV.  For some reason all I get is a blue screen on my TV, but it works fine on my CRT monitor.

Any ideas?   Losing my mind here.   Please, don't make me by an Nvidia card!

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by NemesisUK on 2006-08-19
I had a problem with the 8.28.8 version magic errors, which is strange as the 8.27.10 work fine. To get around the errors I put fglrx --force-vermagic in /etc/modules and everything now works. Why would the 8.28.8's be using gcc-3.4 over gcc-4.0?

---

### Post by Dropknee on 2006-08-20
Cant get the aticonfig --initial to work always get this

Found fglrx primary device section
Nothing to do, terminating.

---

### Post by whatever on 2006-08-20
> **Dropknee said:**
> Cant get the aticonfig --initial to work always get this

Found fglrx primary device section
Nothing to do, terminating.
where's the proplem?
the --initial command updates the xorg.conf file for the use of fglrx. in your case there is "Nothing to do" as you obviously already have modified your xorg.conf to work with fglrx.

---

### Post by Dropknee on 2006-08-20
> **whatever said:**
> where's the proplem?
the --initial command updates the xorg.conf file for the use of fglrx. in your case there is "Nothing to do" as you obviously already have modified your xorg.conf to work with fglrx.

But... I guess.. you need to do the aticonfig --initial to refresh the xorg to make it work with the new driver, lets suppose than I dont need to do the command, but when I finish and reboot, I still getting this

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by whatever on 2006-08-20
> **Dropknee said:**
> But... I guess.. you need to do the aticonfig --initial to refresh the xorg to make it work with the new driver
no
> **Dropknee said:**
> lets suppose than I dont need to do the command, but when I finish and reboot, I still getting this

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
i guess there's a problem with the kernel module.
what's the output of "**dmesg | grep fglrx**" ?

the content of /var/log/Xorg.0.log might be usefull, too.

---

### Post by Dropknee on 2006-08-20
This is the output I get from "dmesg | grep fglrx" command

```
[17179595.328000] fglrx: version magic '2.6.15-26-386 preempt 486 gcc-3.4' should be '2.6.15-26-386 preempt 486 gcc-4.0'
[17179605.672000] fglrx: version magic '2.6.15-26-386 preempt 486 gcc-3.4' should be '2.6.15-26-386 preempt 486 gcc-4.0'
[17179607.396000] fglrx: version magic '2.6.15-26-386 preempt 486 gcc-3.4' should be '2.6.15-26-386 preempt 486 gcc-4.0'

```

---

### Post by whatever on 2006-08-20
remove gcc-3.4, delete /usr/src/fglrx-kernel*.deb and rebuild the module.

---

### Post by lazyd2 on 2006-08-20
Been having problems too installing the latest driver. Everything is working fine with the driver in the repos(8.25.x) inluding xgl/compiz.

With 8.28.8 everything compiles ok but when I reboot I get "mesa"
(ATI X600)

---

### Post by lazyd2 on 2006-08-20
...

---

### Post by gmc on 2006-08-20
Me too, and I've not had any problems with previous releases. Frustrating!

```

dmesg | grep fglrx
[17179585.608000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179585.612000] [fglrx] Maximum main memory to use for locked dma buffers: 1896 MBytes.
[17179585.612000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179594.200000] [fglrx] total      GART = 134217728
[17179594.200000] [fglrx] free       GART = 118226944
[17179594.200000] [fglrx] max single GART = 118226944
[17179594.200000] [fglrx] total      LFB  = 127889408
[17179594.200000] [fglrx] free       LFB  = 119697408
[17179594.200000] [fglrx] max single LFB  = 119697408
[17179594.200000] [fglrx] total      Inv  = 0
[17179594.200000] [fglrx] free       Inv  = 0
[17179594.200000] [fglrx] max single Inv  = 0
[17179594.204000] [fglrx] total      TIM  = 0

```

```

fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.2 (1.5 Mesa 6.4.1))

```

G.

---

### Post by Dropknee on 2006-08-20
This happen when I try to rebuild the module

[[IMG]http://img340.imageshack.us/img340/8123/screenshotdropkneeubuntu1nh8.th.png[/IMG]](http://img340.imageshack.us/my.php?image=screenshotdropkneeubuntu1nh8.png)

This happen when I remove the 3.4-gcc

---

### Post by Dropknee on 2006-08-20
Ok problem solved at last. This is what I do

I uninstall via synaptic gcc-4.0 and all dependencies and seach for fglrx and uninstall all packege with the version 8.28.8 and this was

fglrx-control
fglrx-kernel
fglrx-kernel-source
xorg-driver-fglrx

then start follow the [fitzman49 tutorial]("http://www.ubuntuforums.org/showthread.php?t=204910") from scratch and when I reboot and do this command in terminal
```
fglrxinfo
```
for my surprise I receive this output
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.6011 (8.28.8)

```
and all is working again :D 

I hope this help someone with the same issue

---

### Post by taiye on 2006-08-21
I spent all day yesterday trying to get the ati driver 8.28.8 to work. It drove me round the bend!! Then I read Dropknee's post, followed the instructions and now.....works like a dream.Thanks a lot for the info. Only slight problem is some screen flicking on logging out. I've got Ubuntu 6.06 set up on a Compaq M2512AU (Presario M2000) with the dreaded Radeon Xpress 200M (RS480) card.

---

### Post by Hadron Quark on 2006-08-23
Are you sure you didnt do anything else?

I followed the instructions to the letter, but still indirect rendering for my x800 with dapper.

2.6.15-26 kernel.

Interestingly the 
sudo module-assistant prepare,update 

line reinstalls gcc 4.0

I'm back to getting this from dmesg | grep -i fglrx:

[17179607.172000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179607.176000] [fglrx] Maximum main memory to use for locked dma buffers: 1170 MBytes.
[17179607.176000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179610.900000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[17179610.900000] [fglrx:firegl_unlock] *ERROR* Process 4822 using kernel context 0

---

### Post by Dropknee on 2006-08-23
just remove the package I mention in my post, and do the tutorial step by step from the beginning. Thats is what I do and work for me. Is you remove the gcc-4.0 and all the dependencies do this command

```
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```

you reinstall the gcc and all the dependencies back.

Try that and lets us know

---

### Post by Hadron Quark on 2006-08-24
Only gcc-4.0 or gcc-4.0 base too?

Whats th epoint of uninstalling it if it just reinstalls again at the next step?

Could you explain the steps?

---

### Post by Hadron Quark on 2006-08-24
Could you list your relevant details from 

1) sudo lsmod | grep -i fglrx
2) cat /etc/modules
3) sudo lspci | grep -i agp
4) sudo lsmod | grep -i agp

thanks for your help.

---

### Post by Hadron Quark on 2006-08-24
More info : if I

cat /var/log/Xorg.0.log | grep -i fglrx

I get:


(II) fglrx(0): UMM Bus area:     0xd8701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xd0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

---

### Post by taiye on 2006-08-24
The only thing I did not do was to run sudo aticonfig --initial.I manually edited the xorg.conf file by changing device "vesa" to "fglrx". Then rebooted. I'm not sure whether that would make a difference.

---

### Post by Dropknee on 2006-08-24
> **Hadron Quark said:**
> Only gcc-4.0 or gcc-4.0 base too?

Whats th epoint of uninstalling it if it just reinstalls again at the next step?

Could you explain the steps?

Just remove the gcc-4.0

---

### Post by Hadron Quark on 2006-08-27
I did. But then it just installs again with the update. Could you posts the ocntents of the files I asked for please?

---

### Post by toasted on 2006-08-27
I too have this trouble so am waiting to see what occurs next!!

---

### Post by toasted on 2006-08-27
> **Dropknee said:**
> Ok problem solved at last. This is what I do

I uninstall via synaptic gcc-4.0 and all dependencies and seach for fglrx and uninstall all packege with the version 8.28.8 and this was

fglrx-control
fglrx-kernel
fglrx-kernel-source
xorg-driver-fglrx

How do you determine all dependencies and uninstall them?
I have a gcc-4.0-base too right next to it

---

### Post by dude051 on 2006-08-27
> How do you determine all dependencies and uninstall them?
I have a gcc-4.0-base too right next to it

If you uninstall via synaptic, a window listing the dependencies that will uninstall along with it will pop up.

I havent tried this yet, but I am interested if anyone got this to work on an XGL/Compiz system. I am having problems running XGL as a server, instead as a session (which im running now). Where XGL will only run on Mesa drivers, and refuse fglrx 2.28, giving the above problems. I might try it in a bit after I research some more.

---

### Post by toasted on 2006-08-27
ok so just select gcc-4.0 in Synaptic
Then choose remove or complete removal?
I never was sure about the difference

---

### Post by dude051 on 2006-08-27
Yes, choose gcc-4.0, I forgot to say, but gcc-4.0 is the GCC Compiler itself where as gcc-4.0-base is langugage and common files for the compiler.

As for the difference between removal and complete removal, the help pages say this:

> Debian only: To remove all files related to the package
				choose Mark for
				Complete Removal instead of 
				Mark for Removal.

Removal though only removes the package, and packages that depend on it. Obviously, because if you remove that package the others will be come "broke". If there is a difference between that.. im not sure heh.
Hope that helps.

---

### Post by toasted on 2006-08-27
Say we are talking about application x
If we choose to completely remove application x and there are some dependent packages they will be removed as well... thats clear

What if some of those dependent packages are also depended by application Z, will they still be removed, will it throw a flag, or just not remove them?

I have done both ways... remove and completely remove and really havent seen a difference or had a problem either way

Just curious ya see  :D

---

### Post by dude051 on 2006-08-28
I havent seen a difference either, so its hard to say. I would guess would be like...
-Remove a media player package
-Media player core and GUI are removed as dependants but the codecs it uses are left, because they arent broke, but are just there.

- Complete removal would remove all associations with it, media player core, GUI and codecs ect.

Just my guess... I dunno though :(

---

### Post by toasted on 2006-08-28
> **Dropknee said:**
> Ok problem solved at last. This is what I do

I uninstall via synaptic gcc-4.0 and all dependencies and seach for fglrx and uninstall all packege with the version 8.28.8 and this was

fglrx-control
fglrx-kernel
fglrx-kernel-source
xorg-driver-fglrx

then start follow the [fitzman49 tutorial]("http://www.ubuntuforums.org/showthread.php?t=204910") from scratch and when I reboot and do this command in terminal
```
fglrxinfo
```
for my surprise I receive this output
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.6011 (8.28.8)

```
and all is working again :D 

I hope this help someone with the same issue

Glad you had success. Have you noticed any improvements using the new drivers? What advantage is there to updating??

---

### Post by Hadron Quark on 2006-08-28
It gives HW openGL : its what this entire thread is about.:-$ 

Still no one has answered *WHY* to remove gcc-4.0 when the update and install just reinstalls it as the next step.:-s 

Unfortunately, *still* noone who has it working has posted their relevant files :( It means we can only guess at to what is making it work for them.

One thing is for sure : the dropknee walkthrough does not work on my machine with an AQG x800pro and dapper 6.06 with a  2-6-15-26 kernel.:confused:

---

### Post by dude051 on 2006-08-28
I dont see why to remove gcc4 either.. seeing as how the guide clearly makes you apt-get gcc3.3, not 4... so your guess is as good as mine.

As for the improvement, its not just hardware OpenGL, that was supported in earlier drivers, but it's just better support for them and if I remember the new drivers include a clock limiter to reduce heat. Something I like because I have a laptop, and reducing heat is always welcome.

Release notes for the latest ATI drivers can be seen at:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8.html")

---

### Post by toasted on 2006-08-28
I'm just going to wait since mine works ok with the older drivers. I might try the suggestion here but not right now. I bet ATI has another release soon .

---

### Post by whatever on 2006-08-28
> **dude051 said:**
> I dont see why to remove gcc4 either.. seeing as how the guide clearly makes you apt-get gcc3.3, not 4... so your guess is as good as mine.[/URL]
gcc4 is a dependency of the "build-essential" package, so you don't have to apt-get it explizitly. installing "build-essential" ensures you got gcc4 installed.
the "gcc-3.3-base" package is _only_ needed, because it is a dependency of libstdc++5, _not_ for compiling the kernel module.

---

### Post by dude051 on 2006-08-28
My mistake, I did not the the -base suffix.

---

### Post by toasted on 2006-08-28
> **whatever said:**
> gcc4 is a dependency of the "build-essential" package, so you don't have to apt-get it explizitly. installing "build-essential" ensures you got gcc4 installed.
the "gcc-3.3-base" package is _only_ needed, because it is a dependency of libstdc++5, _not_ for compiling the kernel module.

So by removing gcc-4.0 we can no longer compile anything? 
If this works to get the driver working can we reinstall gcc-4.0 and still have the driver work?

---

### Post by dude051 on 2006-08-28
> **toasted said:**
> So by removing gcc-4.0 we can no longer compile anything? 
If this works to get the driver working can we reinstall gcc-4.0 and still have the driver work?

Right, and I dont see why you cant reinstall it. I haven't tried this yet so I can not say if it truely interfiers with it.

---

### Post by toasted on 2006-08-31
Is this working for anyone else?

---

### Post by Dropknee on 2006-09-01
I want to be more clear about this. This happen when I remove the GCC 4.0

[[IMG]http://img101.imageshack.us/img101/1155/screenshotsynapticpackagemanagerdr2.th.png[/IMG]](http://img101.imageshack.us/my.php?image=screenshotsynapticpackagemanagerdr2.png)
and this is what popup when I try to remove it

[[IMG]http://img97.imageshack.us/img97/1153/screenshotsynaptichb8.th.png[/IMG]](http://img97.imageshack.us/my.php?image=screenshotsynaptichb8.png)

This are the dependencies, I just remove it and when you do this

```
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```

you reinstall all back, just remove it and do the tutorial from the very beginning, this work for me but maybe not for you, dont blame me for that, I just trying to help

---

### Post by moonglow on 2006-09-18
For those of sis-based motherboard users who have tried everything and still have mesa drivers loading instead of fglrx try this:

1. Fresh install

2.Use Easy Ubuntu to install the fglrx drivers

3.make sure you have "fglrx" and not "ati" in the [DRIVERS] section of your /etc/X11/xorg.conf

4.type:

sudo gedit /etc/modprobe.d/blacklist

in a terminal window

5. add:

blacklist sis_agp

to the bottom of the file and save

6.Reboot

This was the ONLY way I got 3d to work on my ASROCK K7S41GX mobo

---

### Post by toasted on 2006-09-18
As a sidenote, I got the 8.28 drivers working with Edgy with no trouble at all using this:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)
I also had to reconfigure X server and run fire gl control panel as root to get dual screens..... normal stuff but worked with Edgy where it never has with Dapper!

---

