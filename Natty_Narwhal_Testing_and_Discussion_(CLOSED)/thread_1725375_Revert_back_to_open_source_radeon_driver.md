---
title: "Revert back to open source radeon driver"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Arkantos on 2011-04-09
Hi. I installed fglrx (catalyst) driver. I followed these steps to install fglrx driver.

[http://ubuntuforums.org/showpost.php?p=10618166&postcount=1](http://ubuntuforums.org/showpost.php?p=10618166&postcount=1)

But even after removing fglrx driver it seems X tries to load fglrx module:

**[COLOR="Green"]$ cat /var/log/Xorg.0.log | grep EE[/COLOR]**

> 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    36.933] (II) Loading extension MIT-SCREEN-SAVER
[    36.942] (EE) Failed to load module "fglrx" (module does not exist, 0)

Any ideas to fix it. Thanks..

---

### Post by lucazade on 2011-04-09
> **Arkantos said:**
> Hi. I installed fglrx (catalyst) driver. I followed these steps to install fglrx driver.

[http://ubuntuforums.org/showpost.php?p=10618166&postcount=1](http://ubuntuforums.org/showpost.php?p=10618166&postcount=1)

But even after removing fglrx driver it seems X tries to load fglrx module:

**[COLOR="Green"]$ cat /var/log/Xorg.0.log | grep EE[/COLOR]**



Any ideas to fix it. Thanks..

is "/etc/X11/xorg.conf" file present?
because OSS ati driver doesn't need it, only fglrx (and other closed drivers) needs it.

---

### Post by coffeecat on 2011-04-09
Apart from removing xorg.conf you might need to do what is described here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by PCNetSpec on 2011-04-09
Could it be this line:

**sudo update-alternatives --config gl_conf (and select the line with fglrx)**

in the instructions you followed that is causing the problem.

**update-alternatives** has probably set the **gl_conf** entry to "Manual".

Install the **galternatives** package (a GUI front end for update-alternatives), and use it set the gl_conf entry back to "Auto"... and select something other than fglrx

My gl_conf entry is set to:

Status: Auto
Choice: *
Priority: 500
Options: /usr/lib/mesa/ld.so.conf

and that is the only entry.

if that helps.

---

### Post by Arkantos on 2011-04-09
> **lucazade said:**
> is "/etc/X11/xorg.conf" file present?


No there isn't any xorg.conf. In fact I removed it after removing fglrx driver :)

> **PCNetSpec said:**
> Could it be this line:

**update-alternatives** has probably set the **gl_conf** entry to "Manual".


Also my gl_conf entry is set to "Auto".

I am not sure but may be:

**[COLOR="Green"]sudo update-initramfs -u[/COLOR]**

This command installed fglrx module. And I don't know how to revert back to original.

Thanks for all replies. I upgraded Natty from Maverick. I'll do a fresh install and test again.

---

