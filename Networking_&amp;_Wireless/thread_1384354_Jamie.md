---
title: "Jamie"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by wilsjamie on 2010-01-18
I recently purchased an Acer Aspire 1410 notebook running Windows 7 home edition. I installed Ubuntu 2.3 and my wireless and network LAN connection is not working. I saw on a link in this forum, someone was having similar problem. However, when i tried the solution that was recommended/suggested to the person, it did not work for me. 

Can someone please tell me what I can do to get my wireless and wired connection to work?

---

### Post by Iowan on 2010-01-18
Current Ubuntu release is 9.10 - I'm not quite sure what 2.3 might be. 
Open a terminal (Applications>Accessories>Terminal) and enter:```
sudo lshw -C network
``` Post results here. (That should provide details about your interface devices.)

---

### Post by wilsjamie on 2010-01-18
ran the command and got the following returned:

  *-network               
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 00:26:9e:68:0b:bf
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1C driverversion=1.0.1.4 firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: WiFi Link 100 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:e1:b2:a1:09:4f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jamie@jamie-laptop:~$ 



is it that the network is "DISABLED"?

---

### Post by bkratz on 2010-01-18
Could you also post the output of 
 lspci | grep Wireless
 (that is LSPCI in lowercase)

---

### Post by wilsjamie on 2010-01-18
The command "lspci | grep Wireless" did not return anything.

---

### Post by bkratz on 2010-01-18
> **wilsjamie said:**
> The command "lspci | grep Wireless" did not return anything.

Try just lspci

---

### Post by wilsjamie on 2010-01-18
Sorry....i should put exactly what i saw:

jamie@jamie-laptop:~$ lspci | grep Wireless
jamie@jamie-laptop:~$

---

### Post by wilsjamie on 2010-01-18
[SIZE=2]jamie@jamie-laptop:~$ lspci[/SIZE]
    [SIZE=2]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)[/SIZE]
    [SIZE=2]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/SIZE]
    [SIZE=2]00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/SIZE]
    [SIZE=2]00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)[/SIZE]
    [SIZE=2]00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev03)[/SIZE]
    [SIZE=2]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)[/SIZE]
    [SIZE=2]00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)[/SIZE]
    [SIZE=2]00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)[/SIZE]
    [SIZE=2]00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)[/SIZE]
    [SIZE=2]00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)[/SIZE]
    [SIZE=2]00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)[/SIZE]
    [SIZE=2]00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev03)[/SIZE]
      [SIZE=2]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
[/SIZE]
  [SIZE=2]00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)[/SIZE]
    [SIZE=2]00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)[/SIZE]
    [SIZE=2]00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)[/SIZE]
    [SIZE=2]01:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)[/SIZE]
    [SIZE=2]02:00.0 Network controller: Intel Corporation WiFi Link 100 Series[/SIZE]
    [SIZE=2]jamie@jamie-laptop:~$ [/SIZE]
  [SIZE=2] [/SIZE]

[SIZE=2][/SIZE]
[SIZE=2]
[/SIZE]

---

### Post by bkratz on 2010-01-18
I was hoping that it would give some more information than just Intel Corp WiFi Link 100 series. Well ok I will just search for that.

---

### Post by wilsjamie on 2010-01-18
thanks for helping me out.........

---

### Post by bkratz on 2010-01-18
> **wilsjamie said:**
> thanks for helping me out.........




Found something interesting

[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

Look at the bottom of the page

---

### Post by wilsjamie on 2010-01-18
still.....no joy :(

I did everything as instructed but still didn't work.


stressss !!!!!!!!!

---

### Post by mick222 on 2010-01-18
Enable backports repositories syatem -. admin-.software sources
-. updates 

```
This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.

1. Open up Terminal.

2. Install the "linux-backports-modules-karmic" (newer wireless drivers from compat-wireless) package and the "b43-fwcutter" package (wireless firmware). During installation, if it asks you to fetch the firmware automatically, make sure you select yes.

Code:
sudo apt-get install linux-backports-modules-karmic b43-fwcutter
3. Blacklist the ssb module.

Code:
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
4. Blacklist the wl module.

Code:
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
5. Reboot

6. Enjoy your wireless!!!
```
should work you need wired access first chk this post seems to work for most people [http://ubuntuforums.org/showthread.php?t=1369260&page=3](http://ubuntuforums.org/showthread.php?t=1369260&page=3) Aso better to dscribe your problem a little in the title.

---

### Post by bkratz on 2010-01-18
> **mick222 said:**
> Enable backports repositories syatem -. admin-.software sources
-. updates 

```
This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.

1. Open up Terminal.

2. Install the "linux-backports-modules-karmic" (newer wireless drivers from compat-wireless) package and the "b43-fwcutter" package (wireless firmware). During installation, if it asks you to fetch the firmware automatically, make sure you select yes.

Code:
sudo apt-get install linux-backports-modules-karmic b43-fwcutter
3. Blacklist the ssb module.

Code:
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
4. Blacklist the wl module.

Code:
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
5. Reboot

6. Enjoy your wireless!!!
```
should work you need wired access first chk this post seems to work for most people [http://ubuntuforums.org/showthread.php?t=1369260&page=3](http://ubuntuforums.org/showthread.php?t=1369260&page=3) Aso better to dscribe your problem a little in the title.




Just curious, why would he bother with the Broadcom drivers when he has a Intel card?

---

### Post by bkratz on 2010-01-18
> **wilsjamie said:**
> still.....no joy :(

I did everything as instructed but still didn't work.


stressss !!!!!!!!!



Everything else I have found today seems to indicate that it should have worked out of the box with the driver being iwlagn. I should have asked earlier, but is there any kind of switch or key combination that can turn off wireless on the unit? Also, can you check the bios and make sure that it is on?

---

