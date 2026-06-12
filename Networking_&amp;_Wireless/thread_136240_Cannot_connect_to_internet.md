---
title: "Cannot connect to internet"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by chrisjs162216 on 2006-02-25
I have a Dell Dimention XPS R400 desktop and stuck 5.04 on it since Windows stopped working on it.  I was going to use a wireless card, but it didn't reconize is so I figured I would put the ethernet card in it (Intel Pro/100) and update to Breezy.  However, once I go to System>Administration>Networking and enable eth0, it acts like it isn't connected.  I can't update Synaptic Package Manager, ping my router or anything.  Pinging 192.168.1.1 (router) simply says:

root@ubuntu:/home/jack # ping 192.168.1.1
connect: Network is unreachable.

Since I'm still new to linux, I don't really know what to do.  Any suggestions?

---

### Post by bscbrit on 2006-02-25
Have you installed the drivers for the ethernet card?

---

### Post by procras on 2006-02-25
1) When the machine boots look for messages regarding network interfaces identified.
$ dmesg | less
or
$ dmesg | grep eth

2) Check that you have a module loaded for that network card
$ lsmod | grep <INSERT MODULE NAME HERE>

3) You can look at the output from syslog when you load and unload the relevant module
In one terminal type
$ sudo -s
Respond with your password
$ tail -f /var/log/syslog

In another terminal type
$ sudo modprobe <MODULENAME>
or 
$ sudo rmmod <MODULENAME>

I fancy that the module you are looking for might be eepro100 from a google search. This is found on my system
$ locate eepro100.ko
/lib/modules/2.6.12-10-amd64-generic/kernel/drivers/net/eepro100.ko

4) Configure your network with the tools System->Administration->Networking
or do it the old fashioned way (for testing and fun)
$ sudo -s
Respond with password
$ ifconfig
Shows a list of interfaces eth0 should be there if you have loaded the module
$ ifconfig IPADDRESS eth0
Set the IPADDRESS statically for the interface
$ route add default gw GWADDRESS eth0
To add the default route for the gateway (eg. your router/ADSL modem)

---

### Post by chrisjs162216 on 2006-04-16
Wow, I've been using Ubuntu non-stop for a little over a month and already know a lot :)  A simple upgrade to Breezy fixed it.  I wasn't going to mess with an old distro anyway.  Now if only Dapper had a working version of NDISWrapper...

---

