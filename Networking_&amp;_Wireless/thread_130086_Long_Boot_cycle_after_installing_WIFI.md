---
title: "Long Boot cycle after installing WIFI"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by USA1 on 2006-02-15
Hello all,

Compaq V2000.

When I first installed ubuntu on the maching neither the WIFI nor the ATI video card were working properly, but the machine was able to boot Ubuntu quite quickly.

Now that I have setup both of the above correctly, the machine takes about 5 minutes to boot up.  It slows down right around where it is detecting all the network devices.

Also, If turn the WIFE with the keybard on/off button, Ubuntu won't boot.

How can I disable it from trying to configure/detect the network at boot.
It would be great if it could boot quickly and then once it is booted, I can choose to set the network if I want to.  Which configuration files do I have to alter to help it boot a bit quicker.

Also, I do I fix the boot menu, I do not want to ubuntu to be the default and I want to change the time to wait longer because booting to a default option.
Again which configuration file do I have to edit to resolve this boot menu issue.

Thanks in advance.

USA1

---

### Post by spd106 on 2006-02-15
You should be able to disable the interfaces through network-admin. Click on properties and disable. You will have to reverse this process on startup.

Perhaps have a at initng, do a search in the howto section for a guide.

Lastly, edit the /boot/grub/menu.lst file as root. It's fairly well documented, just remember to count the menu entries from zero. Failing that cut and paste the windows entry to the top of the list.

---

### Post by USA1 on 2006-02-15
[QUOTE=spd106]You should be able to disable the interfaces through network-admin. Click on properties and disable. You will have to reverse this process on startup.

Perhaps have a at initng, do a search in the howto section for a guide.

Lastly, edit the /boot/grub/menu.lst file as root. It's fairly well documented, just remember to count the menu entries from zero. Failing that cut and paste the windows entry to the top of the list.[/QUOTE]


Yes I can disable it from the network manager for the duration of that session.
As soon as you reboot, something in the system reactivate all the connections again.
I can image that it must be looking for a connection on the ETH0 an not finding none and that is what is getting it stuck.

It get stuck at the point where it is configuring network interfaces
network interfaces up

---

### Post by spd106 on 2006-02-17
There's some info [here]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsCompaq#head-fca815c650938cd6219bb955a11584614cbc8f6b")
But it might not be very useful.
I'm not sure what else to suggest. Could you give some more details as to how you set up the wifi card.

---

