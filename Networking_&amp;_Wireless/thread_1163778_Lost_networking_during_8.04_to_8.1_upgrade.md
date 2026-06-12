---
title: "Lost networking during 8.04 to 8.1 upgrade"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by myotis on 2009-05-19
Upgraded 8.04 to 8.1 on Thinkpad T42.

When rebooting the network manager icon spins for a while and then tells me the network is disconnected and that I am now offline. I have tried rebooting a couple of times after the upgrade but this doesn't help

Same problem occurs whether I try to connect to the wireless or wired networks.

This is only an interim upgrade on my way to jaunty, but I assume I need to get 8.1 working properly before upgrading. In any case I, ideally need, to get my network back up and runnning to download Jaunty.

I have found several threads on this, but as usual I am a bit confused as to where to start.

Can anyne help.

Many thanks,

Graham

---

### Post by Peter09 on 2009-05-19
Can you post the output of

```
lshw -C network
```

and

```
ifconfig
```

---

### Post by myotis on 2009-05-19
Thanks, the print out from these two commands are below.

Graham
--------------------------------------------------------------
graham@T42-Linux:~$ lshw -c network 
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Ethernet interface 
       product: 82540EP Gigabit Ethernet Controller (Mobile) 
       vendor: Intel Corporation 
       physical id: 1 
       bus info: pci@0000:02:01.0 
       logical name: eth0 
       version: 03 
       serial: 00:0d:60:fd:6b:7b 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=64 mingnt=255 module=e1000 multicast=yes 
  *-network:1 
       description: Wireless interface 
       product: PRO/Wireless 2200BG [Calexico2] Network Connection 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:02:02.0 
       logical name: eth1 
       version: 05 
       serial: 00:0e:35:58:5f:63 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: ca:28:2a:70:43:8d 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
----------------------------------------------------------------
graham@T42-Linux:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0d:60:fd:6b:7b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:333 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:100 
          RX bytes:24988 (24.9 KB)  TX bytes:684 (684.0 B) 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:58:5f:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2634 (2.6 KB)  TX bytes:1680 (1.6 KB) 
          Interrupt:11 Base address:0x2000 Memory:c0214000-c0214fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2744 (2.7 KB)  TX bytes:2744 (2.7 KB) 
-----------------------------------------------------------------

---

### Post by Iowan on 2009-05-19
What's in */etc/network/interfaces*? Ideally, only:```
auto lo
iface lo inet loopback

```

---

### Post by myotis on 2009-05-20
Thanks, and yes that is all that is in this file.

Graham

> **Iowan said:**
> What's in */etc/network/interfaces*? Ideally, only:```
auto lo
iface lo inet loopback

```

---

### Post by myotis on 2009-05-20
I have just booted up from an 8.1 Live CD and the network (wire and wireless) work fine from the live CD. As of course it did before the upgrade.

Not sure if that gives any clues other than to confirm their is nothing intrinsically wrong with the networking.

Graham

---

### Post by myotis on 2009-05-22
Ah well, I guess I just have to give up on this. and go back to Windows, again.  What a shame :-(

Thanks to the couple of people who tried but it seems that once again I have an unfixable problem.

Graham

---

### Post by Iowan on 2009-05-22
If you'd rather go back to Windows than fix the problem, then good luck to you. Perhaps try back when Karmic comes out.

---

### Post by myotis on 2009-05-23
> **Iowan said:**
> If you'd rather go back to Windows than fix the problem, then good luck to you. Perhaps try back when Karmic comes out.

On the contrary I would rather not go back to Windows. I am forcing myself to make this move because much as I like using Ubuntu, it just seems to need much more time than I have available to keep it running. Time when I should be "working" on my computer I am actually spending time trying to fix Linux.

Ubuntu (and I assume Linux) just seems to be a continual stream of problems, and while part of me enjoys the tinkering, another part of me is concious that this is more time lost to Ubuntu when I should have been doing something else.  Relying on Linux now just scares me, as I now expect a software update of any sort, to probably break something. 

Unfortutunately, horrible as Windows is, most of the time it just works , and when something goes wrong, I can find a help forum that can provide an answer minutes after I post the question. 

Its the uncertainty of getting help, as much as the unpredictability of Ubuntu that is the problem. And I know that the people here and on the other linux forums that I try to get help from are volunteers, and I am grateful for the help that I have received.

I hate the fact that I am forcing myself back to Windows, but it seems the only sensible thing to do.  I'm not at all happy about it.

Graham

---

