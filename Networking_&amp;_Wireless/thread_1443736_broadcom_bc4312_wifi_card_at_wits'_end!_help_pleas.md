---
title: "broadcom bc4312 wifi card: at wits' end! help please!"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by cerberez on 2010-03-31
So I'm trying out Lucid on my hp mini 1030nr. Seems great... EXCEPT wireless stubbornly refuses to work for me. Thankfully, I've got ethernet, but that won't work when I take my beloved netbook out into the world.


> 2.6.32-18-generic i686> 01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)I've tried apt-get install  sudo apt-get install bcmwl-kernel-source

I've tried just going into system>admin>hardware drivers and activating the sta driver

I've installing the drivers from hp website in wine and using ndisgtk to use the .inf file

I've tried b43-fwcutter

between all of these things, of course, I've updated the system with update manager and sudo apt-get update, and rebooted dozens of times.

This is particularly infuriating, because I've had wireless on this computer before (ndiswrapper worked on UNR 9.1, until it died a horrible death)... if I really can't get wifi on lucid I'll try going back to that, but I would rather not.

Can anyone help me?

thanks *so* much, I'm going crazy here.

---

### Post by cerberez on 2010-03-31
In case it helps:

> ezra@ezra-netbook:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:00:00:00:00:00
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.72 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:febfc000-febfffff ioport:ec00(size=256)


> ezra@ezra-netbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe48:f823/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6685311 (6.6 MB)  TX bytes:1038473 (1.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


---

### Post by 98cwitr on 2010-03-31
have you tried going to Administration->Hardware Drivers to see if it's there?

If not, do

```
sudo apt-get install cabextract
```

Download .exe from HP's site then run cabexract for the .exe in terminal ```
sudo cabextract *driver.exe*
```, you should find the correct .inf in the extracted files, load that one into ndiswrapper and you should be good after a reboot. Post your ifconfig again after you've done this.

---

### Post by theozzlives on 2010-03-31
4312 should work out of the box.

---

### Post by 98cwitr on 2010-03-31
^^^nope, had the same issue with a coworker's laptop yesterday as a matter of fact with a BC43** driver. Had to manually install using ndiswrapper and cabextract :(

---

### Post by chicken159 on 2010-03-31
Yeah...it should, and it did - but was a bit slow and kept stalling on a new install on my mini10v. So I tried changing drivers...and now neither work despite several reloads. 

Any suggestions as to how to work out what the issue is here? Can't see any effect of hitting the infamous F2 button.

---

### Post by 98cwitr on 2010-03-31
under lucid and that kernel man your guess is as good as mine...i'd like to know too.

---

### Post by cerberez on 2010-03-31
> **98cwitr said:**
> have you tried going to Administration->Hardware Drivers to see if it's there?

If not, do

```
sudo apt-get install cabextract
```Download .exe from HP's site then run cabexract for the .exe in terminal ```
sudo cabextract *driver.exe*
```, you should find the correct .inf in the extracted files, load that one into ndiswrapper and you should be good after a reboot. Post your ifconfig again after you've done this.

No luck. Didn't work :(

> ezra@ezra-netbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet6 addr: fe80::224:81ff:fe48:f823/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5888 (5.8 KB)  TX bytes:4999 (4.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


---

### Post by cerberez on 2010-03-31
> **cerberez said:**
> No luck. Didn't work :(

I just installed 9.1 and, trying this, I get the error "unable to see if hardware is present." But where the driver shows up in the menu, it says "hardware present: yes."

It still doesn't work. Why is it so hard?

What's going on?

thanks!

---

### Post by cerberez on 2010-03-31
> **cerberez said:**
> I just installed 9.1 and, trying this, I get the error "unable to see if hardware is present." But where the driver shows up in the menu, it says "hardware present: yes."

It still doesn't work. Why is it so hard?

What's going on?

thanks!

WOW! It finally works! after seeing it not even work on 9.1 (yikes!) I decided to give sudo apt-get install bcmwl-kernel-source another try (after an apt-get update). Another reboot and it works. Is it possible that there's something in Lucid that was screwing with my internet?

Anyway, I'm going to be cautiously optimistic. I couldn't connect to the networks in my building, but I can't connect even on my xp notebook. I'm connected now through my phones wifi-tethering, which sets up like a wifi hotspot (and to think, vzw wants to charge 15  a month to let you do that on the pre). I'll report back when I've been somewhere with reliable wifi to check it out, but I think my problem might be fixed.

---

