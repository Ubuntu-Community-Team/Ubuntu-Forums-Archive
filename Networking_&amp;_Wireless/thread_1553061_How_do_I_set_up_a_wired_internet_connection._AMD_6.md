---
title: "How do I set up a wired internet connection. AMD 64bit ubuntu 10.04"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by TaoBoogie on 2010-08-14
I have had the exact same set up 10.04 on the same machine connecting to the net with no problems. I had upgraded from an earlier version.
This time with a fresh install from disk the network manager does not see any connections. How can I get the manager to recognise the network and connect to the net?
I realise that it would help if I posted up the output of some commands in a terminal but I am writing this on my phone and can not cut and paste large chunks of text. I can only hope for some advice until I can get to a computer with a working connection.
Ubuntu 10.04  AMD dual core 64 bit with wired 10 meg broadband.
How can I get the network manager to see the connection
How can I find the MAC address? 
Cheers.

---

### Post by Iowan on 2010-08-14
From a terminal (Applications>Accessories>Terminal), **lshw -C network** should provide information about your interface(s). **ip link** is another way to find the MAC address.

---

### Post by TaoBoogie on 2010-08-14
Thanks
I tried (lshw -C network) 
The response from the terminal was I should run this programme as "super user" So thinking this may mean that I have to add sudo I tried that with no response. The terminal went back to it's normal display.
Tried iplink
Got "command not found"

When I go to the network manager icon and alt click I can get an option to "Edit connections". When I try that there is nothing listed undetermined wired connections. When I click Add I am prompted for a MAC address as I do not know this I have to close the dialogue box.

---

### Post by TaoBoogie on 2010-08-14
Tried ip link
Got
l:  Lo LOOPBACK, UP, LOWER UP mtu 16436 qdisk noqueue state UNKNOWN 
link/loopback.00:00:00:00:00:00: brd 00:00:00:00:00:00

---

### Post by Iowan on 2010-08-14
> **TaoBoogie said:**
> Thanks
I tried (lshw -C network) 
The response from the terminal was I should run this programme as "super user" #-o I hate when I forget that...
Yes, it shoulda been **sudo lshw -C network**. It works without, but the results can be a little different... but it should have returned *something*!

---

### Post by TaoBoogie on 2010-08-15
Thanks for your help Iowan.
This time I did get a return very briefly, for a couple of seconds > PCI (sysfs)
The the terminal display returns to default status.

---

### Post by TaoBoogie on 2010-08-15
Thanks for your help Iowan.
This time I did get a return very briefly, for a couple of seconds > PCI (sysfs)
The the terminal display returns to default status.

---

### Post by TaoBoogie on 2010-08-15
Not sure if this helps
When I type in a terminal ifconfig I get > 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 K 

---

### Post by TaoBoogie on 2010-08-17
Are there any other terminal tests I can run to check hardware/software issues?
I have connected to the net through my phone, network manager recognises that straight away.

---

### Post by dineshs on 2010-08-18
> I have connected to the net through my phone, network manager recognises that straight away.Can you explain this,like what port are you using to connect? USB or ethernet?If USB what is the result of```
lsusb
```and what phone?mobile?

---

### Post by TaoBoogie on 2010-08-18
My broadband connection, the one that does not work, is through an ethernet connection. It did work perfectly untill this install.
I did manage to connect to the net using my HTC desire connected to the computer via a USB. I used the Internet Sharing function on my HTC to do this.

Terminal command lsusb gives:
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```

---

### Post by dineshs on 2010-08-18
You might have ensured networking is enabled(Right click Network manager icon on top right of the panel)and the BIOS setup  Can you post the results of
```
ifconfig -a
```

---

### Post by TaoBoogie on 2010-08-18
Thank you dineshs
I have ensured the networking is enabled by the method you suggest. I am not sure how to do it in the BIOS setup though.
Here is the results of ifconfig -a
```

ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

usb0      Link encap:Ethernet  HWaddr 26:2f:df:c5:a9:75  
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::242f:dfff:fec5:a975/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:396 errors:1 dropped:0 overruns:0 frame:1
          TX packets:419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:397973 (397.9 KB)  TX bytes:81976 (81.9 KB)

```

---

### Post by TaoBoogie on 2010-08-18
So, you got me to wondering about the BIOS setup dineshs.
I checked the "Integrated Peripherals" and noticed the "On Chip Lan" 1 and 2 were disabled so I set both to Auto and now I'm up and running and connected again.
Many thanks for all the help given.
Slainte

---

