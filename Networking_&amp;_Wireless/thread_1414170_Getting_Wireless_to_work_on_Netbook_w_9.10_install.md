---
title: "Getting Wireless to work on Netbook w/ 9.10 installed"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by nwchandler on 2010-02-23
I bought a netbook and couldn't handle windows xp at all, so installed ubuntu 9.10, but the wireless network icon doesn't appear on the top of the screen like it should, presumably because ubuntu doesn't automatically recognize whatever card is in there. This is an asus 1001-HA. could anyone assist me with getting this thing up and running on a wireless network? Much appreciated,

Nicholas

---

### Post by chili555 on 2010-02-23
Please open Applications -> Accessories -> Terminal and do:```
lspci -nn
```Please post the result here. If it's a Ralink, I have to break out my horse tranquilizers...just kidding.

---

### Post by nwchandler on 2010-02-23
So it looks like it is Ralink.... - anyway here's the cut and pasted message from terminal...thanks in advance for any help.


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.


nicholaschandler@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
01:00.0 Ethernet controller [0200]: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

---

### Post by chili555 on 2010-02-23
You might try this: [http://ubuntuforums.org/showpost.php?p=8782864&postcount=9](http://ubuntuforums.org/showpost.php?p=8782864&postcount=9)

Let us know if you need some help.

---

### Post by nwchandler on 2010-02-23
I tried the instructions there but when i typed in the initial command it told me:

"no command 'deb' found" - did you mean:
debc (from package devscripts - main)
derb (from package libicu-dev - main)
dab (from package bsdgames - universe)
debi (from package devscripts - main)

and then  reminded me that the command deb was not found

seems like its a relatively simple fix that I'm just not getting quite correct...thanks again for bothering with this - other than that I've got my browers, my word processing, and most other things seem to be fine, i just need to have wireless running or else it's pointless almost for me to even have this so called "netbook"

---

### Post by nwchandler on 2010-02-23
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

I did find supposed linux drivers here for the 3090, and put them on an external, but opening the folder there is no obvious way for me to install them...

---

### Post by chili555 on 2010-02-23
> there is no obvious way for me to install them...That's why we need horse tranquilizers!

The deb method will be a great deal easier, so save the tar.bz2 for another day.

Open System -> Admin -> Software Sources. Click the 'Other Software' tab, click 'Add' and copy and paste the deb line we referenced.

Now walk that netwbook over to the router and connect an ethernet cable and continue with the other steps.```
sudo apt-get update
sudo apt-get install rt3090-dkms
```It may take a reboot, but your wireless should work after you detach the ethernet cable.

---

### Post by nwchandler on 2010-02-23
it worked!! I didn't actually need the first command, didn't seem to work, I just added 

deb [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu) karmic main
and then put in

sudo apt-get install rt3090-dkms
with ethernet cable plugged in. I then added all offered updates, one of which clearly related directly to the 3090 (there were over 200 total) and when I finished, I unplugged the ethernet cable, restarted, and it picked up wireless just like that. Thanks everyone for the assistance. Firefox is functioning perfectly and everything else is just like I want it, no windows, no viruses, and free software. Thanks again.

---

### Post by chili555 on 2010-02-23
> everything else is just like I want it, no windows, no viruses, and free software.Great job! Glad it's working for you. Enjoy.

---

### Post by nwchandler on 2010-05-20
Hi again,

So I installed routine updates that ubuntu told me to install today, and when I rebooted, it had lost the wireless network icon on the top of the screen that I had gotten using the help from this forum a while back. I tried to go through the process again, I deleted and redid the instructions just as I had before, but it did not work, and there is still no wireless icon. Any idea what I can do now?

---

### Post by chili555 on 2010-05-21
Please do:```
sudo modprobe rt3090sta
iwconfig
```Note any errors or warnings and post them here.

---

### Post by nwchandler on 2010-05-21
hey thanks!

sudo modprobe rt30390sta

FATAL: Error inserting rt30390sta (/lib/modules/2.6.31-21-generic/updates/dkms/rt3090sta.ko): Invalid module format

iwconfig

lo          no wireless extensions

eth0      no wireless extensions

---

### Post by chili555 on 2010-05-21
> FATAL: Error inserting [COLOR="Red"]rt30390sta[/COLOR] (/lib/modules/[COLOR="Blue"]2.6.31-21-generic[/COLOR]/updates/dkms/rt3090sta.ko): Invalid module format
I assume you really typed rt3090sta, not rt30390sta.

Is this your running kernel version?```
uname -r
```Does the behavior improve if you do:```
sudo apt-get install --reinstall dkms
sudo apt-get install --reinstall rt3090sta-dkms
```

---

### Post by nwchandler on 2010-05-21
do i need to be on the internet when i am doing all this (what you just mentioned and the last set of instructions as well)?

---

### Post by nwchandler on 2010-05-21
p.s. kernel is 2.6.31-21-generic

---

### Post by chili555 on 2010-05-21
> **nwchandler said:**
> do i need to be on the internet when i am doing all this (what you just mentioned and the last set of instructions as well)?Yes.

---

### Post by nwchandler on 2010-08-22
Hi there, it's been a long time, I didn't have the time or ability to try and deal with this during exams and paper writing so I just used my other computer, but I pulled this out today and hooked it up to the internet via ethernet cable and tried all of the things you told me to do - the first messages were the same as before - 

FATAL: Error inserting rt3090sta (/lib/modules/2.6.31-21-generic/updates/dkms/rt3090sta.ko): Invalid Module format

when i typed iwconfig, it says

lo       no wireless extensions

eth0     no wireless extensions

when i typed sudo apt-get install --reinstall dkms, it seemed to be successful, went through some things and told me to reboot, i did

when i typed the second, final command - the reinstall rt3090, 

it  said first, reading package lists, then building dependency tree, reading state information, and then it says

E: Couldn't find package rt3090sta-dkms

and finishes

not sure where to go from here... thanks in advance

---

