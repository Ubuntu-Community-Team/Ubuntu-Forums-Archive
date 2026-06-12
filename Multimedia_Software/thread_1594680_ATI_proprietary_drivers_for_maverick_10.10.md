---
title: "ATI proprietary drivers for maverick 10.10"
date: 2010-10-12
forum: Multimedia Software
---

### Post by Divan Santana on 2010-10-12
Hi All,

I'd like to get the ATI proprietary drivers working on ubuntu 10.10 since the ubuntu-netbook interface is completely useless without it on most ATI laptops/netbooks.

Has anyone managed to get it working?
The latest un-released Catalyst 10.10 drivers are supposed to support it. A public link to the rc1 is at [http://www.ati-forum.de/allgemein/downloads/treiber/3269-catalyst-10-10-beta-f%C3%BCr-linux/](http://www.ati-forum.de/allgemein/downloads/treiber/3269-catalyst-10-10-beta-f%C3%BCr-linux/)

I can't get it past the uncompressed stage(although on opensuse 11.3 it did work).

Any one have any luck with this?

---

### Post by Divan Santana on 2010-10-12
Otherwise does anyone have any idea how to install the old ubuntu (therefore non unity)netbook interface on maverick?

---

### Post by sendblink23 on 2010-10-12
> **Divan Santana said:**
> Hi All,

I'd like to get the ATI proprietary drivers working on ubuntu 10.10 since the ubuntu-netbook interface is completely useless without it on most ATI laptops/netbooks.

Has anyone managed to get it working?
The latest un-released Catalyst 10.10 drivers are supposed to support it. A public link to the rc1 is at [http://www.ati-forum.de/allgemein/downloads/treiber/3269-catalyst-10-10-beta-f%C3%BCr-linux/](http://www.ati-forum.de/allgemein/downloads/treiber/3269-catalyst-10-10-beta-f%C3%BCr-linux/)

I can't get it past the uncompressed stage(although on opensuse 11.3 it did work).

Any one have any luck with this?

You do know.. that the FGLRX provided in Ubuntu 10.10 is actually pretty much like *Catalyst 10  driver right?  :P
If you read the actual driver numbers, it is Higher than Catalyst 10.9 so its basically running a catalyst 10.10 driver

FGLRX (Meerkat 10.10) - System > Administration > Additional Drivers = 8.780
Catalyst 10.9 = 8.771

If you want to compare it here is a screen shot of Catalyst 10.9, read the driver packaging number:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169761&d=1284753117[/IMG]

But ofcourse when the official Catalyst 10.10 is released (then De-Activate the ones for S>A>AD)... then it install the official Catalyst 10.10... so honestly relax and WAIT FOR IT, don't use any beta's from around... keep using whats provided from *S>A>AD* until Catalyst 10.10 is officially released

---

### Post by Divan Santana on 2010-10-12
Wow - that was quick.
Actually on got Catalyst 10 RC1 installed.

It is like you said likely the same as what is shipped with ubuntu maverick.

I was hoping to a different result but after running aticonfig post install it says no supported detected adapters. Bummer.

Not sure that the official catalyst release will be any different. Point is I should likely downgrade back to ubuntu 10.04 as the netbook interface is broken(and bug filed) without a proprietary ATI driver.


root@angela-laptop:~# sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64

---

### Post by André Oliva on 2010-10-25
Hello, Divan Santana, I have the same problem as you. I have the same video card, and tried to install Unity in my laptop. After about two weeks of searchs, I found that

[LIST]
[*]ATI doesn't give support any more for ATI Radeon X1200, so the proprietary Linux driver FGLRX won't work on Maverick (the proprietary driver works with Ubuntu <= 9.10). So, we have to use the open source radeon driver of Xorg.
[*]The open source drivers have good 3d acceleration (acceptable) on Ubuntu 10.04.1 LTS. I recommend you to use 10.04.1 until this problem is solved.
[*]Even with the good 3d acceleration in Lucid, Unity may not work with our graphics card. I tried to install Unity in Lucid using the ppa described in the [**ubuntu wiki**]("https://wiki.ubuntu.com/Unity"), but it didn't worked. In the [**release notes of Maverick**]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes"), it is noted that Unity may not work at all in some ATI cards.
[*]I started a [thread]("http://ubuntuforums.org/showthread.php?t=1603145") about this issue. I tried the development drivers described there but it didn't worked for me at the moment.
[/LIST]
I filed a [**bug in Launchpad**]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665991") about this problem, and I invite you to mark "this bug also affects me" and add some comment.

Good luck!

---

### Post by André Oliva on 2010-10-25
Ah, and if you have a netbook and want the .iso image for Ubuntu Netbook Edition 10.10 LTS, go to an Ubuntu mirror, like
[http://mirrors.ucr.ac.cr/ubuntu-cd/10.04.1/](http://mirrors.ucr.ac.cr/ubuntu-cd/10.04.1/)

and you can click 
[ubuntu-10.04-netbook-i386.iso]("http://mirrors.ucr.ac.cr/ubuntu-cd/10.04.1/ubuntu-10.04-netbook-i386.iso") to download

---

### Post by Divan Santana on 2010-10-26
Thanks for the help. I landed up downgrading back to 10.04 netbook edition due to this. Will keep an eye on the bug report and if support improves will upgrade at a later stage.

Thanks

---

### Post by P4man on 2010-10-29
Has anyone tried this with 10.10 drivers (I mean catalyst 10.10) ?

Id like to try out unity but it corrupts horribly on my 4870 with the restricted drivers (10.9) The OSS drivers are not an option as they make my GPU fan spin almost nonstop (this is a hot and loud card).

---

### Post by R33D3M33R on 2010-11-01
Has anyone tested 10.10 on 64-bit system? I'm receiving screen lockups in Unreal Tournament '99. I can get into tty, kill ut-bin and the system works like normal afterwards. I can start UT again, but after some time playing, it locks up again, and so on. I had Lucid 32-bit installed on this same system and everything worked flawlessly. My card is HD 4670.

---

### Post by André Oliva on 2010-11-05
Check if your card is currently supported by ATI (on ATI/ADM website). If it is, try to install Catalyst. If not, don't try it. You have to use the open source drivers... I have problems with that drivers, but by some reason (Ubuntu Development Summit?) Nobody from the Drivers Team have responded to the bug that I filed.

---

### Post by R33D3M33R on 2010-11-07
Well, I already installed Maverick 32-bit and drivers from the repository. It works flawlessly now. The 64-bit drivers seem to be broken for my hardware combination.

---

### Post by ErikT63 on 2010-11-07
> **R33D3M33R said:**
> Has anyone tested 10.10 on 64-bit system? I'm receiving screen lockups in Unreal Tournament '99. I can get into tty, kill ut-bin and the system works like normal afterwards. I can start UT again, but after some time playing, it locks up again, and so on. I had Lucid 32-bit installed on this same system and everything worked flawlessly. My card is HD 4670.

I have Catalyst 10.10 running with Maverick 64-bit. So far my biggest problem is that I haven't been able to enable compositing in Metacity or Compiz. Besides that, there are a few buggy things like flash crashing and an occasional OpenOffice document getting temporary unreadable. I'm still searching for solutions. 

For gaming, I played Warzone 2100 once and it seemed to work fine. Besides that, I really don't play games on my comp so I don't have much experience with that.

---

### Post by Niccola on 2010-11-07
Mine Catalyst Control Center is the downloaded 10.10 in amd.com
but in the acccle is saing 2.12

see the image:
[IMG]http://img231.imageshack.us/img231/795/capturadetelatz.png[/IMG]


There's something wrong?

---

