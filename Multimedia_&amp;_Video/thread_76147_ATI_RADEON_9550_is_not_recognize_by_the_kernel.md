---
title: "ATI RADEON 9550 is not recognize by the kernel"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by ilans on 2005-10-14
After a lot of experiments (includ the "how-to" manual) I finally found the
reason that prevent 3D  accelereation on my pc.
My card (ATI Radeon 9550) is not recognize by Ubuntu kernel

lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173

I run:
lsmod | grep fglrx
and  see that the module is not use by enyone (used by colomn = 0)

when I run:
fglrxinfo 
I get:
vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1) 

Important information:
I upgrage my ubuntu hoary to breezy
In hoary there was excellent 3D acceleration.

---

### Post by SilverTab on 2005-10-14
a little bump for you, since im in the exact same situation, and some more info:

here's the result from dmesg | grep fglrx
```

[4294755.314000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294755.319000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294755.320000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294755.334000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4294755.335000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294755.335000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294755.335000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294755.335000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[4294755.335000] [fglrx:firegl_unlock] *ERROR* Process 8845 using kernel context 0

```

and the result from cat /proc/mtrr:
reg00: base=0x00000000 ( 0MB), size=984064MB: write-back, count=1


(from what I know you get approx. the same result as me right ilans??)

---

### Post by ilans on 2005-10-15
I made another test:
I launch Ubuntu Hoary Live CD and run lspci
the result was exactly the same (unknown ATI device 4173 ... 4153) as in my
breezy installation. 

In my previous hoary there wasn't any 3D problem and the kernel was different for sure.
This fact change my idea that the problem is a  pure kernel problem.


.

---

### Post by ilans on 2005-10-15
I added a bug in bugzilla

[https://bugzilla.ubuntu.com/show_bug.cgi?id=17823](https://bugzilla.ubuntu.com/show_bug.cgi?id=17823)

---

### Post by SilverTab on 2005-10-15
[QUOTE=ilans]I added a bug in bugzilla

[https://bugzilla.ubuntu.com/show_bug.cgi?id=17823](https://bugzilla.ubuntu.com/show_bug.cgi?id=17823)[/QUOTE]


cool... I was about to do it considering the lack of success from my rage3d post...(but their forum is moving a bit slower than ubuntu forum so we never know!)

---

### Post by johanPO on 2005-10-15
Hi,

Had the same problem, but I now got it up and running. I must say that I dont know exactly what made it work at the end as I have spent several hours to solve this one.

Below a description of what I think made it work for me.
[http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

then sudo dpkg-reconfigure xserver-xorg  and not the fglrxconfig
then I replaced the ati with fglrx in xorg.conf  giving Driver          "fglrx"

now I get from fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)

---

### Post by ilans on 2005-10-15
[QUOTE=johanPO]Hi,

Below a description of what I think made it work for me.
[http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

then sudo dpkg-reconfigure xserver-xorg  and not the fglrxconfig
then is replaced the ati with fglrx in xorg.conf  giving Driver          "fglrx"

now I get from fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)[/QUOTE]

Thank you
How did you manage to download the new ati_installer (~58mb) from ATI site?
My firefox freeze when I am tring to download it !

---

### Post by johanPO on 2005-10-15
Hi,

I used Konqueror as my firefox was opening the file instead of saving it. 
Another thing that I have to look into, that seems to have changed with the upgrade from 5.04.....

So far Krusader, Azeureus and Kaffeine needs to be repaired.

---

### Post by ilans on 2005-10-15
[QUOTE=johanPO]Hi,

I used Konqueror as my firefox was opening the file instead of saving it. 
Another thing that I have to look into, that seems to have changed with the upgrade from 5.04.....

So far Krusader, Azeureus and Kaffeine needs to be repaired.[/QUOTE]

Thank you, I manage to download it !
But... I have few questions :( 
1. what are the steps that you made in order to install it ?
    did you run ati-driver-installer-8.18.6-i386.run without any preparation ?
        (I did it but I get errors).
    How did you apply the patch ? 
    Do I have to remove the previous fglrx packages ?
2. did you use a special guide in order to install the new driver ?

---

### Post by johanPO on 2005-10-15
You find the information at the bottom of page [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

How to apply the patch and generate the packages:
[I]
1) extract the ati-installer files: sh ati-driver-installer-8.18.6-i386.run
--extract
   (or the 64bit version if that is what you are using).
2) apply the patch: patch -p0 < /path/to/this/ubuntu.patch
3) change into the installer directory: cd fglrx-install
4) build the packages: ./ati-installer 8.18.6 --buildpkg Ubuntu/breezy
   (or Ubuntu/hoary or Ubuntu/warty)
5) remove the installer files: cd .. ; rm -rf fglrx-install

The 5 .deb packages should now be generated and contained in the current
directory.

After installing all the packages, don't forget to untar the
/usr/src/fglrx.tar.bz2 and generate the kernel module for your current kernel
as this is not done automatically.  I recommend module-assistant which will
build and install the kernel module when run as: module-assistant a-i fglrx[/I]

---

### Post by Golgoth on 2005-10-15
[http://ubuntuforums.org/showthread.php?t=76116](http://ubuntuforums.org/showthread.php?t=76116)

---

### Post by SilverTab on 2005-10-15
[QUOTE=ilans]Thank you, I manage to download it !
But... I have few questions :( 
1. what are the steps that you made in order to install it ?
    did you run ati-driver-installer-8.18.6-i386.run without any preparation ?
        (I did it but I get errors).
    How did you apply the patch ? 
    Do I have to remove the previous fglrx packages ?
2. did you use a special guide in order to install the new driver ?[/QUOTE]


were you able to download it without konqueror???

I know I was able to do it a couple of days ago but can't remember what I used....

---

### Post by ilans on 2005-10-15
[QUOTE=SilverTab]were you able to download it without konqueror???

I know I was able to do it a couple of days ago but can't remember what I used....[/QUOTE]

I booted to win2000 and used IE6

But I have still a problem. So far I did...

1. sudo apt-get remove xorg-driver-fglrx
    sudo apt-get remove fglrx-control
    sudo apt-get remove linux-restricted-modules-$(uname -r)
   Than I rebooted (before change correctly xorg.conf in order to launce to gnome)

2. I generate and install the 5 new patched debs files :
    fglrx-control_8.18.6-1_i386.deb
    fglrx-kernel-source_8.18.6-1_i386.deb
    fglrx-sources_8.18.6-1_i386.deb
    xorg-driver-fglrx_8.18.6-1_i386.deb
    xorg-driver-fglrx-dev_8.18.6-1_i386.deb

3.  I untar /usr/src/fglrx.tar.bz2

4. I have a problem in the folowing step:
  "generate the kernel module for your current kernel"

I hope that I'll manage to solve my ATI driver problem, and then
I will be happy to help in writing a new updated how-to - based on my experience

---

### Post by johanPO on 2005-10-15
Hi,

I am far from an expert in this, but what happens if you do 

sudo dpkg --install on your deb files?

---

### Post by ilans on 2005-10-15
[QUOTE=johanPO]Hi,

I am far from an expert in this, but what happens if you do 

sudo dpkg --install on your deb files?[/QUOTE]

I already installed successfully all 5 pached debs file,
and I untar the file /usr/src/fglrx.tar.bz2

but now I am stuck in this step: 
"generate the kernel module for your current kernel"

I tried both:
1. sudo module-assistant a-i fglrx
    (I installed module-assistant and linux-header)

I get this message:
/usr/bin/make -C /usr/src/linux-headers-2.6.12-9-386
 SUBDIRS=/usr/src/modules/fglrx modules                                     
 /usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11:
 gcc-3.4: command not found                                                
 /usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12:
 gcc-3.4: command not found                                               
 make[1]: gcc-3.4: Command not found  

2. sudo sh make.sh

I get this message:
   ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make.sh: line 843: cd: 2.6.x: No such file or directory
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found



BUY WHY I HAVE GOT ERROR ON GCC 3.4 IF I USE GCC 4.0 ???

---

### Post by mlomker on 2005-10-15
> BUY WHY I HAVE GOT ERROR ON GCC 3.4 IF I USE GCC 4.0 ???

Another lovely Breezy 'feature'.  The kernel is compiled with 3.4 but the default compiler is 4.0.

Take look at [this how-to]("http://ubuntuforums.org/showthread.php?p=411503") and note the build-dep lines and the export command for CC.

---

### Post by Téragone on 2005-10-15
[QUOTE=ilans]I already installed successfully all 5 pached debs file,
and I untar the file /usr/src/fglrx.tar.bz2

but now I am stuck in this step: 
"generate the kernel module for your current kernel"

I tried both:
1. sudo module-assistant a-i fglrx
    (I installed module-assistant and linux-header)

I get this message:
/usr/bin/make -C /usr/src/linux-headers-2.6.12-9-386

 SUBDIRS=/usr/src/modules/fglrx modules                                     
 /usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11:
 gcc-3.4: command not found                                                
 /usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12:
 gcc-3.4: command not found                                               
 make[1]: gcc-3.4: Command not found  

2. sudo sh make.sh

I get this message:
   ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make.sh: line 843: cd: 2.6.x: No such file or directory
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found



BUY WHY I HAVE GOT ERROR ON GCC 3.4 IF I USE GCC 4.0 ???[/QUOTE]


And you will have to apply this patch:

[http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)


I tried it but no success. The driver is not working.

I tried also the 8.16.20 driver, same thing.

It seems that we need a new kernel base on that :

[https://bugzilla.ubuntu.com/show_bug.cgi?id=17614](https://bugzilla.ubuntu.com/show_bug.cgi?id=17614)

---

### Post by mincho on 2005-10-15
ya but i need an installation method please post here the method which help me in installing driver on ubuntu linux.
                i am goin sick of ATI.

---

### Post by Téragone on 2005-10-15
[QUOTE=mincho]ya but i need an installation method please post here the method which help me in installing driver on ubuntu linux.
                i am goin sick of ATI.[/QUOTE]

See this post by mlomker :

[http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)

---

### Post by pjcarr42 on 2005-10-19
I am also having similar trouble with the ATI 9550. It is not recognized in the device manager. Display and 2d seem to work just fine, but 3d is a mess. The fglrx drivers dont seem to enable 3d...Anyway I am wondering how you guys are doing with trying to resolve this issue. I am fairly new to linux and have only been using Ubuntu for a few days so I am a bit lost. I have been using the terminal and synaptic for downloads and find that most everything else is coming along just fine.....but on this issue ???? no clue!!
paul

ps..also wondering if this problem is limited to AMD. I am using the 3200 Athlon XP...

---

### Post by mlomker on 2005-10-19
> AMD. I am using the 3200 Athlon XP...

No.  I have an amd64 with a Mobility 9700 card and all of the [how-to's]("http://ubuntuforums.org/showthread.php?t=75382") are based on it. There may be an issue with certain 9550 cards, though.

---

### Post by silverash on 2005-10-21
So did anyone get this card to work on duel display?

I don't mind not having 3d or acc but i do mindthat i have two screnns with the same content. When every I try these fixs I can get the thing to work where all the logs and info command tell me its working but the desktop only shows on part of the one monitor.

Can some one who got duel screen let me know how you got yours to work.

Thanks
Alex

P.S. p3, Breezy Badger, ATI Radeon 9550,  17" ViewSonic E70f x 2

---

### Post by SilverTab on 2005-10-21
I gave up trying to make it work...when I need 3d graphic power, I boot in window... sad, but its simple, and it works...one more reason why I wont install linux only on my computer...

even though im on it 90% of the time...I still need windows for a couple of things...3d graphics being one of them...

the sad part is that it was working perfectly in hoary...

---

### Post by mlomker on 2005-10-23
> the sad part is that it was working perfectly in hoary...

Sivertab, I'm getting an increasing number of people contacting me with this firegl_unlock error.  Have you opened a bugzilla ticket on this yet?  One of the people with the problem needs to open it so that they can request config files/information from you to troubleshoot the issue.

---

### Post by ilans on 2005-10-23
[QUOTE=mlomker]Sivertab, I'm getting an increasing number of people contacting me with this firegl_unlock error.  Have you opened a bugzilla ticket on this yet?  One of the people with the problem needs to open it so that they can request config files/information from you to troubleshoot the issue.[/QUOTE]

I opened these bug:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=18314](https://bugzilla.ubuntu.com/show_bug.cgi?id=18314)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=17823](https://bugzilla.ubuntu.com/show_bug.cgi?id=17823)

I don't know what cause the problem, and I don't have much experience
with bugzilla. I'll be glad if I opended well the bugs...

---

### Post by ilans on 2005-10-23
I made more 2 tests in order to solve the problem:
1. install again a fresh copy of Ubuntu breezy (not upgrade)
   and have the same problem
2. I upgrade the kernel. look this thread:
   [http://ubuntuforums.org/showthread.php?t=80248](http://ubuntuforums.org/showthread.php?t=80248)

and I get the same problem:
code:
uname -a
Linux ubuntu1 2.6.13-ck8.20051020 #1 Fri Oct 21 00:03:28 HST 2005 i686 GNU/Linux <<<------------------------------

ilan@ubuntu1:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Inter face (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (re v 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (re v 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (re v 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (re v 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Contr oller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 St orage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Co ntroller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02 )
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC '97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 415 3 <<<------------------------------
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173 <<<------------------------------
0000:02:03.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capt ure (rev 11)
0000:02:03.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (r ev 11)
0000:02:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 01)


ilan@ubuntu1:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) <<<------------------------------
OpenGL renderer string: Mesa GLX Indirect <<<------------------------------
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

---

### Post by vicus on 2005-11-14
Hello everybody.

I have a Hercules Radeon 9600 256 MB Ram. Works well in Windows (but only with 4X AGP, don't know if this issue is solved yet), but in Linux there isn't any 3D acceleration. I tried using ATI official driver and also the opensource driver, the same result. When starting X, fglrxinfo command or ATI Panel still tells that OpenGL works with Mesa. The Motherboard has a Nforce2 chipset, i used Fedora COre 3, Suse 9.2 and Ubuntu. I am currently using Ubuntu, i am going to stick with it for a while. My newest attempt has these steps:
1. Uninstall all fglrx packages.
2. Mount POSIX shared memory.
3. Install ATI driver (in runlevel 3, Gnome is stopped).
4. run 'dpkg-reconfigure xorg-xserver'
5. Reboot. Start X.
The result is the same:( I attached the xorg configuration, the file is xorg_new.conf.
I also attached the xorg conf and the X log from a previous attempt. I really really hope you could give me a hand, cause this one is killin me...

---

### Post by johanPO on 2005-11-14
Hi,

in your xorg_new.conf you have ati as "driver". This is what mine looks like

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"
EndSection

What do you get if you run sudo dmesg | grep fglrx ?

---

### Post by vicus on 2005-11-15
Thank Johan, but finally it works. I just followed Mlomker howto about the new ATI driver. Super.

---

### Post by sparhawk on 2005-11-19
[QUOTE=ilans]After a lot of experiments (includ the "how-to" manual) I finally found the
reason that prevent 3D  accelereation on my pc.
My card (ATI Radeon 9550) is not recognize by Ubuntu kernel

lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173[/QUOTE]

Ilians try running the command "update-pciids" it will update the ids of all pci devices to the newest.

---

### Post by mlomker on 2005-11-19
[QUOTE=sparhawk]Ilians try running the command "update-pciids" it will update the ids of all pci devices to the newest.[/QUOTE]

That is really cool!  Thanks.

---

### Post by almahtar on 2005-11-26
[QUOTE=sparhawk]Ilians try running the command "update-pciids" it will update the ids of all pci devices to the newest.[/QUOTE]
Thanks!  lspci|grep ATI used to say:
```
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 10)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 01)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955


```

and now says:
```
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

```

Thanks a lot!  I've been getting the firegl_unlock error and it's had me stumped.  I'll test if this fixed it.

---

### Post by almahtar on 2005-11-28
Well it didn't fix my problem, but it's nice that all (most of) my hardware's recognized now, so thanks for that!

---

### Post by erakepio on 2006-02-27
ive got exactly the same problem.  all my hardware is recognised and works correctly..barring the gfx card.  I've tried downloading and running the installer file for ATi cards with no success.

I then tried this fglrx thing and it still didnt seem to fix the problem.  I like ubuntu but i just cannot work in 1024x768 and prefer tp work in larger resolutions such as 1280x1024

---

### Post by Demon Designs on 2007-07-25
I am new at this but i hav the exact same card how can this be done in an easier way?

---

### Post by Ian Clark on 2008-03-01
I have an ATI Radeon 9550, too.  Ubuntu had the ATI driver going, but not the Radeon.  So I changed that.  Now the options are in color - not greyed out under "appearance".  But I still get an error message stating: "Desktop Effects could not be enabled".  It's now 2008, and I don't know if this bug has been fixed for Ubuntu Gutsy 7.10 yet.  If anyone has any links or suggestions, it would be appreciated.

---

