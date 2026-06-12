---
title: "Can't locate network card"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by dracule on 2009-09-11
Hello,

I have a system set up like this in windows:

ethernet (in) -> built in ethernet jack -> computer -> shared connection with 3rd party etherent card -> laptop

the 3rd party ethernet is just a radioshack PCI one from about 5 years ago.

Anyways, in Ubuntu.. I cant find it at all. in lspci, or in my network connections. It simply seems to not exist. 


Any help figuring out what is going on?

EDIT: using ifconfig -a

i get another interface called "pan0" which appears to be my card... I never heard anything about the naming scheme including somethign called "pan0"

---

### Post by anubhavrocks on 2009-09-11
Can you post the output of
sudo lshw -c network

---

### Post by dracule on 2009-09-12
> phun@ubuntu:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:64:2b:32:f7:ae
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


on the card it says it is a realtek 8139D so i tried modprob 8139too, but it didnt work. 

Currently i am just using the built in ethernet to get internet to my computer. I just booted into windows and the card is working fine.

Im on 64bit btw.

---

### Post by anubhavrocks on 2009-09-12
Can you try plugging the card to a different PCI slot and post the output of 
dmesg

---

### Post by dracule on 2009-09-12
what? while it is running? because i thought that was unsafe so i just tried it when it was turned off.
and dmesg is super long so i dont know if i should post it here

---

### Post by dracule on 2009-09-12
I tried it anyways and got this as my newest entry: > [36974.700012] npviewer.bin[2579]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ffa8b60c error 14

---

### Post by dracule on 2009-09-12
bump, this is VERY important.

---

### Post by cariboo on 2009-09-13
You did shut down before moving the nic?

---

### Post by dracule on 2009-09-13
Yes

---

### Post by anubhavrocks on 2009-09-13
One of the first things that needs to work is that the kernel should be able to see your PCI device.
Since lspci is somehow not listing the device.Something is obviously wrong.Can you check in windows device manager and find the device id/vendor id and then try 
lspci -nn 

You should look for the device with same vendor/device id.

---

