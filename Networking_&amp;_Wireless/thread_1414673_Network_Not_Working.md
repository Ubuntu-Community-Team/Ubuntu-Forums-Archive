---
title: "Network Not Working"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by wagb278 on 2010-02-23
I need help to figure out were to start to fix my networking which just stopped working. I have Ubuntu 8.04 and all was working fine until I plugged in a USB memory stick. The first symptom was that the mouse locked up.

I cannot ping the Ubuntu box from from other nodes on the LAN and the other nodes all work fine - other than not connecting to this Ubuntu box. 

It appears that the Network service is not running. When I go to Admin >> Network Settings there is no entry in the Connections tab for Wired Connection. All that is there is Point to Point (modem) which I don't use. 

ifconfig indicates that loopback is running. But I expected to see something about Ethernet, like I do on another Ubuntu box.

When I perform lspci I do not see an entry for Ethernet Controller. 

When I perform sudo /etc/init.d/networking restart - 
I receive "ERROR getting interface flags: no such device" and the message: Failed to bring up eth0.

Without a network connection I cannot reinstall - if I know what to install.

Thanks in advance for any tips

---

### Post by theozzlives on 2010-02-23
Is your network card integrated? If so, is it enabled in the CMOS?

---

### Post by wagb278 on 2010-02-23
> **theozzlives said:**
> Is your network card integrated? If so, is it enabled in the CMOS?

BIOS says "On-board LAN" is set to Enable

---

### Post by theozzlives on 2010-02-23
Do you have a NIC you can try?

---

### Post by wagb278 on 2010-02-23
> **theozzlives said:**
> Do you have a NIC you can try?

No. 

I think the Ethernet driver is not running.

I performed a lsmod | grep 'e1000' and get no results. I remember when I got this machine there was no built-in driver for the Intel Ethernet port and that I had to install it as a mod. The one that worked was either "e1000" from Intel or "igb" from *someone*.  I don't remember which mod worked.

lsmod |grep 'igb' returns no entries either - so whichever one should be running is not.

I looked in the system log to see if there was a message that it tried to load some mod or driver and failed but I cannot find any message about Ethernet. How do I search the logs to find boot errors?

Thanks

I will try to remember how to install the dri

---

### Post by wagb278 on 2010-02-24
The network magically started working! 

While investigating the problem I booted Live CDs for Ubuntu 8.04 64-bit and 32-bit and had no network on either. 

There was a kernel update on 27 Jan (a month ago) so I was getting ready to recompile the e1000 driver and noticed that the network was working. 

I suspect that for some reason the Mod for the eth0 driver was not getting invoked.  Just keep rebooting until it does is my only suggesting to others.

Strange!
If any one has any other ideas I welcome comments.

---

