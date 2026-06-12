---
title: "Error: &quot;Permission Denied&quot; trying to install WG311v3 using Ndiswrapper"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by mulluysavage on 2009-02-20
I was able to install the wrong driver yesterday, without permissions problems. Now I can neither remove the wrong driver nor install the new driver - permission denied. What do I do?

---

### Post by mulluysavage on 2009-02-20
I wasn't using sudo... sorry!

---

### Post by abyssius on 2009-02-20
> **mulluysavage said:**
> I was able to install the wrong driver yesterday, without permissions problems. Now I can neither remove the wrong driver nor install the new driver - permission denied. What do I do?

You probably need to be root. Open a terminal, enter your commands using 'sudo'.
```
sudo ndiswrapper -r *<old_driver_name>*
```
To remove old driver. Then, you can load the new driver:
```
sudo ndiswrapper -i *<new_driver_name>*
```
Finally:
```
sudo ndiswrapper -l
```
To make sure the new driver loaded

---

### Post by mulluysavage on 2009-02-20
okay, when I try to install I get

couldn't open wg311v3.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.

but then it shows that it's installed when I go ndiswrapper -l.

---

### Post by mulluysavage on 2009-02-20
...and upon ndiswrapper -l it says "wg311v3" invalid driver!

---

### Post by abyssius on 2009-02-20
Apparently, WG311v3 isn't the correct driver for your adapter. You'll have to remove it and install a driver that doesn't generate the 'invalid driver!' error message. You must get 'device present' for the driver to work properly. For example:

```
desktop:~$ ndiswrapper -l
wusb54gv2 : driver installed
	device (13B1:000A) present 
```

Have you tried ndisgtk? This is the ndiswrapper GUI. It makes things rather simple. If you haven't, you can install it via:
```
sudo apt-get install ndisgtk
```
This adds the menu item, {Windows Wireless Drivers} to your System menu. It will allow you to graphically install/uninstall windows drivers and further configure your interface.

---

### Post by sailthesea on 2009-02-20
You may want to try this link that I was shown to when having problems with Netgear, It worked a treat for me. 


The problem seemed to be finding the specific driver for the hardware Ubuntu will recognize it on its own but doesn't seem to configure correctly.
Hope this helps 

Good Luck!

---

### Post by sailthesea on 2009-02-20
OK should be right this time, sorry

[http://ubuntuforums.org/showthread.php?p=6759228#post6759228](http://ubuntuforums.org/showthread.php?p=6759228#post6759228)

---

