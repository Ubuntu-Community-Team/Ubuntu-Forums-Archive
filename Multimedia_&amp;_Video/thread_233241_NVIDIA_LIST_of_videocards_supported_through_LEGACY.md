---
title: "NVIDIA LIST of videocards supported through LEGACY DRIVER"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by ubuntu_demon on 2006-08-09
**I'm posting this as a forum user and not as a staff member. This is all on your own risk.**

These are the video cards for which you have to try the legacy driver first (before trying the regular driver) :

> 
NVIDIA chip name 	Device PCI ID
RIVA TNT 	0x0020
RIVA TNT2/TNT2 Pro 	0x0028
RIVA TNT2 Ultra 	0x0029
Vanta/Vanta LT 	0x002C
RIVA TNT2 Model 64/Model 64 Pro 	0x002D
Aladdin TNT2 	0x00A0
GeForce 256 	0x0100
GeForce DDR 	0x0101
Quadro 	0x0103
GeForce2 GTS/GeForce2 Pro 	0x0150
GeForce2 Ti 	0x0151
GeForce2 Ultra 	0x0152
Quadro2 Pro 	0x0153
GeForce4 460 Go 0x0177
NV31M [GeForce FX Go5600] (rev a1) 0x031a


You should try the regular nvidia driver if your driver is not on this list.

The original source of this list is :
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html)

I added the "GeForce4 460 Go 0x0177" because of this post :
[http://www.ubuntuforums.org/showpost.php?p=1342493&postcount=19](http://www.ubuntuforums.org/showpost.php?p=1342493&postcount=19)

If you know of other nvidia cards for which the regular driver doesn't work but the legacy driver does work then please reply in this thread with[B] a link to the post in this thread :

Post the way you got the Nvidia driver to work
[http://www.ubuntuforums.org/showthread.php?t=221313](http://www.ubuntuforums.org/showthread.php?t=221313)[/B]

---

### Post by ubuntu_demon on 2006-08-09
**HOWTO install proprietary nvidia drivers**

**I'm posting this as a forum user and not as a staff member. This is all on your own risk.**
[B]
A note before we start :[/B]
Instead of installing *linux-restricted-modules-`uname -r`* you can also install linux-386, linux-686 or linux-k7. This will install the restricted modules as a dependency and it makes sure that they stay installed when upgrading your kernel.

If you have an intel Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV you should probably install this kernel package :
```

$sudo aptitude install linux-686

```

If you have an amd duron/athlon you should probably install this kernel package :
```

$sudo aptitude install linux-k7

```

[B]
To install the legacy (proprietary) nvidia driver :[/B]
```

$sudo aptitude install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`
$sudo nvidia-xconfig

```

Don't forget to do a reboot.

[B]
To install the regular (proprietary) nvidia driver :[/B]
```

$sudo aptitude install nvidia-glx nvidia-kernel-common linux-restricted-modules-`uname -r`
$sudo nvidia-xconfig

```

Don't forget to do a reboot.

If you have a (very) new nvidia videocard and you are experiencing problems with the nvidia-glx driver included in Dapper :
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

More information :
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

**Don't forget** to post the way you got your Nvidia videocard to work :
[http://www.ubuntuforums.org/showthread.php?t=221313](http://www.ubuntuforums.org/showthread.php?t=221313)

If you have problems you can also look in that thread whether someone else has the same videocard. He or she might already have solved your problems.

---

### Post by Orky on 2006-08-09
It is my experience that the lists of supported cards that nVidia provides for each of its driver versions, is unreliable, so don't assume it is correct, and try different versions if necessary, to find the latest driver that will still work correctly. Also, some driver versions might work partly, but not support 3D functions, on older cards.

This is gonna be fun in a few years, when they stop supporting my card in the new driver!

---

### Post by ubuntu_demon on 2006-08-09
> **Orky said:**
> It is my experience that the lists of supported cards that nVidia provides for each of its driver versions, is unreliable, so don't assume it is correct, and try different versions if necessary, to find the latest driver that will still work correctly. Also, some driver versions might work partly, but not support 3D functions, on older cards.


This list is for Dapper's nvidia-glx-legacy package.

I will try to maintain this list using :

Post the way you got the Nvidia driver to work
[http://www.ubuntuforums.org/showthread.php?t=221313](http://www.ubuntuforums.org/showthread.php?t=221313)

> **Orky said:**
> 
This is gonna be fun in a few years, when they stop supporting my card in the new driver!

When that happens I'm hoping that your (not-yet-legacy) nvidia video card will be "supported" through the nvidia-glx-legacy driver

---

### Post by dlmmsu on 2006-08-25
My thanks, I have an Nvidia Geforce 256 DDR AGP card. By installing the packages you suggested and then running "dpkg-reconfigure xserver-xorg" and selecting the higher resolutions worked for  me. By the way  it might be prudent to mention once you are in the configure xserver program (text screens) that  selections are  performed  using the space  bar (pardon my thickness) on individual screens , arrow keys to move around, tab followed by enter advances to the next screen. 

Sometimes it doesn't take a 20 Megaton weapon, just accurate information.

By the way I'm a super noob (i.e. full time Electrical Engineer, part time Windows IT admin) I've been getting grayer trying to fix this.

Once again many thanks
Dennis

---

### Post by ubuntu_demon on 2006-08-26
> **dlmmsu said:**
> My thanks, I have an Nvidia Geforce 256 DDR AGP card. By installing the packages you suggested and then running "dpkg-reconfigure xserver-xorg" and selecting the higher resolutions worked for  me. By the way  it might be prudent to mention once you are in the configure xserver program (text screens) that  selections are  performed  using the space  bar (pardon my thickness) on individual screens , arrow keys to move around, tab followed by enter advances to the next screen. 

Sometimes it doesn't take a 20 Megaton weapon, just accurate information.

By the way I'm a super noob (i.e. full time Electrical Engineer, part time Windows IT admin) I've been getting grayer trying to fix this.

Once again many thanks
Dennis
I'm glad to have been of help :)

---

### Post by muzeriter5 on 2006-09-11
You might want to add nVidia's FX Go5600 to that list. I tried over and over again to get the normal drivers working. Tried once with the legacy drivers, worked immediately. :-k

---

### Post by ubuntu_demon on 2006-09-11
Thanks for the information. 

Can you please post the results of :
$lspci -n | grep 0300
$lspci | grep VGA

thanks :)

---

### Post by muzeriter5 on 2006-09-13
Here are my results:

```
$ lspci -n | grep 0300
0000:01:00.0 0300: 10de:031a (rev a1)
$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5600] (rev a1)
```

Like I said, with the legacy driver it works fine.

---

### Post by lyrrad on 2006-09-13
OK I'll probably just be showing my ignorance, but
I've never looked at linux before, and am looking
for an alternative to Bill Gates' software.

I've installed the Ubuntu package onto my machine,
but it comes up as "Signal Over Range!!" on my (LCD)monitor.

I have an nVidia RIVA TNT2 64 graphics card so I tried
the code listed on this page to load the legacy driver,
but it comes back saying that it is not available.

How do I get the legacy drive on? Or is that even my problem?

lspci -n | grep 0300
0000:01:00.0 0300: 10de:002d (Rev 15)
lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (Rev 15)

I have since found further direction on this site concerning this problem, but
still no progress.

I downloaded the legacy driver to a CD but I keep seeing "Unable to locate any
package files. Perhaps this is not a Debian disk." Or is there a way to connect
online from the command line? 

I would really like to learn more about this OS but am getting very frustrated!
Any advice would be greatly appreciated.  Thanks

---

### Post by ubuntu_demon on 2006-09-14
> **muzeriter5 said:**
> Here are my results:

```
$ lspci -n | grep 0300
0000:01:00.0 0300: 10de:031a (rev a1)
$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5600] (rev a1)
```

Like I said, with the legacy driver it works fine.
thanks!

Maybe it's good if you also try the newest driver (both legacy and normal) :
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

---

### Post by AndrewB on 2006-09-15
0000:01:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)


Works with the regular "nvidia-glx" driver package

---

### Post by ubuntu_demon on 2006-09-16
> **AndrewB said:**
> 0000:01:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)


Works with the regular "nvidia-glx" driver package
Please tell us the result of :

$lspci -n | grep 0300

---

### Post by AndrewB on 2006-09-16
lspci -n | grep 0300
0000:01:05.0 0300: 10de:0110 (rev b2)

---

### Post by ubuntu_demon on 2006-09-16
> **AndrewB said:**
> lspci -n | grep 0300
0000:01:05.0 0300: 10de:0110 (rev b2)
Thanks for the information.

Now I'm sure your videocard wasn't listed in this list.

---

### Post by jem7v on 2006-10-29
Heya, I've got a card running on the Legacy drivers. It ran fine in Dapper and, after much agony, runs fine in Edgy:

Geforce2 MX

Also, so that I don't have to do this later, the answer to lspci -n | grep 0300 is

01:00.0 0300: 10de:0110 (rev a1)

(in case that makes a difference or helps at all)

Here's my longwinded post about how I eventually got it working:
[http://www.ubuntuforums.org/showpost.php?p=1680904&postcount=84](http://www.ubuntuforums.org/showpost.php?p=1680904&postcount=84)

---

### Post by RaZoR-x11 on 2007-01-18
Hey, just wondering here, ermm dose the i have a AMD sempron 2600+ clocks@2100mhz do i need the kernel k7? or do i need to keep the genetic i am very confussed.

---

### Post by barronmb on 2007-02-01
Here are some new goodies for ya.

nVidia GeForce 4 Ti4600.  Trying to install the latest and greatest results in it telling you to intall the 1.0-96xx (9631 is the latest of that series)... This card is NOT supported by "legacy" package or "Latest" package.  I installed that version... but can't seem to get the appropriate x.org.  I dl-ed the nVidia provided driver (9361) and installed.... it says that I am using modular XOrg and that it can't find the appropriate place to put the driver and it has to compile a new module for my kernel.... aannnnddd it can't find the appropriate place to put the libs... so it simply installs puts the libs and such in generic places... and tells me to install the dev package.
Also... I can not get 3D support by installing either legacy glx or nvidia-glx.  I am not on my Ubuntu box at home (at work now) so I can't give you any outputs... but if you know of a repository with the proper restricted packages for me.... please post up :).  

Fun times!

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-02-19
> **barronmb said:**
> Here are some new goodies for ya.

nVidia GeForce 4 Ti4600.  Trying to install the latest and greatest results in it telling you to intall the 1.0-96xx (9631 is the latest of that series)... This card is NOT supported by "legacy" package or "Latest" package.  I installed that version... but can't seem to get the appropriate x.org.  I dl-ed the nVidia provided driver (9361) and installed.... it says that I am using modular XOrg and that it can't find the appropriate place to put the driver and it has to compile a new module for my kernel.... aannnnddd it can't find the appropriate place to put the libs... so it simply installs puts the libs and such in generic places... and tells me to install the dev package.
Also... I can not get 3D support by installing either legacy glx or nvidia-glx.  I am not on my Ubuntu box at home (at work now) so I can't give you any outputs... but if you know of a repository with the proper restricted packages for me.... please post up :).  

Fun times!

Hi barronmb -- Curious really? Were you able to make any sort of progress on this challenge.  I have a friend at work who brought in his spare PC that wants Linux installed on it. The machine itself is a AMD 2100+ w/ a GeForce Ti4200 GPU. I am experiencing the exact same problem as you mentioned in your above post. Honestly, I've never had this much difficulty with Ubuntu...ever. This same problem has been dragging on for almost two days now -- Let me know if you were ever able to determine a fix. 

Many thanks in advance,

Regards,

---

### Post by tseliot on 2007-02-19
> **k|d<FuNkY>FrY said:**
> Hi barronmb -- Curious really? Were you able to make any sort of progress on this challenge.  I have a friend at work who brought in his spare PC that wants Linux installed on it. The machine itself is a AMD 2100+ w/ a GeForce Ti4200 GPU. I am experiencing the exact same problem as you mentioned in your above post. Honestly, I've never had this much difficulty with Ubuntu...ever. This same problem has been dragging on for almost two days now -- Let me know if you were ever able to determine a fix. 

Many thanks in advance,

Regards,

Try Envy (follow the instructions):
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by plb on 2007-02-19
> **tseliot said:**
> Try Envy (follow the instructions):
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I tried your app. I end up with a blank screen after installation. Not saying it's your fault, I installed via nvidia site and got the same thing. TNT2 card.

---

### Post by tseliot on 2007-02-19
> **plb said:**
> I tried your app. I end up with a blank screen after installation. Not saying it's your fault, I installed via nvidia site and got the same thing. TNT2 card.

Try point 4 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by plb on 2007-02-22
> **tseliot said:**
> Try point 4 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

I'll give it a try but just to let you know there was no mouse cursor. It's a completely blank screen right when X starts up and the only way around it is a hard reboot.

EDIT: Thanks that worked, although I didn't need the last bit with GLX.

---

### Post by MarioMidget on 2007-02-25
i am new to ubuntu and i don't know how to go about installing drivers very well. but i did install the generic nvidia driver for my nvidia GeForce Go 6150 and it is giving me 32bit color, but it isn't giving me the proper screen resolution. i have a 14" wide screen monitor and it is only giving me 1024x768 resolution when i i know when i ran windows xp i could get a better resolution. is there any way i can install more resolutions and/or refresh rates? everything looks stretched. sorry for being long winded and sorry for posting in the wrong place if i did.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-02-25
If your vid card supports the widescreen resolution(s), you should be able to simply edit your xorg.conf file. (e.g. sudo nano /etc/X11/xorg.conf) - Manually input your widescreen resolutions under the 'Screen' Section. Backup your original first! 

I had to do this in order to run 1680x1050... Hope this helps!

---

### Post by MarioMidget on 2007-02-27
thankyou! it helped a lot :)

---

### Post by Masterj15 on 2007-03-02
Ummmmmmm I need some help install the legacy drivery because of the fact that when I  tried to install  the driver it said that I need linux-image-2.6.18-3-486 but I could not find it on the internet so I downloaded and installed linux-image-2.6.18-4-486 and it did not do the trick. Could some one give me a link to download linux-image-2.6.18-3-486.

---

### Post by Snookered on 2007-03-17
Installed an Nvidia PWA-G4000PRO on a Compaq mobo w/PIII 800MHz, 512 ram and it works good after installing Kubuntu 6.10. Yes, it is very old. Once updated and multimedia gets installed it will be my first comp to give away!

---

### Post by romcio on 2007-03-21
Hi, Alberto, Thanks for your work and envy!!!

I've just installed and configured my GEFORCE4 MX 440 with 7184 drivers on Edgy.
I think it's very importent for all guys who have that card.

9136 doesn't work. Nothing else work. Only 7184. I've tried everything for 2 weeks:)

romcio

---

### Post by Bachstelze on 2007-04-07
**UPDATE NEEDED FOR FEISTY :**

Feisty uses the 9755 driver, which dropped support for another bunch of old GPUs, listed here : 

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

If your card is listed as "supported by 96xx driver", you can get it from the URL at the bottom of this post *or* use Ubuntu's *nvidia-glx-legacy* packages (note that they will give you a 71xx driver, which might or might not result in a performance loss since it's significantly older).

If your card is listed as "supported by 71xx driver", you can get it from the URL at the bottom of this post *or* use Ubuntu's *nvidia-glx-legacy* packages. It will give you the very same version of the driver so just use the method you find the most convenient (using Ubuntu packages is usually recommended for beginners).

Older nvidia installers can be downloaded from [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

---

### Post by Vivian on 2007-04-10
Hey, mi name is vivian im just wondering is this something to do about computer or something thanks!

---

### Post by slayerboy on 2007-04-10
> **Vivian said:**
> Hey, mi name is vivian im just wondering is this something to do about computer or something thanks!

Hiya Vivian!):P

First, welcome to Ubuntu Linux and the Ubuntu Forums!

This topic is about a specific type of card (or device) in your computer that your monitor attaches to in order to display video from your computer.  Without one of these devices, you will not a lot done with a computer other than maybe listen to the noises it makes.

There are three main video cards around right now.  This particular topic is about NVidia cards that are no longer supported by NVidia.  There are other cards made by ATI and also there are cards that are integrated (included with the motherboard inside your computer) made by Intel and a variety of other manufacturers.

I would recommend taking a look at the "Absolute Beginner Talk" area of the forum ( [http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73) ).  If you have any questions, feel free to ask.:KS

---

### Post by slayerboy on 2007-04-10
> **HymnToLife said:**
> **UPDATE NEEDED FOR FEISTY :**

Feisty uses the 9755 driver, which dropped support for another bunch of old GPUs, listed here : 

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

If your card is listed as "supported by 96xx driver", you can get it from the URL at the bottom of this post *or* use Ubuntu's *nvidia-glx-legacy* packages (note that they will give you a 71xx driver, which might or might not result in a performance loss since it's significantly older).

If your card is listed as "supported by 71xx driver", you can get it from the URL at the bottom of this post *or* use Ubuntu's *nvidia-glx-legacy* packages. It will give you the very same version of the driver so just use the method you find the most convenient (using Ubuntu packages is usually recommended for beginners).

Older nvidia installers can be downloaded from [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

I second this!

I have an NVidia Geforce4 MX4000 and the nvidia-glx package, the 97xx driver) made X unusable.  nvidia-glx-legacy made it a little better, but that driver is fairly old, as it is the 71xx driver.  I had to manually install the 96xx driver to get my video card working pretty much perfectly, not to mention get Beryl running.

Why haven't the 96xx drivers been included for Fiesty?  It was my understanding that the 96xx drivers cover most, if not all, the cards covered by the 71xx driver.  IMHO it would solve quite a few issues for users with "legacy" hardware better.

---

### Post by Bachstelze on 2007-04-11
Read the list I posted, some veeeeeeery old cards are supported only bythe 71xx drivers. I guess it's too late for Feisty but maybe we should do something about getting the 96xx packaged for Feisty+1 ?

---

### Post by klabak on 2007-06-06
Hi guys. I'm brand new to ubuntu linux (4 days using?) and it's been great so far but I'm having resolution problems. I have a RIVA TNT 2 card on an old P3 (yeah I know but I felt like making a linux box on this old system at work). While installing Ubuntu I had a resolution of 1280X1024 (my system defaulted to this) up until I installed the legacy drivers for my card. I have a viewsonic 19" (max res 1280X1024) and I know this card supports this resolution. After installing the legacy drivers and enabling them, I only have 1024x768, 800x600 and 640x480. I checked my xorg.config file and it has all the appropriate resolutions that I want under the "screen" section. Even if I try disabling the legacy drivers the default ubuntu drivers don't pick up the higher resolutions anymore. I've been all over the net trying to find an answer to this. Is there anything else I can do or do I have to look at large text??? *gasp* Thanks.

---

