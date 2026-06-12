---
title: "Ubuntu freezes my Ethernet"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by Ordes on 2009-05-08
I have this problem, since always Ubu 8.04, 8.10, 9.04

Motherboard ASUS p5n32 sli e plus, 2* Nvidia Ethernet

----
When i suspend on ubu, my ethernet completely freezes (doenst work at all)
* Restart pc, still not working
* Disable eth in BIOS, restart, enable, restart, not working
* Even on my WinXP (dual boot) it doesnt work anymore (eth 1+2)

When this first happened, i thought i blew it. So i bought a D-Link eth. 
But when i made a new installation of WinXP i got curious, tried my Nvidia eth again, and it worked again. On both, Win and Ubu.

So after some testing i can confirm that.
* Everytime when i suspend on Ubu both of my Nvidia eth are not working anymore, no matter which OS i am running after
* Plugin plug out doesnt help
* Different BIOS settings dont have any affect,
e.g. Nvidia eth 1 enable, eth 2 disable, suspend, than eth 1 disable eth2 enable, etc 


The only thing that works is, plug in my Dlink eth. Restart, Shutdown, replug my Nvidia eth, 

Suspending Ubu on Dlink eth, no problems 
Suspending WinXP on Nvidia eth 1+2, no problems

---

### Post by Ordes on 2009-07-18
mhm... no one ever had this kind of problem?

or any idea

---

### Post by Ordes on 2010-01-24
...bump...

wondering that no one else encountered this problem with nforce eth

and the problem keeps continuing.. ubu 9.10

---

### Post by aleblanc on 2011-05-27
I think the reason you are getting those problems is that the ethernet IO resources conflict with the acpi IO resources (acpi handles suspend mode). Try "sudo dmesg | grep nForce" and you should see that the conflict is reported. To fix it you need to add a kernel option at bootup to disable strict enforcement of acpi resources: acpi_enforce_resources=no

Here is how I did this with grub2

 1) edit /etc/default/grub : sudo nano /etc/default/grub
 2) edit the GRUB_CMDLINE_LINUX option to include the above 
    mentioned kernel option:

     GRUB_CMDLINE_LINUX="acpi_enforce_resources=no"

 3) update grub2 : sudo update-grub2

For standard grub you will have to edit the /boot/grub/menu.lst file, specifically the lines starting with "linux", and then update grub with: sudo update-grub

After applying the above fix and rebooting check dmesg again (sudo dmesg | grep nForce) to see if the conflict is no longer reported. I found that this fixed the problem for me but only for one of my ethernet ports (which is all I need).

---

### Post by aleblanc on 2011-05-27
Have also just found (but not tried) the following fix, which looks better since it won't disable suspend mode: [http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427]("http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427")

---

