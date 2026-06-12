---
title: "Old Thinkpad T30 with NETGEAR WG511 v2 help"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by V2JTB on 2009-04-04
Hi All,

I have an old Thinkpad T30 and bought a NETGEAR WG511 v2 made in China WIFI card.  I removed the original built in mini card so  I could use the PCMCIA card as I did not want any problems.  I am using the the Ubuntu 8.10 CD.

I have never used linux before and would like to make it easy and use a Wifi card that is supported out the box.  Could you give me some advice on what card to buy and how to get it working?

Almost a Ubuntu Linux user

---

### Post by shane8002 on 2009-04-04
Get the Linksys WUSB54GC, it's a usb wireless card and the driver is rt73 ralink driver that is open source so you just plug it in and thats it works out of the box.

---

### Post by superprash2003 on 2009-04-05
in your terminal type **lshw -C network** and post output

---

### Post by V2JTB on 2009-04-05
Hi All,

I would like to us a PCMCIA card if poss as this is an old laptop.

I typed in ishw -c network

I get - To run a command as administrator (user "root"), use "Sudo <command>".

See "man sudo_root" for details.

---

### Post by V2JTB on 2009-04-05
I got this working - lshw -C network - I used an i instead of l.  

ubuntu@ubuntu:~$ ishw -c network
bash: ishw: command not found
ubuntu@ubuntu:~$ lishw -c network
bash: lishw: command not found
ubuntu@ubuntu:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:13:bf:91
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: xxxxxxxxxxx
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by V2JTB on 2009-04-06
I should point out that I am running Ubuntu from CD.

So not too sure how to load drivers if needed.

Oh my god why is this so hard to do?

---

### Post by V2JTB on 2009-04-06
Two days waiting for a reply, Okay I give up thanks for the help........

Back to Vista

---

### Post by voltsy on 2009-04-13
hi VJ2JTB,

you are _not_ alone! I too have been struggling with NetGear WG511v3 (It seems you do have v3) It can be made to work quite well with ndiswrapper and a package of drivers I downloaded from "somewhere" (can't remember!!) the pkg was called ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip and I used the XP drivers AFAIK, as was recommended in the HOWTO...

...which would all be fine and dandy, except since synaptic did an automatic kernel update to 2.6.24-22-generic on Christmas eve 2008, the system is broken, and I'm still using kernel 2.6.22-16-generic -which allows me not only great web surfing, but actually allows me to BOOT THE MACHINE without running into kernel hangs with ACPI conflicts on my BIOS/old-hardware (HP omnibook 6000 1GHz P3).

The kernel fix for my H/W was to add kernel parameter "acpi=off" to /boot/grub/menu.lst (at the end of your first uncommented 'kernel' line)

The fix for our wayward WG511v3 drivers _might_ be to add more entries to the /etc/modprobe.d/blacklist file as described here: [http://ubuntuforums.org/archive/index.php/t-801947.html](http://ubuntuforums.org/archive/index.php/t-801947.html)

namely:

blacklist prism54
blacklist p54pci
blacklist islsm_pci
blacklist islusb
blacklist isl3886

...but this is still a work-in-progress, so if I can't blacklist the offending kernel modules of the more recent Hardy Heron kernels, I too will be stuck, but intend just to revert to kernel vmlinuz-2.6.22-16-generic because it works fine. 

It really shits me when all my finely tuned tweaks get trashed by automatic updates, but that's progress I suppose ;-)

BTW, here is my current sudo lshw -C network entry for the WG511v3:

*-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 03
       serial: 00:1e:2a:af:88:9f
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8000c driverversion=1.45+Marvell,02/22/2005,3.1.1.7 ip=192.168.1.9 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

