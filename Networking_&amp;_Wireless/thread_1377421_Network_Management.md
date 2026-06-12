---
title: "Network Management"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by michellez on 2010-01-10
Hi,

Situation:
I'm running Ubuntu 9.04 on an Asus EEE 901. I am going to be running this as a mail server and web server (light usage!). As I will only be connecting in by SSH I want to be able to manage the network connections via the terminal/command line.
I am using primarily the wired interface but want to have the wireless connected as well incase (WPA encryption).

Am I missing something when I can not find config files for nm-applet? What's my best way of doing this?

Advice appreciated :)

Thanks,
Michelle

---

### Post by michellez on 2010-01-10
BTW, I'm wanting to assign static IPs manually with ths.

---

### Post by michellez on 2010-01-14
Any ideas guys? The other problem I've realised as well is that if I reboot the thing remotely via SSH, I've got to get in front of the laptop and actually log it on in Gnome before the wireless connects! :(

Thanks
Shell

---

### Post by Iowan on 2010-01-14
The logon thing is a Network Manager "feature". If you want the connection active on boot-up, you probably need to edit the interface details into */etc/network/interfaces*. What kind of static address assignment will you do?

---

### Post by michellez on 2010-01-15
I tried setting it up in the /etc/network/interfaces file - just the wired eth0 to start with but could not get it working. Set it up as per plenty of examples I could find for a static IP. Did /etc/init.d/networking restart - no change. Rebooted it - then it didn't work at all! :(

---

### Post by Iowan on 2010-01-15
Post your */etc/network/interfaces* file. Also, post results of **ifconfig -a** - it's possible the network is configured, but something else is amiss...

---

