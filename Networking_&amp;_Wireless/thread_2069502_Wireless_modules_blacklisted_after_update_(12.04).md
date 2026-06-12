---
title: "Wireless modules blacklisted after update (12.04)"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by SThom27 on 2012-10-10
I was prompted to update today, but something went wrong.  It didn't fully update and when I restarted, all I got was a black screen.  So I rebooted into "safe mode" and finished the update, but when I restarted my wireless wasn't working.

I checked [http://help.ubuntu.com/community/BroadcomSTA(Wireless)](http://help.ubuntu.com/community/BroadcomSTA(Wireless)) and made sure I had the right drivers installed.  After making sure the bcmwl-kernel-source package was installed, I went to the Additional Drivers page and tried to install the STA drivers.  It didn't work.  It told me to check /var/logs/jockeylog for what was wrong.  Here's what I saw:

[PHP]2012-10-10 21:24:23,312 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-10-10 21:24:23,350 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-10-10 21:24:52,569 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-10-10 21:24:52,588 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-10-10 21:24:52,744 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted[/PHP]So, no wireless still.

Here's the rest:

Dell 1545 with a the BCM4312 wireless card.  "lsmod" shows no wireless modules and "iwconfi" shows no wireless extensions.  I'm running Ubuntu 64-bit with the 3.5.0-17-generic kernel.  Also this:

[PHP]$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...  [/PHP]I have no idea what updates were trying to install when all this broke.  I've also replaced network-manager with WICD.  Any help is appreciated.

---

### Post by misfit815 on 2012-10-13
Having the same issue with Lubuntu after update. Any help is appreciated.

---

### Post by chili555 on 2012-10-13
Will you both please post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by SThom27 on 2012-10-13
I tried everything I could find on this forum and on AskUbuntu and finally decided it might be due to installing Gnome Shell, Cinnamon, or the full Kubuntu suite.  After fully uninstalling every little app, widget, and library, still nothing worked.

So, I backed everything up and reinstalled.  Hope you get some help.  I don't know if this forum is just that dead or what, but I don't have time to wait days without wireless.

FYI, there's a lot of threads in this forum and on AskUbuntu with lots of things to try.  In my case, I think it was related to having installed the full Kubuntu desktop complete with all libraries and apps.  I had uninstalled network-manager and replaced it with WICD and that could have been part of the problem as well.

Good luck!

Edit: I don't know if it'll help now, but here's what was asked for (from my now working re-install)
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

---

### Post by chili555 on 2012-10-14
> I think it was related to having installed the full Kubuntu desktop complete with all libraries and apps. I had uninstalled network-manager and replaced it with WICD and that could have been part of the problem as well.It's amazing the urban lore that gets spread around and accepted as gospel. It's not your fault. The ONLY reason is that you don't have the correct driver/firmware combo for your device. All the Gnome/Unity/NM/Wicd is red herring and guesswork on the part of the post answering 'experts.' 

Please do:```
sudo su
apt-get remove --purge bcmwl-kernel-source
apt-get install firmware-b43-lpphy-installer
echo b43 >> /etc/modules
exit
```Reboot and let us have your report.

---------
WARNING: misfit815 and other searchers; unless your device is also Broadcom Corporation BCM4312 802.11b/g [COLOR="Red"]LP-PHY[/COLOR] [[COLOR="Red"]14e4:4315[/COLOR]], the fix may be different.

---

### Post by misfit815 on 2012-10-14
Results:

```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

I followed the instructions above, but still do not have wireless.

---

### Post by chili555 on 2012-10-15
> **misfit815 said:**
> Results:

```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

I followed the instructions above, but still do not have wireless.Let's see:```
sudo modprobe b43
dmesg | grep b43
```Thanks.

---

### Post by misfit815 on 2012-10-15
```
[   21.035146] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   81.890495] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   81.890501] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   81.890504] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

Thanks for your help. I'm going to see where that link leads me now.

...which led me to...

$ sudo apt-get install firmware-b43-installer

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firmware-b43-lpphy-installer
The following NEW packages will be installed:
  firmware-b43-installer
0 upgraded, 1 newly installed, 1 to remove and 1 not upgraded.
Need to get 3,524 B of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/multiverse firmware-b43-installer all 1:015-9 [3,524 B]
Fetched 3,524 B in 0s (23.6 kB/s)           
(Reading database ... 234752 files and directories currently installed.)
Removing firmware-b43-lpphy-installer ...
Deleting old extracted firmware...
Selecting previously unselected package firmware-b43-installer.
(Reading database ... 234747 files and directories currently installed.)
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-9_all.deb) ...
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
An unsupported BCM4312 Low-Power (LP-PHY) device was found.
Use b43 LP-PHY firmware (firmware-b43-lpphy-installer package) instead.
Aborting.

```

---

### Post by chili555 on 2012-10-15
> An unsupported BCM4312 Low-Power (LP-PHY) device was found.
Use b43 LP-PHY firmware ([COLOR="Red"]firmware-b43-lpphy-installer[/COLOR] package) instead.And did you??

---

### Post by misfit815 on 2012-10-15
Yup. Went something like this...

```

sudo apt-get remove --purge firmware-b43-lpphy-installer
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer

```

And now I'm back on wireless. It looks like whatever was updated the other day somehow hosed something associated with the lpphy package, and removing and reinstalling it took care of the issue.

Thanks.

---

### Post by chili555 on 2012-10-15
Glad it's working! Please use thread tools at the top to mark solved.

---

