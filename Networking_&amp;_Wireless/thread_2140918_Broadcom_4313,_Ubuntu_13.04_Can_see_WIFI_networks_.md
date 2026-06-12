---
title: "Broadcom 4313, Ubuntu 13.04: Can see WIFI networks but not connect to them"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by green white blue on 2013-05-01
I have a Lenovo g580 with a Broadcom 4313 802.11 Wireless Lan Controller (STA). I can see wireless networks but not connect to the WPA2 Personal used in this household. It tries to and then seems to time out. I have a fresh install of 13.04. The printer and a Windows 7 laptop is connected to it, so that should work.

In fact, I had installed Ubuntu 12.10 earlier (WIFI worked then) and upgraded it to 13.04. From that point on it was broken. Thinking the upgrade broke something I wiped everything and cleanly installed 13.04.

I'd be grateful for any solutions. I am an absolute beginner when it comes to Ubuntu.

---

### Post by LuigiMazzini on 2013-05-01
I have the same problem. No solution found yet. 
Ubuntu on computers with Broadcom 4313 is really disturbing. Without Windows I would be in trouble now.

---

### Post by Subq on 2013-05-02
After 2 days of tinkering with the same Broadcom 4313 issue in 13.04, the only fix I found to work is to downgrade bcmwl-kernel-source to the 12.10 release version:

Turn off wireless and run

```
sudo apt-get remove bcmwl-kernel-source
```

Download [bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_i386.deb]("http://packages.ubuntu.com/quantal/i386/bcmwl-kernel-source/download") and install.

Lock the package version to prevent future updates:

```
gksudo gedit /etc/apt/preferences.d/bcmwl-kernel-source
```

and paste in the following:

```
Package: bcmwl-kernel-source
Pin: version 5.100.82.112+bdcom*
Pin-Priority: 1001
```

Restart your computer.

Good luck!

---

### Post by green white blue on 2013-05-03
I can't try that out since I am back on 12.04 but I really appreciate the effort. Thanks!

---

### Post by LuigiMazzini on 2013-05-03
Thanks for help. 
Unfortunately I didn't make it. When trying to install the downloaded [bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_i386.deb]("http://packages.ubuntu.com/quantal/i386/bcmwl-kernel-source/download") I get this:
> Selecting previously unselected package bcmwl-kernel-source. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 187905 files and directories currently installed.) 
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_i386.deb) ... 
dpkg: dependency problems prevent configuration of bcmwl-kernel-source: 
 bcmwl-kernel-source depends on dkms. 
 bcmwl-kernel-source depends on linux-headers-generic-pae | linux-headers. 
 
dpkg: error processing bcmwl-kernel-source (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 bcmwl-kernel-source

---

### Post by Subq on 2013-05-03
LuigiMazzini,

Looks like a simple dependency problem. Just install the following:

```
sudo apt-get install dkms linux-headers-generic-pae
```

Then run through the above steps beginning with step one.

---

### Post by LuigiMazzini on 2013-05-03
Thanks for your reply.
Seems Ubuntu has some serious problems after upgrading to 13.04.
Trying to do
> **Subq said:**
> 
```
sudo apt-get install dkms linux-headers-generic-pae
```

is not successful and gives this error:
> luigimazzini@Ubuntu:~$ sudo apt-get install dkms linux-headers-generic-pae
[sudo] password for luigimazzini: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
dkms set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-headers-generic-pae:i386 : Depends: linux-headers-generic:i386 (= 3.8.0.19.35) but it is not going to be installed
E: Unable to correct problems, you have held broken packages


---

### Post by Subq on 2013-05-03
If you upgraded to 13.04 rather than a clean install, then that's likely the source of the dependency problem and may be more trouble than it's worth to sort out as opposed to just running a clean install. If you decide to go with the clean install, be sure dkms and headers are installed before running the steps above and you should be ok.

I've kept notes on fixes for b4313 in Ubuntu over the last few years, but with 13.04 the bcmwl-kernel-source downgrade is the only one that worked for me. Hopefully it'll work for you as well.

Let us know how it goes.

---

### Post by Hadaka on 2013-05-03
Hi, give this a try..
[http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619)
post #31
read carefully,follow closely.
to check if you are 32 or 64 bit
do...
[CODE]  arch [CODE]
good luck.

---

### Post by LuigiMazzini on 2013-05-05
Thanks for your replies.
Hadaka: I tried but no success.
Subq: I will probably try with a clean install. I'm worried about it - as I try to do all the suggested things while running Ubuntu from the USB stick I can't fix it. Here's where I get stuck:
[http://i1273.photobucket.com/albums/y416/LuigiMazzini/Screenshotfrom2013-05-05135539_zps937209d6.png](http://i1273.photobucket.com/albums/y416/LuigiMazzini/Screenshotfrom2013-05-05135539_zps937209d6.png)
Now I have Ubuntu 13.04 (x86_64) on USB and can't decide whether it's worth to install it on the disc or should I just downgrade the non-functioning 13.04 (which is currently installed on the disc).

---

### Post by DonL on 2013-05-05
Thank You!!!!
I spent hours trying to figure that out. I'd offer you a beer for that!

---

### Post by varunendra on 2013-05-06
> **LuigiMazzini said:**
> Hadaka: I tried but no success.
LuigiMazzini, can you please share with us at which step did you get an error and what was it? The suggested method is still an experimental one, but we already have seen it succeed on two fresh installations of 13.04.

> **DonL said:**
> Thank You!!!!
I spent hours trying to figure that out. I'd offer you a beer for that!
[s]LuigiMazzini[/s] **[COLOR="#800000"]DonL[/COLOR]**, we'd really appreciate if you can disclose who is getting the beer, we won't ask for a share - promise!! *[COLOR="#696969"](lying)[/COLOR]* :P

Ok, seriously, it helps a lot if you clearly state which method worked for you, because then others can try or suggest it to others with more confidence. Thanks for your feedback! :)

---

### Post by LuigiMazzini on 2013-05-06
Varunendra, thanks for your reply.
I'll give another try in next days and will report about how it goes. This time I decided to go from the beginig, including download and fresh install of 13.04. I'm sure we will get it working. ;)

---

### Post by mutated on 2013-05-08
The very first method in this thread worked for me - took a bit to get the file transferred over, but it worked like a charm!

---

### Post by varunendra on 2013-05-08
> **mutated said:**
> The very first method in this thread worked for me - took a bit to get the file transferred over, but it worked like a charm!

Thanks for your valuable feedback mutated. You mean the solution in [post #3]("http://ubuntuforums.org/showthread.php?t=2140918&p=12630816#post12630816")?
Could you please also share with us which version of Ubuntu and which kernel version you succeeded at (**uname -mr** for kernel version)? Just to confirm.

Although I can see that the driver suggested in that post has been patched for kernel version 3.4 (and hopefully higher ones too), but I don't have 32 bit copy of 13.04 to test myself, so I'd appreciate your response. Thanks :)

---

### Post by wildmanne39 on 2013-05-08
Hi, please do not use large images, alot of people do not have a real fast connection and it creates problems for them to load pages.
Thanks

---

### Post by irober02 on 2013-05-24
Worked perfectly for me thanks.

---

### Post by praseodym on 2013-05-24
Hi,

this device normally runs with the free driver brcmsmac, only the firmware is missing:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```

Shut down without any current source for 10 minutes and restart. Alternatively, the firmware can be downloaded via git:
```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git 
```
The needed files need to be copied from "linux-firmware" to /lib/firmware

---

### Post by gdholly on 2014-01-15
> **praseodym said:**
> Hi,

this device normally runs with the free driver brcmsmac, only the firmware is missing:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```

Shut down without any current source for 10 minutes and restart. Alternatively, the firmware can be downloaded via git:
```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git 
```
The needed files need to be copied from "linux-firmware" to /lib/firmware

Posting to confirm this as a solution, and to thank all the posters in this thread.  I learned a lot working on this problem, and I could not have solved this without this great community resource.

---

### Post by varunendra on 2014-01-15
Welcome to the forums gdholly ! :)

Just so you know, this device should work out-of-box with kernel versions 3.8 and later. Everything required is already in the kernel, just make sure NOT to install the "wl" (or sta, or "bcmwl.." - same thing, different names) driver while or after installing. It (the "wl" driver) blacklists the native drivers to avoid conflicts, so they can't load while it is installed.

If you choose to "Install Updates" during installation, the "wl" driver automatically gets installed (if you are connected to internet) and often causes troubles afterwards with this card.

Even the kernel 3.2 series should work with the native brcmsmac driver, but its newer versions (in kernel 3.8 and later) are much better.

---

### Post by gdholly on 2014-01-15
Then my "install updates during installation" was the culprit.

Will there be problems with my implemented driver fix if I update (sudo apt-get update)?

Sorry, I should have posted that I am on Ubuntu 13.04.

---

### Post by varunendra on 2014-01-15
> **gdholly said:**
> Will there be problems with my implemented driver fix if I update (sudo apt-get update)?

No, there won't be any.

The "apt-get update" or "apt-get upgrade" or "apt-get dist-upgrade" commands as well as the "Update Manager" gui program only update/upgrade the already install packages. They don't install any additional packages, so are completely safe in that respect.

Another thing I'd like to mention here - At least two users have so far reported the native driver to be problematic on 13.10 running kernel 3.11 (or maybe even 3.12), whereas the newer version of the "wl" driver (bcmwl-kernel-source......02) worked for them. Although I took these as exceptions and there is a fair chance that they might have had some configuration issues between Ubuntu and/or their routers.

---

### Post by redlabrat on 2014-01-23
> **praseodym said:**
> Hi,

this device normally runs with the free driver brcmsmac, only the firmware is missing:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```

Shut down without any current source for 10 minutes and restart. Alternatively, the firmware can be downloaded via git:
```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git 
```
The needed files need to be copied from "linux-firmware" to /lib/firmware

Thanks a lot for this solution! It solved same problem for me on Ubuntu 12.04 LTS (3.2.0-58-generic x86_64).

---

