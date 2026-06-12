---
title: "Wired Connection issue"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by sasrar on 2013-01-16
I recently tried to get rid of the nasty "Google redirect" virus from my Dell Inspiron 530 computer. I used the Combofix program to do this.

When I finished running Combofix the wired internet connection wouldn't work. So after much Internet surfing and research I decided to install Ubuntu 12.04 on the computer. I thought the problem would get solved, but there is still no wired connection.

Here is the output for ifconfig:
> 
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:8a:1f:6f  
          inet6 addr: fe80::21a:a0ff:fe8a:1f6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4985966 (4.9 MB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1406944 (1.4 MB)  TX bytes:1406944 (1.4 MB)And here's the information on the wired lan card :
> 
  *-network
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:8a:1f:6f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.1-2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)Anyone with any ideas on what's wrong with the wired connection?

---

### Post by ahallubuntu on 2013-01-16
Silly question: are you sure the cable is plugged in properly to your router?  Is the link light on/flickering in the plug on the back of the computer where the cable is plugged in?  Is it lit up where it is plugged in on the router (i.e. if you are plugged into port 2 on the router, is the #2 lit up?  Unplug the cable and #2 light goes out?)

If that's all ok...

If you click on the Network Manager Applet in the top right corner, is "Enabled Networking" checked?  If so, can you simply choose Wired Network to connect?

Do you have any other computers connected successfully to this same router?

It's remotely possible the infection got into your router, too, at least if you never changed the default admin password on the router.  I have heard of these infections - they exist "in the wild" but never seen one personally.

---

### Post by sasrar on 2013-01-16
The cable from the router is plugged in and the light is on. I tried unplugging and plugging in the cable to different ports on the router, but the result was the same- no Internet connection. The lights are coming on, though.

I just connected the cable from the router to my laptop and now I see the problem is not the computer but the router itself. I don't receive a connection from the router. Thanks for the tip :).

Can this be fixed by resetting the router? Or is there a better way?

---

### Post by sasrar on 2013-01-16
The problem's solved! I unplugged and plugged in the power cable and now I do get a wired connection from the router. Thanks so much for the help ahallubuntu!

---

### Post by ahallubuntu on 2013-01-16
Duh - power cycling the router, I didn't even think to suggest that!  Glad you figured it out and it was simple after all.  (Bet you wish you'd stuck with Windows now though huh? :-)  Oh, well, welcome to Ubuntu!  I love it - don't miss Windows at all!!

---

