---
title: "HELP!! update hosed my ATI graphics driver!!"
date: 2010-09-30
forum: Multimedia Software
---

### Post by mattkerle on 2010-09-30
Hi guys, looking for some help as I'm pretty out of my depth with this one. I'm running Ubuntu 9.10 on a dell XPS 1645 laptop with an ATI graphics card.

I was previously running the proprietary ATI FGLRX driver and with the exception of screen artefacts on resume from hibernate, it worked fine with compiz the works.

Unfortunately I took an update the other day that totally hosed my graphics setup, and now I'm forced to run under the default "low resolution" settings, which are ok but have disabled compiz and all transparencies.. :-(

After the update I had to reboot (wtf? oh ok graphics is a kernel 
driver..), and got the following error message:
[FONT="Courier New"]
Ubuntu is running in low-graphics mode
the following error was encountered. You may need to update your configuration to solve this.
(EE)Unable to initialise PCS Database
(EE)  Missing PCS defaults file /etc/ati/amdpcsdb.default
(EE)No devices detected
[/FONT]

I tried to continue to boot but the low resolution mode was pretty awful, so I ended up uninstalling the ATI driver from Administration->Hardware drivers, and now my system is stable but no transparencies or Compiz.. :-(

Any ideas how to fix this? I found [this old bug]("https://bugs.launchpad.net/ubuntu/karmic/+source/fglrx-installer/+bug/440233") on launchpad but it's a year old so I don't quite trust it... I'm thinking I might need to rollback to a previous version of the driver?

info: 
```

$ apt-cache search fglrx
xserver-xorg-video-radeon - X.Org X server -- ATI Radeon display driver
fglrx-modaliases - Identifiers supported by the ATI graphics driver
jockey-common - user interface and desktop integration for driver management
jockey-gtk - GNOME user interface and desktop integration for driver management
jockey-kde - KDE user interface and desktop integration for driver management
fglrx-amdcccle - Catalyst Control Center for the ATI graphics accelerators
fglrx-kernel-source - Kernel module source for the ATI graphics accelerators
xorg-driver-fglrx - Video driver for the ATI graphics accelerators
xorg-driver-fglrx-dev - Video driver for the ATI graphics accelerators (devel files)

$lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9488]
```

```

Commit Log for Tue Sep 28 11:56:14 2010

Upgraded the following packages:
fglrx-amdcccle (2:8.660-0ubuntu4) to 2:8.660-0ubuntu4.1
fglrx-modaliases (2:8.660-0ubuntu4) to 2:8.660-0ubuntu4.1
flashplugin-installer (10.1.82.76ubuntu0.9.10.1) to 10.1.85.3ubuntu0.9.10.1
openssl (0.9.8g-16ubuntu3.1) to 0.9.8g-16ubuntu3.2
thunderbird (3.1.5~hg20100920r5804+nobinonly-0ubuntu2~umd2~karmic) to 3.1.5~hg20100926r5805+nobinonly-0ubuntu1~umd1~karmic
thunderbird-gnome-support (3.1.5~hg20100920r5804+nobinonly-0ubuntu2~umd2~karmic) to 3.1.5~hg20100926r5805+nobinonly-0ubuntu1~umd1~karmic
xorg-driver-fglrx (2:8.660-0ubuntu4) to 2:8.660-0ubuntu4.1
xulrunner-1.9.2 (1.9.2.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~karmic) to 1.9.2.11~hg20100925r34605+nobinonly-0ubuntu1~umd1~karmic
```

---

### Post by Yellow Pasque on 2010-09-30
Make sure everything is purged:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
Then you should be able to install the driver normally.
Also, consider upgrading to lucid.

---

### Post by mattkerle on 2010-09-30
I'd already removed some of those packages so your command line didn't work initially, not sure what the following did??

I'll try installing the driver again. I've avoided upgrading to Lucid so far cos this is my work machine and I finally managed to get it stable with graphics drivers, wireless drivers etc etc, so I've been waiting for some spare time to upgrade in case the proverbial hits the rotator and I need to restore everything. 


```

$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fglrx

$ sudo apt-get remove --purge fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting xorg-driver-fglrx for regex 'fglrx_*'
Note, selecting fglrx-kernel-source for regex 'fglrx_*'
Note, selecting xorg-driver-fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx-driver-dev for regex 'fglrx_*'
Note, selecting xfree86-driver-fglrx for regex 'fglrx_*'
Note, selecting fglrx-control-qt2 for regex 'fglrx_*'
Note, selecting fglrx-modaliases for regex 'fglrx_*'
Note, selecting xfree86-driver-fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx-amdcccle for regex 'fglrx_*'
Note, selecting fglrx-driver for regex 'fglrx_*'
Note, selecting fglrx-control for regex 'fglrx_*'
E: Couldn't find package fglrx_*
```

---

### Post by mattkerle on 2010-09-30
hmmm now the ATI driver doesn't even show up as an option in the Hardware Drivers list to install!!!

---

### Post by mastablasta on 2010-09-30
which card you have? open source should be able to provide you with effects and all the whizz.

---

### Post by Yellow Pasque on 2010-09-30
> **mattkerle said:**
> hmmm now the ATI driver doesn't even show up as an option in the Hardware Drivers list to install!!!
Hmm, it shouldn't have removed modaliases (I'll check into that, THANKS). Anyway, you can add it back manually:
```
sudo apt-get install fglrx-modaliases
```
Now driver should show in Jockey again.

---

### Post by mattkerle on 2010-09-30
```
$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc Device 9488
```

not sure what that means??? it's a Dell 1645 XPS laptop, so not sure what the graphics would be, I don't have the spec sheet for it as work provided it (how I curse the day I didn't copy down the specs from the order form!!) [Google tells me]("http://developer.amd.com/gpu_assets/ATI_Device_IDs_Jan_09.txt") it's a "ATI MOBILITY  RADEON HD 4670 ,M96"

I'm not sure what graphics driver I'm using now, I assume it's the OS one as I have my screen resolution and the refresh rate doesn't suck, but I've lost the transparencies I had and none of the compiz magic is happening anymore, eg compiz still looks like it's enabled, but CTRL+ALT+LMOUSEDOWN doesn't do anything anymore, where it used to rotate the cube.

How do I check the installed status of the OS graphics driver? (sorry feeling very n00by right now...)

---

### Post by mattkerle on 2010-09-30
ok thanks that put it back, just reinstalled it so I'm about to restart, I'll report back if that changes anything...

---

### Post by tommcd on 2010-09-30
> **mattkerle said:**
> ```
$ 
How do I check the installed status of the OS graphics driver? (sorry feeling very n00by right now...)
To check the installed status of the driver try running:
[CODE]aptitude search fglrx
```
An "i" before the package means it is installed. A "p" before the package means it is purged (i.e., not installed). A "B"  before a package means it has broken dependencies. An "i A" before a package means it was automatically installed, usually as a dependency for some other package.

---

### Post by Yellow Pasque on 2010-09-30
> **mattkerle said:**
> ```
$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc Device 9488
```

not sure what that means???

It means you should update your PCI ID's (or your OS ;) )
```
sudo update-pciids
```

---

### Post by mattkerle on 2010-09-30
restarted, straight back to the "Unable to initialise PCS Database" error.. :-(

remembered that originally I couldn't get the driver to install from the Hardware drivers applet so I had downloaded the driver installer directly from ATI and installed that. reinstalled the (admittedly old) 8.723 proprietary driver that I had. After a reboot Catalyst control center reappeared, but graphics performance was terrible (couldn't paint windows while dragging) so it looked like the driver wasn't working and was using instead some kind of low-graphics mode.

ran "sudo sh /usr/share/ati/fglrx-uninstall.sh" to get rid of everything and am about to give up until I can download the latest drivers from ATI. that's 90mb so will have to wait a bit.. :-(

almost at the point of giving up... (posted from the backup vista laptop :( )

---

### Post by mattkerle on 2010-09-30
> **Temüjin said:**
> It means you should update your PCI ID's (or your OS ;) )
```
sudo update-pciids
```

haha maybe it's the OS I need to update! I have **enormous** pain with the wireless in 9.10 (gnome network manager is so buggy it hurts..), so if the Lucid one is better maybe I should just bite the bullet...

```
$ sudo update-pciids
Downloaded daily snapshot dated     2010-08-27 03:15:02
$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc Device 9488
```

so, apart from upgrading to Lucid, do I have any options here?

---

### Post by Yellow Pasque on 2010-09-30
I guess your GPU vendor just made a generic name string. No big deal, as long as you know it's M96/Mobility 4670. When you install the driver, follow this guide (some things may be slightly different in Karmic). It uses .debs and dkms, so a kernel update shouldn't hose things... [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

I attached your missing file, just in case (though it may not work as it's from Catalyst 10-8)

---

### Post by logan85 on 2010-09-30
In 10.04 after updating the kernel i had the same problem, and reinstalling the catalyst driver did not work, so i went to /usr/share/ati/ and there was a script, and i ran it by: sudo sh ./fglrx-uninstall.sh and after reboot everything was fine. Hope this will help.

edit: sorry, i see that you had already done that.

---

