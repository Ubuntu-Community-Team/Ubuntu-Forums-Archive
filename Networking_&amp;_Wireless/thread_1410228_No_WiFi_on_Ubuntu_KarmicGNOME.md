---
title: "No WiFi on Ubuntu Karmic/GNOME"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by elsalvadorbali on 2010-02-18
Hi there,

I managed to kill my wifi network somehow... :(
The wifi led of my Compaq 615 notebook shows a red wifi sign, which means that wifi is not active. Nothing happens when I press the button (normally it should turn blue).
When I click on the Network Connections icon, it shows only the LAN connections, nothing about wifi.

**My notebook has **
06:00.0 Network controller [0280]: **Broadcom Corporation BCM4312** 802.11b/g [14e4:4315] (rev 01)

**chipset**.

The whole thing happened after I installed some backport stuff with that I wanted to solve some sound problem.
After WiFi gone, I took it off, but I cannot heal WiFi ever since.

The Drivers (System/Administration) says that "this driver is activated but not in use".


Does anyone have any idea on how to solve this?


Thank you very much in advance!


SalvadorBalí

---

### Post by northd_tech on 2010-02-18
The 4312 is one of the older Broadcom WiFi interfaces and should be fairly easy to fix.  Does System > Administration > Hardware Drivers show yours as a "Broadcom STA wireless driver" or as a "b43" driver?

Either way, several people have mentioned going in there and clicking that Broadcom driver, then "Remove" to remove it.  Then reactivate the driver (yours should be the "b43" if I recall correctly).  You might need to reboot, and this often fixes the Broadcom driver.

Other people have mentioned needing to disconnect the ethernet cable (and possibly doing the Remove, Activate, reboot thing) to get the Broadcom working.

If you do a forum search here for "Broadcom 4312" you should find several threads about that wireless.

It might be helpful if you post the results of the following terminal commands either here (or on one of the relevant Broadcom 4312 threads here):

```
lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

edit:  Here is a link to a recent thread here about the Broadcom 4312 (which was fixed on that thread):

[http://ubuntuforums.org/showthread.php?t=1402769&page=3&highlight=Broadcom+4312](http://ubuntuforums.org/showthread.php?t=1402769&page=3&highlight=Broadcom+4312)

---

### Post by elsalvadorbali on 2010-02-19
Hi northd_tech!

Thank you for your help.
Yesterday evening I managed to get my WiFi work.
The solution was rather easy, but I had to do a huge research work to find this easy solution on the net. Well, that's also because I'm quite a novice in Ubuntu, so I do not exactly which command does what.

What helped me finally was this command:
sudo modprobe b43
 
This finally activated the driver.
Well, not exactly, because this made my WiFi led light up in blue, but after rebooting, the card did not work again.
BBUT, when I checked the drivers menu, I realized that a new driver appeared: the b43 - at the side of the broadcom. I removed the broadcom one, and activated the b43, and it worked!

Before this, I removed and re-installed several times the driver, but it always put back the broadcom's driver.
Maybe it could also be re-started somehow, but i did not find a solution for that. This is OK now.


Best regards,

SalvadorBalí

> **northd_tech said:**
> The 4312 is one of the older Broadcom WiFi interfaces and should be fairly easy to fix.  Does System > Administration > Hardware Drivers show yours as a "Broadcom STA wireless driver" or as a "b43" driver?

Either way, several people have mentioned going in there and clicking that Broadcom driver, then "Remove" to remove it.  Then reactivate the driver (yours should be the "b43" if I recall correctly).  You might need to reboot, and this often fixes the Broadcom driver.

Other people have mentioned needing to disconnect the ethernet cable (and possibly doing the Remove, Activate, reboot thing) to get the Broadcom working.

If you do a forum search here for "Broadcom 4312" you should find several threads about that wireless.

It might be helpful if you post the results of the following terminal commands either here (or on one of the relevant Broadcom 4312 threads here):

```
lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```edit:  Here is a link to a recent thread here about the Broadcom 4312 (which was fixed on that thread):

[http://ubuntuforums.org/showthread.php?t=1402769&page=3&highlight=Broadcom+4312](http://ubuntuforums.org/showthread.php?t=1402769&page=3&highlight=Broadcom+4312)

---

### Post by carlholmberg on 2010-02-22
I solved a similar problem on one of my students Compaq 615's by using Broadcoms STA-driver (installed through jockey) and adding the following to /etc/rc.local
rmmod ssb
modprobe wl

---

