---
title: "ATI Driver issues. Everything is slow."
date: 2008-04-27
forum: Multimedia Software
---

### Post by NOLU on 2008-04-27
Since I've upgraded to 8.04, everything is very slow from the internet to simple folders opening up. All effects are off but it's still slow.

I have this info if it helps:

01:00.0 VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary)


Section "Device"
Identifier "Generic Video Card"
Driver "fglrx"
Busid "PCI:1:0:0"

Someone has got me as far as it being a possble driver issue bt I'm new to all this and I don't know where to go from here.

Any help would be appreciated.

---

### Post by ubuntu-freak on 2008-04-27
Seems to be quite a few problems with ATI in Hardy. Have you tried using ENVY? Remove any proprietary driver you installed already. File a bug report also, or confirm an existing one.
 
If all else fails, go back to Gutsy and wait for Hardy 8.04.1 (June).
 
Nathan

---

### Post by NOLU on 2008-04-27
I haven't tried ENVY although I don't know what it is.

---

### Post by ubuntu-freak on 2008-04-27
> **NOLU said:**
> I haven't tried ENVY although I don't know what it is.

 
Have you read the how-to on installing ATI drivers? It's in this very section of the forums, above the normal posts, it's a "Sticky Thread" and stays put.
 
Here is a link to the ENVY website:
 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
 
Nathan

---

### Post by NOLU on 2008-04-27
When I try to install Envy in terminal, I get this:

paul@paul-desktop:~$ sudo apt-get install envyng-gtk
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any idea's what this is or how to fix it?

---

### Post by ubuntu-freak on 2008-04-27
> **NOLU said:**
> When I try to install Envy in terminal, I get this:

paul@paul-desktop:~$ sudo apt-get install envyng-gtk
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any idea's what this is or how to fix it?

 
The Update Manager or Synaptic must have been running.
 
Nathan

---

