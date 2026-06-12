---
title: "Broadcom activation failed ; lspci -nn is blank"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by wfzimmerman on 2012-04-28
After upgrading to 12.04, no "Enable Wireless" visible on my Networking dropdown.  Additional Drivers > Activate > produces "installation failed, have a look at jockey.log."  

lpsci -nn produces 02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

installed b43-firmware per [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

activation still fails

jockey.log says

2012-04-28 11:22:23,674 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-04-28 11:22:23,729 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-28 11:22:25,586 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-28 11:22:26,318 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-28 11:22:26,333 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

---

### Post by chili555 on 2012-04-28
There is an issue where jockey, also known as Additional Drivers, installs the wrong driver or even multiple drivers which conflict. Your card is the poster child!> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] (rev 01)
Let's unravel this mess. Please run:```
lsmod | grep -e wl -e bcma -e brcmsmac -e b43
```When you find that, at least, bcma and brcmsmac are loaded, blacklist them. If b43 is loaded, which I doubt, blacklist it, too:```
sudo su
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
exit
```And do the same for b43 if it appears.

Reboot and give us a good report.

---

### Post by wfzimmerman on 2012-04-28
[QUOTE=chili555;11883642]There is an issue where jockey, also known as Additional Drivers, installs the wrong driver or even multiple drivers which conflict. Your card is the poster child!Let's unravel this mess. Please run:```
lsmod | grep -e wl -e bcma -e brcmsmac -e b43
```

Solved! Ironically, although I did many things, that was not one of them.  I am not 100% sure what was the winning combination of steps, but I think it was uninstalling all the bcm* packages and reinstalling these four:

bcmwl-kernel-source
firmware-b43-installer (NOT firmware-b43-lpphy-installer as suggested in one thread)
broadcom-sta-common
broadcom-sta-source

it looks as if these brought along a couple of other packages:

b43-fwcutter
diffstat
module-assistant
quilt

---

### Post by chili555 on 2012-04-28
Awesome! Glad it's working.

---

