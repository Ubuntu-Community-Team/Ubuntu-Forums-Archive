---
title: "How to enable Ethernet?"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by 1erika on 2009-11-22
Hi!
After having used Ubuntu 9.10 Karmic for 2 weeks (first in my life I use Linux) I found a problem with Ethernet connection. I have read a lot of forums both Russian and English. 
Some things I understand:

[LIST]
[*]find out whether Ethernet is enable in PC using command ```
lspci | grep eth
``` - there were no answer. So that's why I decided that Ethernet controller is disable at all
[*]try to use another command (just to be sure that controller is disable) ```
sudo ifconfig eth0 up
``` - the answer was "....No such device"
[*]in BIOS check boot settings - especially "onBoard LAN Boot ROM" - it's enabled
[*]Windows is guileful - I have found one Russian blog about Ubuntu where I've read that Windows has an option which disable Ethernet controller after shutting down the PC
[/LIST]
So. What is my question :)
My laptop is ASUS Eee PC 1005HA (very new). And I've installed Ubuntu after removing XP. So that's why in device manager I can't disable **Wake-on-lan after shutdown**. And I don't have XP version and don't want to install it at all. 
**Is there any other solution to the problem with disabled Ethernet controller?**


Thank you.
P.S.: Sorry for my poor English :(

---

### Post by Iowan on 2009-11-22
Your English is fine...
Another command to use is **lshw -C network** - that should (maybe) give an indication of chipset.

---

### Post by 1erika on 2009-11-22
I have a lot of problem with times :)
So, about this command.
My netbook write smth like this:

      1. different settings of Wireless Network Adapter (it's disable now so that's why ```

*- network DISABLED
      description: Wireless interface
...        
 
```So here everything is ok. But next 
```

*-network 
description: Ethernet interface
product: Atheros AR8132 / L1c Gigabit Ethernet Adapter

```Yeaaah. Now I have the info about Ethernet controller from terminal
But all other lines don't tell me anything about why there is no Ethernet controller (or if it is disable)
Some info about capabilities, configuration and resources.
Next
```

*-network DISABLED
    descr...
    physical id: 1
    logical name: vboxnet0
   serial: 0a:00:27:00:00:00
   capabilities: ethernet physical
    configuration: broadcat = yes multicast=yes

```

---

### Post by Iowan on 2009-11-22
**vboxnet0** is not something I understand - does it show up in **ifconfig -a**?

---

### Post by 1erika on 2009-11-22
Hm... I don't now why, but now it works. I plug out and in a cable and Ubuntu find a connection...
Thanks a lot for your help!!
And also thanks for different commands in terminal :)

---

### Post by SteveHillier on 2009-11-22
> **1erika said:**
> My laptop is ASUS Eee PC 1005HA (very new). 

The bit here that I don't like is the 'very new' bit.  It could be that there are no drivers for your ethernet card currently being shipped.  This is sometimes a problem.

Just as background I have in the last year set up two Linux web servers, both of which were 'latest' models.  In both of these I had no network ability until I installed a very old network adapter.  This was required for both Ubuntu and Fedora OS.  

This is unlikely to be an option for you.

You could also try running the following command in terminal 

```
lshw -class network
```

which should give you the name of the adapter on your machine then search the forum for that adapter or post the output from that back here.

---

