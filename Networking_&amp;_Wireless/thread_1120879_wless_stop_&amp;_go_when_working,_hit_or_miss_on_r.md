---
title: "wless stop &amp; go when working, hit or miss on restart PLEASE HELP!"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Toady00 on 2009-04-09
I'm running ubuntu 8.10. I have a dell inspirion e1705 laptop. I'm using the STA driver & my chipset is BCM4328. 

Problems:
1. Wireless card sometimes doesn't come on when restarted. Maybe 1 out of 5 restarts.
2. When it is working it it stays connected to the wireless network but, downloading files or loading webpages just stops out of nowhere for a few minutes and then starts back.
3.Wireless is slower than I think it should be for a draft n network. If I right click on wireless connections and look at connection information it says only 2Mb/s.

Here are the results from some of the commands the sticky suggests. I have omited some of the info I don't think is relevant but if there is something missing let me know and I'll repost the command results. Thanks everybody for their help.

```
brandon@brandon-laptop:~$ lspci
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

brandon@brandon-laptop:~$ lspci -v | less
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)
        Subsystem: Dell Device 0009
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at efdfc000 (64-bit, non-prefetchable) [size=16K]
        Memory at e0000000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl, ssb

brandon@brandon-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
eth0      no wireless extensions.

pan0      no wireless extensions.

```

This result is from restart when wireless IS NOT working
```

brandon@brandon-laptop:~$ sudo lshw -C network
[sudo] password for brandon: 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

```
This result is from restart when wireless IS working
```

brandon@brandon-laptop:~$ sudo lshw -C network
[sudo] password for brandon: 
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:cf:3d:0b:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.0.199 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

```

---

### Post by Toady00 on 2009-04-10
Should I try to use ndiswrapper instead?

---

### Post by Toady00 on 2009-04-10
Somebody please help! I don't know how to fix this.

---

### Post by PGrey on 2009-04-13
I'm having a similar problem with the same hardware.  I can not find help anywhere on how to fix it. SInce it has been 5 days have you found a resolution yet?

---

### Post by Toady00 on 2009-04-17
> **PGrey said:**
> I'm having a similar problem with the same hardware.  I can not find help anywhere on how to fix it. SInce it has been 5 days have you found a resolution yet?

No. I tried using ndiswrapper, and it worked...for 2 mins. My speed went up from 2Mb/s to 130Mb/s (which is where it should be), and everything seemed fine, but after 2 mins it just quit transferring data to and from the router. I was still connected but I had no movement. And it would not start back until I rebooted. But then it did the same thing after about 2 mins. I tried to uninstall the ndiswrapper driver and go back to the sta driver and completely hosed my laptop. I ended up having to reinstall Ubuntu and to top it all off, I've been working on a website using xampp and I backed up my htdocs folder but I forgot to backup my include files, so I lost half my frigging website practically. I do not suggest using the ndiswrapper unless someone else has some extra steps to take that I missed and they know it works.

---

### Post by Ayuthia on 2009-04-17
Can you post the results of:
```
dmesg|grep -e wl -e ndiswrapper
```

---

### Post by Toady00 on 2009-04-17
> **Ayuthia said:**
> Can you post the results of:
```
dmesg|grep -e wl -e ndiswrapper
```

I nuked my system and went back to the STA driver. If you think you can help me, i'll re-install it. But I don't want to have to nuke my system again to get my wireless working again.

---

### Post by Toady00 on 2009-07-12
Anybody have any ideas. If I could get the wireless to work correctly, I would ditch windows all together, but I rely on a stable wireless connection for many things. Please Please help me out.

---

