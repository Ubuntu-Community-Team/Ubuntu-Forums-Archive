---
title: "Narwahl alpha 3 not running"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by TheManno1 on 2011-04-24
I upgraded from ubuntu 10.10. It only runs in safe mode and does not have internet in safe mode currently writing this in window vista.

---

### Post by TheManno1 on 2011-04-24
Emergency

---

### Post by andrewthomas on 2011-04-24
are you trying for a unity session?

have you tried to select the classic gnome from gdm?

---

### Post by TheManno1 on 2011-04-24
haVE TRIED CLASSIC NO EFFECTS

---

### Post by TheManno1 on 2011-04-24
> **andrewthomas said:**
> are you trying for a unity session?

have you tried to select the classic gnome from gdm?

 WHAT i UPGRADED

---

### Post by TheManno1 on 2011-04-24
Can't i fix it through recovery console.

---

### Post by andrewthomas on 2011-04-24
What video card do you have?

What driver are you using?

---

### Post by TheManno1 on 2011-04-24
acer aspire  5742-7653

---

### Post by andrewthomas on 2011-04-24
> **TheManno1 said:**
> acer aspire  5742-7653

I assume that you have Intel integrated graphics, no?

---

### Post by samacaster on 2011-04-24
Did you fresh install or upgrade using the update manager?

---

### Post by TheManno1 on 2011-04-24
Get Ubuntu 11.04 Upgrading from Ubuntu 10.10   To upgrade from Ubuntu 10.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '11.04' is available. Click Upgrade and follow the on-screen instructions.     To upgrade from Ubuntu 10.10 on a server system: install the update-manager-core package if it is not already installed; launch the upgrade tool with the command sudo do-release-upgrade -d; and follow the on-screen instructions. Note that the server upgrade is now more robust and will utilize GNU screen and automatically re-attach in case of e.g. dropped connection problems.

---

### Post by rosencrantz on 2011-04-24
How and why did you get alpha 3 when beta 2 is already out?

---

### Post by TheManno1 on 2011-04-24
I didn't know

---

### Post by TheManno1 on 2011-04-24
Probably through google

---

### Post by rosencrantz on 2011-04-24
OK, I see your problem - without network no upgrade. 
Try downloading the alternate installer CD 
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
and using that as an offline repository.
Edit: I think the CD has an upgrade option in the main menu. Might still require network, though (if you have non-standard packages), so let's hope the CD recognises your network adapter.

---

### Post by TheManno1 on 2011-04-24
wi]ouldn't that delete my files there is no windows in the computer I am installling

---

### Post by lisati on 2011-04-24
*Thread moved to **Natty Narwhal Testing and Discussion**.*

---

### Post by rosencrantz on 2011-04-24
If it does a true upgrade, it shouldn't delete any personal files.
Check this thread:
> **Partyboi2 said:**
> You should be able to upgrade with the alternate cd without a internet connection.
> 
Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet. 
Download and burn the alternate installation CD.
Insert it into your CD-ROM drive.
A dialog will be displayed offering you the opportunity to upgrade using that CD.
Follow the on-screen instructions.
If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 
gksu "sh /cdrom/cdromupgrade"

I'd try getting important personal files off the disk somehow beforehand, if I were you, though. If USB doesn't work in safe mode, you could try sticking the hard drive in a desktop or laptop, booting from a live linux and copying to an external disk.

---

### Post by rosencrantz on 2011-04-24
Also, in case you screw up your system beyond recoverability, back up your package selections with 
dpkg --get-selections > somelogfile.txt and back that file up in your home directory.
It will help you to recover all extra package selections after a clean re-install.

---

### Post by TheManno1 on 2011-04-24
it is stuck at 50 percent

---

### Post by TheManno1 on 2011-04-24
on resizing partiton

---

### Post by rosencrantz on 2011-04-24
> **TheManno1 said:**
> it is stuck at 50 percent

what is?

---

### Post by rosencrantz on 2011-04-24
OK ... that's ... bad ...
Did you *have* to resize?

---

### Post by TheManno1 on 2011-04-24
I am just resusing partition now.

---

