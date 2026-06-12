---
title: "Natty beta2 alternate CD cli install broken? (Or problem with the virtual machine?)"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by LarsKongo on 2011-04-24
(If this post fits best in the Virtualization forum, then move it there please.) 
I'm trying to install Natty Narwhal with the Alternate CD (32bit) with a Command Line Interface-installation in VirtualBox 4.0.6. (Note: Same problem below happened in 4.0.4.) I'm on a Windows 7 x64 host.

Install works fine up until it's time to boot up the virtual machine. I get as far as the default text plymoth... but then it's time for the Blinking Cursor of Death, and I can't input any commands at all. VBox isn't showing any HDD activity, and forcing a reboot in VBox doesn't help, it even stops displaying the BCoD. Maverick CLI install works fine.

Has anyone else had the same problem? Or is this problem related to VirtualBox?

---

### Post by Ichtyandr on 2011-04-24
I did two "real" alternate installs with natty beta, one xubuntu (32-bit) and one regular gnome (64bit) both went flawless. But never tried to do cli install. this sounds like vbox issue

---

### Post by Hedgehog1 on 2011-04-25
If you are installing Natty inside Virtual Box, you will need to load the new 4.0.6 version (released a few days ago) and update the Guest Additions in the guest OS.

***The Hedge***

:KS

---

### Post by LarsKongo on 2011-04-25
Well. Problem solved. *"and I can't input any commands at all"* seemed to be wrong. :p I could switch tty. Somehow tty7 only displayed the blinking cursor of death.

---

