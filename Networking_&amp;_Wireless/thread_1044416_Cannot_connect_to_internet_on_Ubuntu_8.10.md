---
title: "Cannot connect to internet on Ubuntu 8.10"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by RobSu on 2009-01-19
I went to Network Configuration (System > Preferences > Network Configuration) and put in the information for the network I want to connect to and I hit "OK", but nothing happens. I don't know what to do now. The blue wireless light is on that is on the front of my Eee Pc. I saw this post while browsing these forums: 

> 
You need to provide more info to help us help you. Post the output of the following commands from Applications->Accessories->Terminal.

ifconfig
iwconfig
sudo lshw -C network


So I figured that I'd do that here:
```
robert@robert-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:ec:9f:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22148 (22.1 KB)  TX bytes:22148 (22.1 KB)

robert@robert-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

robert@robert-laptop:~$ sudo lshw -C network
[sudo] password for robert: 
Sorry, try again.
[sudo] password for robert: 
  *-network               [B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:ec:9f:5e
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.0.4 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:2b:d4:6f:93:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

If there's anything else I can do to help you guys fix my problem, let me know. I just got Ubuntu two days ago and I'm new to it, but I really like it and I need internet access to use it at school.

Thanks! 
-Rob

---

### Post by Iowan on 2009-01-19
Are you trying to connect via wired or wireless?

---

### Post by RobSu on 2009-01-19
Wireless.

---

### Post by Iowan on 2009-01-19
I don't (yet) have/use wireless,, so can't help... You might use the forum [Search]("http://ubuntuforums.org/search.php") with keywords "eee" and "Atheros".  I saw a few threads - some even marked [SOLVED].

---

### Post by RobSu on 2009-01-19
Thank you for the suggestion. I searched the said threads and I did not find anything specific to my problem, but I did find alot of helpful information about Ubuntu on the Eee PC though. I still cannot access the internet via wireless, I don't even know how to make it search for the network that I want to connect to. I put in all the information of the network in Network Configuration but now I don't know how to search for it.

EDIT: By the way, I plugged the Eee Pc in with a wire and it connected me straight to the internet. Wireless is still a no-go though.

---

### Post by jonobr on 2009-01-19
Heres an interesting post

[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

---

### Post by RobSu on 2009-01-19
Yeah it is interesting, but I have no idea what he's going on about. Are you implying that I need to install drivers or something? Or should I just blindly follow what he said to do on my Eee PC and see if it works? I just don't want to mess anything up...

---

### Post by jonobr on 2009-01-19
HI 

gabsik in the 3rd post outlines the steps which seem to be just remove ndis wrapper and install madwifi.

The README contains the instructions, so he says.

I think if there are any problems you could just remove the madwifi app and drivers.
However, you may want to add a comment to that post, they are probably still subscribed to it and appear to have the experience with your specifc hardware

---

### Post by RobSu on 2009-01-19
I found the help page that he was talking about and I'm following the instructions, but now I'm on this page:

[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)

and I'm on step one:
> 
Obtain the Windows Driver for your system and locate the file that ends with .inf.
How do I obtain the Windows Driver? What driver is it even talking about? For my system? What?

---

### Post by InVeritasFindME on 2009-01-21
I hope this is somewhat helpful, but if you are using a eee pc then consider an OS like the one from eeebuntu.org or geteasypeasy.com. They have all the drivers already loaded for eee owners, and as I understand are built upon ubuntu... sorry if this is out of place, but I am somewhat new to this and about to install this myself on my eee pc 1000 (40gb SSD).
 
 - InVeritasFindME

---

### Post by Truin on 2009-01-28
To get the wireless working you need to install either the drivers via ndiswrapper etc or you can install kernel that supports the wireless card by default. Kernel installation instructions can be found in [http://array.org/ubuntu/index.html](http://array.org/ubuntu/index.html)

---

