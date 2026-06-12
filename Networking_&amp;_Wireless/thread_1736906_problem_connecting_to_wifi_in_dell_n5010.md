---
title: "problem connecting to wifi in dell n5010"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by bruce2wayne on 2011-04-22
hi, guys this is shan and i'm using a dell n5010 recently i installed ubuntu9.10 in my laptop and it doesn't seem to detect wireless connections, so, i googled it and downloaded a driver from broadcom and tried to install it as per the authors instructions and nothing seems to work well, the broadcom drivers are not detected in the additional drivers and when i try to install linux-wlan-ng tarballs it doesn't seem to work even, though i have gcc(i think thats it), so, i installed my windows driver through nsdgtk but it says that it is **_"unable to see if hardware is present"_** but, when i click ok on the error the wireless network applet says the hardware is present and when i click the network configuration tool it gives the error message **_"could not find a network configuration tool"_** and after configuring my network with network tools in administration it says **_"no wireless extensions"_** when i type 'iwconfig' and there is no ip address when i type "ipconfig". so guys pl help me out here i'm a total noob when it comes to ubuntu and **_i don't have a internet connection too.  _**

---

### Post by josephmills on 2011-04-22
hi there could you please press 
[b]
ctrl+alt+t
[/b]
type in 
```

lspci -vnn | grep 14e4

```
you will see something like this 

0001:01:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller** [14e4:4318]** (rev 02)

we only want this  number in bold  
thanks

---

### Post by bruce2wayne on 2011-04-22
sir, the number in bold is as follows

14e4:4727

and the 14e4 is in red colour

and i have a (rev 01) at the end

---

### Post by josephmills on 2011-04-22
could I see 
```

rfkill list all 

```
thanks

---

### Post by bruce2wayne on 2011-04-22
yes and they are as follows
 
```
 
0: dell-wifi: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: dell-bluetooth: Bluetooth
 Soft blocked: no
 Hard blocked: no
2: hci0: Bluetooth
 Soft blocked: no
 Hard blocked: no

```

---

### Post by bruce2wayne on 2011-04-22
):P
 
i think mr.joseph mills has logged off can any one solve this problem for me pl :popcorn:

---

### Post by bruce2wayne on 2011-04-22
can anyone help me out pl

---

### Post by josephmills on 2011-04-22
hi again could I please see a
```

sudo lshw -C network

```

---

### Post by bruce2wayne on 2011-04-23
welcome back sir here u go
 
```
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version
 -version        print program version (B.02.14)
format can be
 -html           output hardware tree as HTML
 -xml            output hardware tree as XML
 -short          output hardware paths
 -businfo        output bus information
options can be
 -class CLASS    only show a certain class of hardware
 -C CLASS        same as '-class CLASS'
 -c CLASS        same as '-class CLASS'
 -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
 -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
 -quiet          don't display status
 -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
 -numeric        output numeric IDs (for PCI, USB, etc.)
[EMAIL="shan@GRDdown:~$"]shan@GRDdown:~$[/EMAIL] sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:12:00.0"]pci@0000:12:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbd00000-fbd03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:13:00.0"]pci@0000:13:00.0[/EMAIL]
       logical name: eth0
       version: 02
       serial: a4:ba:db:d3:ed:1a
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:34 ioport:d000(size=256) memory:d0c10000-d0c10fff(prefetchable) memory:d0c00000-d0c0ffff(prefetchable) memory:fb300000-fb31ffff(prefetchable)

```

---

### Post by bruce2wayne on 2011-04-23
and since u might need other ifconfig info i have included a new document here that might be of some help to u
 
[ATTACH]189756[/ATTACH]

---

### Post by josephmills on 2011-04-23
please plug into your router and go to System-->addmin-->additional drivers  Is there a driver available?

---

### Post by bruce2wayne on 2011-04-23
sorry to say this but i dont have a wired internet connection at this point of time all i have is wireless connections here in my campus.

---

### Post by bruce2wayne on 2011-04-23
is there another way to work out this problem:(

---

### Post by josephmills on 2011-04-23
this is what I have come up with you don't need ndiswrapper but I mean it might work but I think thatyou might need this [http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211) 
if you find a tar.gz of it you could bring it over from a usb or a cd and make a folder on your desktop call it wireless and put the tar.gz in it then move that folder to /lib/firmware then extract the tar.gz once it is in the firmware file and wireles should work after that point (I think)

---

### Post by bruce2wayne on 2011-04-23
they don't have any tar.gz over there so what file should i be exactly looking for

---

### Post by Fry33 on 2011-05-19
Hello all, I have the same problem which in subj.
I install driver from "additional drivers" menu, but it wifi still doesn't work:(
I attached file with info ( lspci, lsusb, and more ).
Please, help!

---

### Post by josephmills on 2011-05-19
hi there fry there are a couple of things first your wireless switch is turned off please turn it on then post ```
rfkill list all 
```

---

### Post by wijit on 2011-05-27
I too have had similar problems on my new Dell n4030. Pytheas22 has helped many people including me solving this sort of problems. It is about having to download a package to install some drivers which were not provided by Ubuntu nor Dell. Find and follow his thread and I believe you can solve your problems too. The only down side is that you have to redo the "Make" process every time you update your kernel. But that is not a big pain since you can grab the commands into a text file and run them with a single call. I don't know why these problems persist. I have my Dell in Jan 2011 but it seems somebody faced such problems for long before.

---

