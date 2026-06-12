---
title: "Internet Connection Sharing Help for a Newbie"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by Hayloe on 2009-03-08
Hello, I recently installed Ubuntu and have been trying to setup ICS with my Xbox 360 all day, I tried a bunch of random walkthroughs on the web and none worked, I actually messed up the system to where it wasnt connecting. I fixed all that with a fresh install of Ubuntu. and now im asking for your help! nobody in the IRC could help me.

First, about my situation

I'm trying to hookup my Xbox360 to my Laptop, to use Internet Connection Sharing, my Xbox is connected to my laptops ethernet card with a ethernet cable, and my Laptop is connected to the internet wirelessly, with a static IP

I tried to follow the instructions here:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

and followed the instructions all the way down to Client setup, where I stopped. and restarted my PC. then when it rebooted I tested the connection on my xbox using the following settings:

The settings I have on my Xbox (the client) are
IP: 192.168.0.2
Netmask: 255.255.255.0
Gateway: 192.168.0.1
DNS1: 4.2.2.1
DNS2: 4.2.2.2
(my DNS servers are from Verizon DSL)

the test failed report I got from the xbox said
Cannot connect to your network hardware using a static IP address.

I have been trying all day so if someone can help, I would be very appreciative.

again Im on a fresh install of Ubuntu.

---

### Post by Iowan on 2009-03-08
> **Hayloe said:**
> I'm trying to hookup my Xbox360 to my Laptop, to use Internet Connection Sharing, my Xbox is connected to my laptops ethernet card with a ethernet cable, and my Laptop is connected to the internet wirelessly, with a static IP What kind of ethernet cable?  *Ordinarily*, two machines connect directly with a crossover cable.

---

### Post by Hayloe on 2009-03-08
I believe its a plain Cat 5 cable, it came with the XBOX.

I had this working in Windows 7 Beta, I just enabled ICS on my adapter and it worked beautifully, so I don't believe the cable is the problem

---

### Post by Hayloe on 2009-03-08
Well I got it working now, Apparently restarting the PC erased the changes I made in terminal, I guess my next step would be to create a script that runs upon boot-up of Ubuntu, am I right?

EDIT: sorry about the double post =/

---

### Post by Iowan on 2009-03-08
It *shouldn't* _require_ a script - but finding the right config file to put it in seems to be getting trickier. The new Network Manager stores it's settings in /etc/NetworkManager -  */etc/NetworkManager/nm-system-settings.conf* in particular, but it also manages only one interface at a time.  There are some how-to's/workarounds available.  There are also rumblings that a recent update may have solved some of the issues.

---

