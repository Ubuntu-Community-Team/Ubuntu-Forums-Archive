---
title: "Lan Driver Conflict in Ubuntu 8.10"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by unrevealed01 on 2009-03-09
hi there guys,

I was having trouble with Ubuntu 8.10 Realtek RTL8169. Then i was able to solve the problem by installing the latest RTL8168 lan from Realtek. After reboot 2 LAN driver cause conflict.

sudo lsmod | grep r81*

revealed 2 lan driver exists. r8169 and r8168 .

 i have tried to black by gedit etc/modprobe.d/blacklist

I have also used sudo rmmod r8169 after reboot the 2 lan drivers still runs. then i have uninstalled both of the drivers. After reboot both of the drivers still runs.

There are 2 things that runs on my mind one is to edit /etc/rc.local file. How to edit the rc.local file to make sure that r8169 never runs again and renaming the r8169 LAN driver. Please show how to solve this problem.

---

### Post by unrevealed01 on 2009-03-10
For those who have r8169 lan issue black listing and updating with proper driver can solve the problem. I have managed to solve the problem. Below are the steps

Blacklist the R8169

gedit etc/modprobe.d/blacklist

Add
sudo blacklist r8169

*important to update the list or else Ubuntu 8.10 won't blacklist r8169.
 update command

sudo update-initramfs -k all -u  


remove the default LAN driver which is built-in kernel.

rmmod r8169

then download the latest version of r8168 driver from Realtek. i have managed to get the latest driver from Realtek which is r8168-8.011.00.tar. this driver works perfectly.

install the latest driver

You are ready to use the LAN device

*Blacklist and Update very important

:popcorn:

---

### Post by kowala on 2009-03-10
Sir,

I seem to be having a similar issue to what you describe.  Though I am a 15+ year Windows tech this is my first experience with Linux.  I have a Abit IP35 Pro motherboard with two matching RTL8110SC integrated NIC cards.

On a fresh install of Ubuntu both NIC cards recognize and use the r8169 driver yet I have no network connectivity.  I can see both cards in the Network Manager.  Both cards and any "wired connections" I create remain greyed out on the Network Manager l-click selection list.  I have followed instructions on setting up a static ip address by editing the interfaces and resolv files to no avail.  I assume this is driver related as my router recognizes an active NIC during boot up.  Once Ubuntu is loaded the router does not recognize the NIC.

I also tried your solution of black listing the 8169 driver and installing the 8168 driver.  Oddly the 8169 driver reappears after a reboot and I do not see the 8168 driver.

I have spent a few days now beating my head against this wall.  I am open to any suggestions if you can shed light on the situation.

Thank you,

Kowala

---

### Post by unrevealed01 on 2009-05-14
have you solved the issue?

---

