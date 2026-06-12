---
title: "Wired connection to Linksys"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by farfromapro on 2009-02-15
New install 8.10 (kernel 2.6.27-7-generic)
Old machine (Dell dimension XPS T500)

The ubuntu machine is plugged into a linksys router but will not connect.  The linksys does have security enabled (WPA).  I attempted a manual IPv4 setting using some address (192.168.1.??), netmask, and gateway.  Didn't work

the ifconfig shows all 0's for eth0

I'm not sure if the card is recognized by ubuntu.

Any advice / first steps?

in the network toos when i set the device to eth0 no IP information or interface information is available.

Any suggestions?

Thanks!

---

### Post by dmizer on 2009-02-16
I'm confused, you indicate that Ubuntu is "plugged into" your linksys router, but then you mention WPA which is a wireless security protocol. Is your Ubuntu computer wireless or wired?

Either way, please post the output of:
```
lshw -C network
```

---

### Post by farfromapro on 2009-02-16
Thank you for the reply... The computer is wired; Sorry for the confusion on the wireless security (forget I typed it)...

This is the response from the command:

~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 3c900B-TPO Etherlink XL [Cyclone]
       vendor: 3Com Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 04
       serial: 00:50:da:11:a6:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=80 maxlatency=48 mingnt=10 module=3c59x multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:00:c7:62:f8:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

My etc/networking/interfaces file only has an auto lo line in it.. nothing regarding eth0 (not sure if it should or shouldn't).

The response from the command you asked me to run says the network is DISABLED (I'll attempt to enable it after work).

I ran an "ifconfig eth0" and no MAC or IP address showed up.  Yesterday I ran some code that assigned a static ip and added a mac address, which did show up in the ifconfig eth0, but even then I had no internet access.

What should I try next?

Thanks!

how do I make the paste of my code show up in cool scroll window like everyone else?

---

### Post by dmizer on 2009-02-16
You can use the bbc code markup tags like so: [noparse]```
long terminal output
```[/noparse]. This is not just "cool", it's important to do this because it retains formatting. :)

Is your linksys router configured for static IP?

---

### Post by farfromapro on 2009-02-16
I don't believe so.  I'm a little confused on setting that up on the linksys (looked at it for 30 seconds).  It seems like I can only add 4 static ip's but I have 5 computers (I guess it would automatically assing an ip to the 5th?).  I also don't see an option to assign an ip to a specific MAC address.  I'll spend more than a half a minute on later on tonight.

It sounds like I should setup static IP on the router and then set that up on the ubuntu box.  I just need to do that without messing up the XP machines.  I won't have a chance to get to it until later tonight.

I'll update then

Thanks!

---

### Post by dmizer on 2009-02-16
Sorry ... maybe I'm missing something, but if your router is not configured with static IP, then why are you trying to configure Ubuntu with a static IP?

Just try deleting whatever static IP settings you have configured in Ubuntu, and set it up for "automatic configuration DHCP" instead.

---

### Post by farfromapro on 2009-02-16
the automatic doesn't seem to be working.  Thats the default for ubuntu right?
Do you have a suggestion on how I can ensure the automatic DHCP is set properly?

Your not missing anything; I'm a noob so any information I give out is suspect!

If I understand networking properly, which i don't, (haha) the router may not have to be setup to deal with static IPs as long as the client is asking for an IP that is within the limits of the routers routing table and not assigned to another machine.  So I think I can just work with the client and leave the router along right?

Thanks for sticking with me on this!!!!  I appreciate it...

Getting onto the net with the box will make life alot easier!

---

### Post by dmizer on 2009-02-16
On the command line, try typing this:
```
sudo dhclient eth0
```

If that gets you connected, then it will be much easier to make things automatic.

---

### Post by farfromapro on 2009-02-16
I'm on line with my Ubuntu computer!!!!!

Thanks for helping

It was a bad ethernet card... The comp HAD 2... I was plugging into a dead one... 

Now I'm on line, time to get into some real trouble!!

Thanks for your help!

---

### Post by dmizer on 2009-02-16
HA! Sometimes it's the simple stuff that drives you nuts! :)

Glad you got it working!

---

