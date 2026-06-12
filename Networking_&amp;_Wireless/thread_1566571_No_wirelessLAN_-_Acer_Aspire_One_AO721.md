---
title: "No wireless/LAN - Acer Aspire One AO721"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by dorito_125 on 2010-09-02
Hey everyone, I'll quickly introduce myself, I've lurked these forums for about two years now, tinkering with mint fedora, and of course Ubuntu.  My desktop runs Ubuntu Desktop x64, my server is ubuntu, and I've convinced family members to give it a chance on there netbooks,  the netbook remix of course. 

The problem I am having is Ubuntu desktop x64 does not find any networking at all on my laptop. 
Acer Aspire One AO721, I figured as much it would be a driver issue, but I don't know which one or how to find it. 
I'm willing and would like to learn, just point me in the right direction. 
Thank you.

---

### Post by dorito_125 on 2010-09-04
Bump.

Nobody knows where to begin? 

I'm dual booting with Win7 to write this, help! haha.

---

### Post by dineshs on 2010-09-04
What do you get for the following command in terminal?
```
sudo lshw -C network
```

---

### Post by dorito_125 on 2010-09-04
I get this:

```

 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:d0200000-d023ffff ioport:a000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0300000-d0303fff


```

---

### Post by dineshs on 2010-09-04
You may try to make the wired part OK first.Search for solved posts reg [COLOR="Blue"]AR8151 ubuntu[/COLOR]
For example
[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)
Maybe slightly different for 64bit

---

### Post by mabini on 2010-10-06
I own an Aspire One AO721 as well. Lucid Lynx would hang right before the login prompt. I tried booting in safe (CLI) mode to do an upgrade only to find out that the ethernet card does not work out of the box. I was able to download the driver and compile it. This I did after downloading all dependencies, saving them to a flash drive and installing them via 'dpkg.' Halfway through the upgrade, I encountered a black screen. The A0721 never did boot, not even in rescue mode. 

**SOLUTION:**
I then installed 10.10 Beta for amd64. Ethernet card worked out of the box. WiFi network did not. I did System > Administration > Additional Drivers and enabled the Broadcom STA wireless driver. I clicked on the WiFi icon. Lo and behold, Wireless Networks is grey and I could not enable it even if the WiFi chipset is being detected when I do an 'iwconfig.' Turns out the NetworkManager applet has issues with A0721. As a workaround, I installed wicd. WiFi now works perfectly.

If you do not want to install wicd, do this command instead.

 sudo /etc/init.d/networking restart
  
Click on the WiFi icon. You should now be able to enable Wireless Networks. But you will have to do a networking restart every time you boot your computer.

---

