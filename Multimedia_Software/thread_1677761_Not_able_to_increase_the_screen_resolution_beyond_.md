---
title: "Not able to increase the screen resolution beyond 800x600 after upgrade to 10.10"
date: 2011-01-29
forum: Multimedia Software
---

### Post by visgupta1 on 2011-01-29
Hi,

I am using a 15" CRT Samsung monitor and when I upgraded 10.10, the screen resolution became 800x600 and I am not able to increase the resolution of it. This was working fine with 10.04 version.

Below is the o/p for "xrandr":
[I][COLOR=RoyalBlue]xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600         0.0* [/COLOR]
[/I]
I also see a continuous message box at the top left corner of my monitor with text as "Unknown".

Please let me know how to proceed on this. Or let me know if any further input is required from my side.

Regards,
visgupta1

---

### Post by sikander3786 on 2011-01-29
Welcome to the forums :-)

From Applications > Accessories > Terminal, please paste the output of these commands.

```
lspci | grep VGA
glxinfo | grep vendor
cat /etc/X11/xorg.conf
```

---

### Post by ajgreeny on 2011-01-29
Probably nothing to do with the monitor, but more likely the graphics card.  What make/model etc is that?

---

### Post by visgupta1 on 2011-01-31
Below is the o/p:

$$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
$$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Mesa Project
$$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
$$

---

### Post by visgupta1 on 2011-01-31
> **ajgreeny said:**
> Probably nothing to do with the monitor, but more likely the graphics card.  What make/model etc is that?

Sorry I am new to Ubuntu. Can you please tell me how to find this out?

---

### Post by sikander3786 on 2011-01-31
So, try ronfiguring your graphics and reboot to test if there is any improvement.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by visgupta1 on 2011-05-27
> **sikander3786 said:**
> So, try ronfiguring your graphics and reboot to test if there is any improvement.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
I tried this command but nothing changed after that. Still I cannot increase the resolution.

This was working fine with 10.04. Now I have upgraded to 11.04 and still the same issue.

---

### Post by 0coolDemo on 2011-08-03
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20110803154451

Receiving the above error by running the command mentioned above. 

I am using Samsung SyncMaster540N LCD monitor

---

