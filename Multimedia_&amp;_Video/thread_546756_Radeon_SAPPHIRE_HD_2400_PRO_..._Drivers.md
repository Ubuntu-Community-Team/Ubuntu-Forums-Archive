---
title: "Radeon SAPPHIRE HD 2400 PRO ... Drivers?"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by asbesto on 2007-09-09
Hi, I just received this card as gift. Any info for working accelerated drivers?

my system doesn't recognize it and i'm using with the "vesa" driver :(

any help?
:(

---

### Post by uputer on 2007-09-09
The driver is not available yet but should be soon.

Check this site for updates:

[http://www.phoronix.com/scan.php?page=article&item=828&num=4](http://www.phoronix.com/scan.php?page=article&item=828&num=4)

There is also discussion in the forum about the (8.41) drivers.

---

### Post by spidernik84 on 2007-12-04
Same problem here...i'm trying to make the AGP version of this card work under ubuntu with no go.
Tried the official compiled AMD driver and Ubuntu fglrx too without any remarkable success, the driver seems to be uncompatible, considering it's working fine with an x800 and an old 9600 :|
The only wai of having a decent resolution is by using Vesa compatible driver.

I see the post has been written on september, did anyone find any solution after two months?

Thanks

---

### Post by markoloka on 2007-12-04
From my old post aka i used info from this board and phoronix forum.: 
"Script:

[http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

I would just download the script, press cntr+alt+f1 and get to the terminal. Then change it into a executable as root, then just run it. It did all the magic and I had the latest driver installed.

sudo chmod +x ./install-fglrx-debian.sh
sudo ./install-fglrx-debian.sh

To get Xv working, just type

sudo aticonfig --overlay-type=Xv in a terminal and restart your system."
Info taken from ubuntuforums.org and phoronix forum.

Edit note:
fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7059 Release

But lspci still don't know about my card. Unknown device blaah blaah.

Hope you can get it working.

---

### Post by Yellow Pasque on 2007-12-04
You can try the RadeonHD open-source driver for basic 2d support.
[http://www.phoronix.com/vr.php?view=11067](http://www.phoronix.com/vr.php?view=11067)

---

### Post by DizzyCoder on 2007-12-05
I had to join the forum just so that I could post that I can verify this (I mean markoloka's steps above) worked for me.

I have Gutsy64 (desktop install CD) and blew it away once already, but then followed these simple steps (and the wicked .sh script) to get me going...

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7059 Release

There's a new release on that ATI driver... I also got Desktop Effects working by following in the footsteps of Ub1476 from this [thread]("http://ubuntuforums.org/showthread.php?t=574302&page=4")

> Here's what I did:

Clean install of Ubuntu 7.10
Starts Ubuntu 7.10
Go to System>Administration>Restricted Driver Manager>Enable ATI driver
Next, install XGL: System>Administration>Synaptic>Search for XGL>Install the XGL package.
Search for compiz settings>Install it.
Reboot
Go to: System>Preferences>Appearance>Visual Effects>Normal/ Extra/ Custom.

It's 95% out of the box, didn't even get a X server error!

...and with some help from Furlong's [blog]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") (I'm a newb, so getting to the grass roots was crucial in getting me through...)

btw:  compiz effects are looking sweetass like OS/X - now to get a handle on all the shortcuts... ;)

---

### Post by spidernik84 on 2007-12-05
Thanks for the fast reply ;)
I tried both Markoloka and Temüjin's ways, but no go again, Gutsy still boots in vesa mode, even after setting xorg correctly (compiling the radeonhd and instructing xorg to make use of the latter).
What i'm wondering is: could maybe the fact that my sapphire hd 2600 pro is the AGP version of a natively PCIX  device cause this issues and incompatibilities?

Hanging around on Phoronix to find more, i'll keep you informed on the ending...

---

### Post by DizzyCoder on 2007-12-05
> **spidernik84 said:**
> ...
What i'm wondering is: could maybe the fact that my sapphire hd 2600 pro is the AGP version of a natively PCIX  device cause this issues and incompatibilities?

Hanging around on Phoronix to find more, i'll keep you informed on the ending...

FYI:  My card is the Sapphire Radeon PCI Express HD 2400 PRO - and did I say it's wicked sweet??!  My only complaint is that at 1680x1050 its only 60Hz, so I'm at 1280x1024 currently.

---

### Post by ScottLind on 2008-02-13
When I try to enter Restricted Driver Manager, it says: "Your hardware does not need any restricted drivers."

I have a ATi Radeon HD 2400 PRO AGP graphics card.
Can anyone help me?

---

### Post by ScottLind on 2008-02-13
> **markoloka said:**
> From my old post aka i used info from this board and phoronix forum.: 
"Script:

[http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

I would just download the script, press cntr+alt+f1 and get to the terminal. Then change it into a executable as root, then just run it. It did all the magic and I had the latest driver installed.

sudo chmod +x ./install-fglrx-debian.sh
sudo ./install-fglrx-debian.sh

To get Xv working, just type

sudo aticonfig --overlay-type=Xv in a terminal and restart your system."
Info taken from ubuntuforums.org and phoronix forum.

Edit note:
fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7059 Release

But lspci still don't know about my card. Unknown device blaah blaah.

Hope you can get it working.

[http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

how do I make it executable?

---

### Post by Pettman on 2008-02-13
> **ScottLind said:**
> When I try to enter Restricted Driver Manager, it says: "Your hardware does not need any restricted drivers."

I have a ATi Radeon HD 2400 PRO AGP graphics card.
Can anyone help me?

Try the xserver-xorg-video-radeonhd package.

---

### Post by ScottLind on 2008-02-13
> **Pettman said:**
> Try the xserver-xorg-video-radeonhd package.

Should I just run this: "xserver-xorg-video-radeonhd" in terminal?

---

### Post by Yellow Pasque on 2008-02-13
fglrx/Catalyst has major issues with AGP cards. The new 8.02 version that came out today (2/13) doesn't fix them either. Your best option is to use the radeonHD driver and wait for it to support 3D accel. Don't hold your breath waiting for AMD/ATI to fix your issues.

---

### Post by Yellow Pasque on 2008-02-13
> **ScottLind said:**
> Should I just run this: "xserver-xorg-video-radeonhd" in terminal?
It's best to build from source. Click the radeonhd link in my sig.

---

### Post by ScottLind on 2008-02-13
> **Temüjin said:**
> It's best to build from source. Click the radeonhd link in my sig.

Okay. I've followed the steps and rebooting now :)

---

### Post by Sonja on 2008-03-07
Why is it asking me to insert my Linux disc in the cdrom?

---

### Post by Sonja on 2008-03-07
OK, now my xorg.conf file is missing or empty!

---

### Post by Sonja on 2008-03-07
OK I totally reinstalled xorg and that fixed it. Now it seems to be running the HD driver (as far as I can tell), but when I go in System > Admin > Screens and Graphics, nothing opens at all.

---

### Post by ripperzane on 2008-03-30
Helpful Tip
type in the following at a terminal

sudo gedit /etc/apt/sources.list && sudo apt-get update

Goto the line that says deb cdrom:[blablabla (this would be what the specific is of your CDROM you used to install) and simply put a #
so it looks like this in my sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta amd64 (20080319)]/ hardy main restricted

I am using the Beta x64, but this goes for all versions of Ubuntu (that I am aware of).

Poof, no more "Please Insert CDROM" crud.


> **Sonja said:**
> Why is it asking me to insert my Linux disc in the cdrom?

---

