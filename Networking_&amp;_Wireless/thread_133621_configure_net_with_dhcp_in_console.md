---
title: "configure net with dhcp in console"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by devilpaco on 2006-02-20
Well I  have a problem trying to configure internet access in Breezy Budger, I'll try to explain as much as I can my problem.

I have a pentium 166mhz very old and I wanted to install ubuntu on it, but the problem is that I can't boot from cd, so I decided to take the HD an put it on a machine that can, I run the "server" installation on that machine (AMD K7 500mhz) and everything was ok, then when the installer asked me to reboot and finish the installation, I retourned the HD to the pentium 166 an finished the installation there, there's no problem with nothing except when says, "Synchronizing clock to ntp.ubuntulinux.org... Wrror : Temporary failure in name resolution" so I supposed that I have no internet.

I tried ifconfig to reconfigure eth0 but I don't really know how to do it in console and I've not found any about it. I have another Ubuntu machine running well with internet, it accesses with DHCP.

Thankyou and sorry about my english.

devipaco

---

### Post by knalle on 2006-02-20
see if dhclient3 is running

---

### Post by devilpaco on 2006-02-22
I've not seen dhclient3 running, how can I run it??

thankyou very much

---

### Post by fm1234 on 2006-02-22
I assume you've checked dhclient3 is not running by issuing something like 

ps aux | grep dhcl

To make it work, got to menu System, then Administration, then Networking.

In there, select your network interface (usually, eth0) and look for its properties. Then you'll have the option of configuring this network interface with DHCP.

Cheers,
Fernando

---

### Post by jamesr on 2006-02-22
Check if the network card is being seen during the boot up process.

post the appropriate part of dmesg.

Since this is a 166 P1 is the nic ISA or PC?

Post the output of 

sudo ifconfig -a

---

