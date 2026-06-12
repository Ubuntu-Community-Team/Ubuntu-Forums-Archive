---
title: "Broadcom STA Wifi used to work on 11.10"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by Kronalias on 2012-04-26
Just installed 12.04 and no wifi.

Settings => Settings Manager => Additional Drivers =>

===================================================
Broadcom STA proprietary wireless driver
Tested by the Ubuntu developers
Licence: Proprietary
This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware. 

This driver is activated and currently in use.
===================================================

This driver may well be activated, but it certainly isn't in use!

Clicking on the up/down arrow thingy on the top panel reveals:
Wired network
Wired connection 1
Disconnect
VPN Connnections
Enable networking
Connection information
Edit connections

Nothing there about wifi...

... Is it me? (btw, it worked 100% under Xubuntu 11.10)

---

### Post by chili555 on 2012-04-26
Oh, boy! The fun begins! Please open a terminal and show us:```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Kronalias on 2012-04-26
Hi Chili, thank you but no, no to your 'The fun begins'. That started yonks ago!

Usually if it's not broken then you haven't tweaked enough ... but in this instance it's a brand new install..
I've been using the daily builds for some time and everything was going swimmingly until today's release (escape?) when it all went pear shaped.

Here's the output you asked for:
```

martyn@laptop:~$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
martyn@laptop:~$ 
martyn@laptop:~$ lsmod | grep -e b43 -e wl
wl                   2646601  0 
lib80211               14040  1 wl
martyn@laptop:~$

```Does this give you the info you were after?

Thanks in advance for any help or advice!

---

### Post by justin.waters on 2012-04-26
Having the same issue on stock Ubuntu 12.04 64-bit, freshly installed.

Here's the results of the commands:

```

$ lspci -nn | grep 0280
30:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
$ lsmod | grep -e b43 -e wl
wl                  2568210  0
lib80211              14381  1 wl

```

---

### Post by justin.waters on 2012-04-26
```

sudo modprobe b43

```

Did the trick for me.  Any reason why this isn't starting up on its own?

---

### Post by chili555 on 2012-04-26
The fun begins because rumor has it that Additional Drivers misidentifies the correct driver for some Broadcom cards and installs the incorrect one. I believe you are my first case!

Please do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r wl
sudo modprobe b43
```If it works as expected, we'll need additional steps to make it permanent.

---

### Post by chili555 on 2012-04-26
> **justin.waters said:**
> ```

sudo modprobe b43

```

Did the trick for me.  Any reason why this isn't starting up on its own?Please try what I suggested above and let me know.

---

### Post by justin.waters on 2012-04-26
> **chili555 said:**
> The fun begins because rumor has it that Additional Drivers misidentifies the correct driver for some Broadcom cards and installs the incorrect one. I believe you are my first case!

Please do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r wl
sudo modprobe b43
```If it works as expected, we'll need additional steps to make it permanent.

Yup, works for me.  I tried it the first time with the firmware-b43-installer package, and it also works.

---

### Post by chili555 on 2012-04-26
> **justin.waters said:**
> Yup, works for me.  I tried it the first time with the firmware-b43-installer package, and it also works.Excellent! Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
```Look around in /etc/modprobe.d and make sure the purge did not leave any blacklist of b43; if so, remove it:```
sudo rm /etc/modprobe.d/whatyoufound
```Reboot and enjoy.

@Kronalias--

Verify before you try this fix, please.

---

### Post by 1204 on 2012-04-26
Same problem when upgrading from 11.10. After reboot I had to use LAN and  then update manager showed error. Then "apt-get install -f" as it said and it removed  almost everything including kernel files. Well, home folder was still on it's place and did backup personal files to  usb-stick. Then fresh install. Install ready and rebooting to OS - no wlan  and restricted driver didin't work. Then googled and found this, and it is for BCM4311
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```And  it worked. You may optionally try this first, it removes all broadcom  stuff from your system: [SIZE=1]*sudo ap((read_before_copy_paste)t-get purge broadcom-sta-common broadcom-sta-source bcmwl-kernel-source*[/SIZE]

Now system functions perfectly! Maybe they should update install disk what comes to broadcom chips.

---

### Post by chili555 on 2012-04-26
> Now system functions perfectly! Maybe they should update install disk what comes to broadcom chips.I'm glad it's working and I'm sure the developers are working on it. You might want to add to the bug report here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379)

---

### Post by TBABill on 2012-04-26
chili555, I have seen users who, with the BCM4311 and after installing the STA driver, end up with a conflict with the system-enabled brcmsmac and the new wl module. Have you tried to have anyone blacklist the brcmsmac and bcma modules, then try to see if wl works? Just curious if that is another option to the same problem rather than installing b43.

---

### Post by chili555 on 2012-04-26
I don't believe either claim the pci.ids in question; 14e4:4311 and 14e4:4312. *wl*, on the other hand, claims both, as does *b43/ssb*. The trick is to see which actually works. So far, my previous experience and notes suggest these two are driven effectively by *b43/ssb*. I am interested in a report from Kronalias.

---

### Post by 1204 on 2012-04-27
> **chili555 said:**
> I'm glad it's working and I'm sure the developers are working on it. You might want to add to the bug report here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379)Too bad I don't have anything left except fresh system that works. Whole plot revealed to me when I rebooted after "apt-get install -f" and then it was too late. Happily I could rescue personal files with live-cd after so no big harm.

I have several other PCs to upgrade so I will wait for a week or two if anything else occurs or things been fixed. I've installed Ubuntu to ten PCs and all of the users been happy with it.

---

### Post by Kronalias on 2012-04-27
@chili555

Just a quickie to confirm things - I'd been mucking about so I did a complete reinstall and then, right after the mandatory reboot, did these:
```

sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r wl
sudo modprobe b43

```

That sorted things.

Thanks very much for your help!

---

### Post by justin.waters on 2012-04-27
> **chili555 said:**
> Excellent! Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
```Look around in /etc/modprobe.d and make sure the purge did not leave any blacklist of b43; if so, remove it:```
sudo rm /etc/modprobe.d/whatyoufound
```Reboot and enjoy.


Looks like /etc/modprobe.d/broadcom-sta-common.conf has the driver blacklisted.  I removed it, and now Wifi works when I reboot.

To summarize, the fix in its entirety seems to be:

```
sudo modprobe -r wl
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe b43
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
```

---

### Post by chili555 on 2012-04-27
Awesome! We have found the fix for at least these two cards. Please add to the bug report I referenced above.

---

### Post by rabla on 2012-04-27
I have Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) and also got that problem. I ran all the commands i found i thins topic and it helped :lolflag:

---

### Post by wewa on 2012-06-27
Don't mean to hijack this topic.

Anyone know enough about this bug to know if this would apply to other wifi devices?

I have a Compaq Presario c762 with a Atheros wifi and my hours of searching for a solution has brought me to this post.

Should I follow the broadcom instructions here?
Or is there a equivalent post for Atheros somewhere?

Thanks.

---

### Post by westie457 on 2012-06-27
> **wewa said:**
> Don't mean to hijack this topic.

Anyone know enough about this bug to know if this would apply to other wifi devices?

I have a Compaq Presario c762 with a Atheros wifi and my hours of searching for a solution has brought me to this post.

Should I follow the broadcom instructions here?
Or is there a equivalent post for Atheros somewhere?

Thanks.

Any fixes here for the Broadcom chips will not work for Atheros chips - totally different drivers are needed.

Suggest you start your own thread stating what your problem is and anything you have tried so far.

---

### Post by luifer448 on 2013-02-17
It worked for a HP Pavilion dv6-1309sl, thanks!

---

