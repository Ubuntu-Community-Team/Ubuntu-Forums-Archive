---
title: "not possible to enable wireless"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by hkb on 2009-02-26
I don't know how but suddenly i can't enable wireless on my laptop. I have tried with both the KDE and GNOME networkmanagers but none of them lets me enable wireless. 

The wiered network woks without problems and ifconfig doesen't seem to show any problems.

---

### Post by kestrel1 on 2009-02-26
How do you mean exactly?
I have had a problem with my Wireless on Mint 6 recently that it wouldn't pick up any wireless networks in my area & I know there are at least 6, mine included. When it did see mine it wasn't saving the WPA key.
What I ended up doing was to remove my wireless network (auto eth1) & restarting the machine. After I had done that I seem to be able to get on to my wireless network first time.
Not sure if this is the same issue you have.

---

### Post by hkb on 2009-02-26
My problem is that i can't enable wireless. When i right click the network icon i have the 2 choices: "enable networking" and "enable wireless" but "enable wireless" is gray and cant be clicked on.

Its a problem that just came out of the blue. It have worked before but stopped about 2 weeks ago.

---

### Post by kestrel1 on 2009-03-02
Can you post the output from:```
lspci
``````
iwconfig
```

---

### Post by zerubbabel on 2009-03-03
I have exactly the same problem. My wireless has been working flawlessly for months, ever since I switched from Windows to Ubuntu, and all of a sudden, within the past few days, I can no longer enable wireless. I'm running 8.10 with all available updates applied as of today.

Here's the output from "lspci" and "iwconfig":

zerubbabel@dz:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
zerubbabel@dz:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

zerubbabel@dz:~$

---

### Post by Crafty Kisses on 2009-03-03
Hey there! This is the wireless card you have:
```
Intel Corporation PRO/Wireless 3945ABG
```
So there's a couple of things we can do here. Depending on what distribution of Ubuntu you are running, you should probably install the backports package, so for example if you're running Intrepid, you would install this package:
```
sudo apt-get install linux-backports-modules-intrepid
```
Once you have that installed the backports package, reboot with the following command:
```
sudo shutdown -r now
```
Once you're back into Ubuntu, try scanning for networks:
```
iwlist wlan0 scan
```
See if you get any wireless networks.

---

### Post by zerubbabel on 2009-03-03
Ok, I'll do that, but the problem right now isn't that the wireless isn't seeing any networks, but that I can't enable the wireless at all. It's "greyed-out" when I pull down the menu.

---

### Post by zerubbabel on 2009-03-03
Did as suggested, and here is the result:

zerubbabel@dz:~$ iwlist wlan0 scan
wlan0     No scan results

zerubbabel@dz:~$

---

### Post by zerubbabel on 2009-03-04
ping...

---

### Post by willie1 on 2009-03-04
I have had the same problem with my Advent laptop. I'd set up a dual-boot with Vista (:cry:) and if I booted straight into Kubuntu, I could not wake the wireless with the buttons on the machine. I had to boot to windoze first, enable wireless, and then restart the laptop. When I then booted to Linux, the wireless was working.:confused:

---

### Post by Spirit55555 on 2009-03-04
I had same problem, and this fixed it: [http://ubuntuforums.org/showpost.php?p=5926426&postcount=8](http://ubuntuforums.org/showpost.php?p=5926426&postcount=8)

---

### Post by zerubbabel on 2009-03-04
But I only have Ubuntu 8.10 installed, no windoze, and I never had any trouble with the wireless until a few days ago. Haven't installed anything new either, except system updates.

---

### Post by Maheriano on 2009-03-04
Is it a laptop? Have you tried plugging it in and then trying it? My brother's wireless doesn't work unless it's plugged in and I still haven't found a solution for it.

---

### Post by zerubbabel on 2009-03-04
Yes, it's a Dell Latitude d830, and it's plugged in most of the time.

---

### Post by zerubbabel on 2009-03-04
Here's the relevant section of the output from "sudo lshw":

           *-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1c:bf:87:10:b0
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

Obviously, it's disabled for some reason, but how can I enable it when that option is "grayed-out" in the menu from the network icon? Is there another tool somewhere, or a way to enable it from the commandline?

---

### Post by zerubbabel on 2009-03-04
Ah ha! Found the problem. How embarrassing! There's an external switch on the edge of this laptop that I never knew was there, which turns the wireless on and off, and I must have bumped it a few days ago.

---

### Post by Maheriano on 2009-03-05
> **zerubbabel said:**
> Ah ha! Found the problem. How embarrassing! There's an external switch on the edge of this laptop that I never knew was there, which turns the wireless on and off, and I must have bumped it a few days ago.

Holy hell, I was going to suggest that but discarded it since you knew what you were doing.
I used to work for tech support for a company and this was a major problem for people. It was even more obscure when you had to do something like Fcn+F6 to turn it on/off. It was first on my troubleshooting checklist when helping people.

---

### Post by kestrel1 on 2009-03-05
> **zerubbabel said:**
> Ah ha! Found the problem. How embarrassing! There's an external switch on the edge of this laptop that I never knew was there, which turns the wireless on and off, and I must have bumped it a few days ago.
Easily done. At least you will know next time :lolflag:

---

### Post by willie1 on 2009-03-05
> **zerubbabel said:**
> Ah ha! Found the problem. How embarrassing! There's an external switch on the edge of this laptop that I never knew was there, which turns the wireless on and off, and I must have bumped it a few days ago.

Mine doesn't work either with the external switch or by Fn + F2, both of which work in Vista. (Came pre installed).

---

