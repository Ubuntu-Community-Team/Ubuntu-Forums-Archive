---
title: "How to get 9.04 to recognize new ethernet card post install"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by jvin248 on 2009-07-16
I have a new install of 9.04 Server and I replaced the ethernet card and only the loop-back interface is 'active' (127.0.0.0).  Lspci correctly lists the card, and etc/network/interfaces file has listing for 'eth0'. ifup eth0 returns errors.

Actually, I moved the HDD from the install machine to one that cannot boot from CD (yeah, it's old but low power and noise) to do an install. After reboot on the noCD machine, everything worked except the ethernet card. I tried several ethernet cards with reboots and nothing other than loopback on 'ifconfig'.  When I pulled the ethernet card from the original host machine and put it in the noCD machine, the noCD machine now works.

Obviously there is a setting in some file somewhere on the server that locks the ethernet interface activities to a specific card (maybe MAC address?).

How to find that file and change the setting to allow a new ethernet card?

Is there a way to get Ubuntu to re-auto discover ethernet cards?

---

### Post by martinbaselier on 2009-07-16
/etc/network/interfaces Is only used, if networkmanager is not used. 

Open a terminal and enter the following:
**sudo lspci -v -s xx:xx.x**
Replace xx:xx.x is the number of the card, you can find it by first running lspci without options.

On the verbose page, it should show the Kernel modules and driver in use.

Is that part working?

If not, try using google to find which kernel modules you need for the specific card and use **modprobe MODULENAME** to load the module with MODULENAME.

Now the card should be working. Please check and if so, add it to the list, so it will load automatically.
sudo gedit /etc/modules
Just add you modulename on the bottom of the file and save and close the file. 

Now try connecting with networkmanager. Please post if it works or not and when it does not work, the problems you encountered.

---

