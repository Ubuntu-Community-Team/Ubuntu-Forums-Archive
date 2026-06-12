---
title: "Can't get nvidia drivers to work."
date: 2010-10-23
forum: Mythbuntu
---

### Post by tonycollinet on 2010-10-23
I've tried both versions suggested by the proprietary drivers app, and tried downloading and installing from the nvidea website.

In all cases, after a reboot, I get a blank screen, and must boot into recovery mode to delete xorg.conf before I get everything back again.

This is after an upgrade to 10.10. 9.04 was no problem - but I used envy to install.

Card is a flavour of 9200 (probably ls or gs or similar cut down variant)

Ideas? (I need the tv out option)
Thanks

---

### Post by Wobblybob on 2010-10-23
Hi tonycollinet this [[COLOR="Blue"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9211609&postcount=35") got my nvidia drivers working after getting the driver from [[COLOR="Blue"]here[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us").

---

### Post by ian dobson on 2010-10-23
Hi,

Can you try backlisting the open source nv driver.

cat /etc/modprobe.d/nvidia-graphics-drivers.conf
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

The nouveau/lbm-nouveau
 modules are the opensource driver and the other 2 are old nvidia drivers.

I had the same problem that the nvidia driver wouldn't load until I removed the nouveau driver.

Regards
Ian Dobson

---

### Post by tonycollinet on 2010-10-24
> **Wobblybob said:**
> Hi tonycollinet this [[COLOR="Blue"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9211609&postcount=35") got my nvidia drivers working after getting the driver from [[COLOR="Blue"]here[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us").

Hi WB

I've read through that post - at one point he says something along the lines of "now can't get into terminal" - and then gives a list of terminal commands. How are these entered if you can't get into the terminal?


Thanks.

---

