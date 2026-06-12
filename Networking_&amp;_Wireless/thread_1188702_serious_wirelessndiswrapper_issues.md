---
title: "serious wireless/ndiswrapper issues"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by ahndoruuu on 2009-06-16
So before I begin this post, let me say that I have already look at just about every "comprehensive troubleshooting" thing that is available on this forum yet I can't seem to solve my problem.

Perhaps its because I just installed Ubuntu yesterday and still know almost nothing about using it, idunno.

Anywho my situation is that I'm dual-booting Ubuntu with my current Vista installation and my wireless card works on Vista, which I'm currently using, but is not functioning in Ubuntu, so I've been having to restart constantly between the two operating systems as I try one method after the next, using a flash drive to take necessary files over to Ubuntu.

So the wireless card I'm running is a Linksys WMP54GS v 1.1
I figured out that Ubuntu will not support it natively and thus I need to make use of ndiswrapper.
I downloaded the appropriate Windows XP drivers for the card, then
I followed tutorials on how to download and install ndiswrapper (in .deb format), and installed two of the packages successfully, the utilities package and the common package
but when it comes to installing the GUI for it (I forget the exact name) it said the installation can't take place because of a failed dependency. It says it needs the utilities package installed, which I DID install just prior to attempting the GUI installation. I've tried reinstalling the packages, logging out and back in, all with no effect.

So please if anyone can help me with this, I'd be eternally grateful as this little hurdle is seriously impeding my desire to transition permanently over to Ubuntu.  I mean if installing drivers is this hard...imagine doing actual hard things...0.0

---

### Post by MaindotC on 2009-06-16
Did you try using Synaptic Package Manager?  Usually that auto-resolves dependency issues.  I believe the package you need is ndisgtk.  You don't really need the gui but whatever floats your boat!

Unless you are doing graphics-intensive operations like running games in Wine or using Compiz, you can always run Ubuntu in a virtual machine in Vista.  Then you can watch your Vista installation load up w/ viruses while Ubuntu stays nice & clean :D

---

### Post by ahndoruuu on 2009-06-16
And how exactly would I go about using Synaptic Package Manager if I have packages I downloaded onto my desktop?

and the file you mentioned IS the gui for ndiswrapper as far as I understand.

---

### Post by cariboo on 2009-06-16
Before you go installing the windows drivers, I would check to see if you wirekess device is detected and the driver is loaded. Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

The above command will create a text file called network.txt, with all the details of your network devices. Copy the text file to your Windows partition, and paste the output in your next post.

---

### Post by dmizer on 2009-06-16
Well, to get NDISwrapper to work, you don't really need the GUI. Let's try to get you online wirelessly and then we can fix the GUI problem.

You'll want to move the Windows driver directory into your home folder (off of your desktop) because it will be permanent. If you delete the directory after you're done, the driver will no longer work.

Once you've done that, open a terminal and enter this command:
```
ls name-of-windows-driver-directory
```
Replace name-of-windows-driver-directory with the actual name of the directory (remember Linux is case sensitive so "Directory" and "directory" are not the same).

Also, please run this command:
```
lshw -C network > lshw-output.txt
```
And post the contents of lshw-output.txt (it will be in your home folder).

Then I can give you a command to load your wireless driver.

---

### Post by ahndoruuu on 2009-06-16
This is the result of "sudo lshw -C network > network.txt":

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:97:b1:0b
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f8:30:a5:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:72:58:da:e3:d3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


from what I can see, this indicates that no driver is installed and possibly that my card is not even being identified properly. but then again I could be totally wrong...

---

### Post by dmizer on 2009-06-16
You have a driver installed. All you really need to do is connect to the internet once (via LAN cable) so Ubuntu can download the firmware for your wireless card, and you should be good to go.

This is your wireless card:
```
BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
```
This is the driver for your wireless card:
```
configuration: driver=b43-pci-bridge latency=64 module=ssb
```

Edit:
If it is impossible for you to get access to the internet via LAN cable, please see this documentation: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#Off-line%20Installation](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#Off-line%20Installation)

---

### Post by ahndoruuu on 2009-06-16
that documentation does say its for a different version of Ubuntu than I am currently running, but

okay I'll try the steps there and report back, thank you.


EDIT: 

dmizer, the documentation you referred me to is telling me to go to System -> Administration -> Restricted Driver Manager, and the "restricted driver manager" is not there.


EDIT AGAIN:

Since I am running Jaunty, i ran "sudo jockey-gtk" which opened the Hardware Drivers
which promptly informed me that I am using no proprietary drivers so didn't give me the option to use the firmware I downloaded.

---

### Post by ahndoruuu on 2009-06-16
Yeah with no Restricted Driver Manager I'm not sure what to do from here.

---

### Post by dmizer on 2009-06-16
OK, to get NDISwrapper to work, you don't really need the GUI. Let's try to get you online wirelessly and go from there.

You'll want to move the Windows driver directory into your home folder (off of your desktop) because it will be permanent. If you delete the directory after you're done, the driver will no longer work.

Once you've done that, open a terminal and enter this command:
```
ls [COLOR="Red"]name-of-windows-driver-directory[/COLOR]
```
Replace [COLOR="Red"]name-of-windows-driver-directory[/COLOR] with the actual name of the directory (remember Linux is case sensitive so "Directory" and "directory" are not the same.

Post the output here.

---

### Post by ddrichardson on 2009-06-16
> **ahndoruuu said:**
> And how exactly would I go about using Synaptic Package Manager if I have packages I downloaded onto my desktop?

and the file you mentioned IS the gui for ndiswrapper as far as I understand.
The guides you mention seem to refer you to direct downloads of deb files, I suspect you have a version of the utils pre or post the one required by ndisgtk.

You can uninstall this package then```
sudo apt-get  install ndisgtk
```
In honesty, I'd love to know if there is an issue because I wrote the section of the system help which explains ndisgtk.

---

### Post by ahndoruuu on 2009-06-16
> **ddrichardson said:**
> The guides you mention seem to refer you to direct downloads of deb files, I suspect you have a version of the utils pre or post the one required by ndisgtk.

Yes you were right, I was attempting to install an older package of ndisgtk, though I have no idea how I got an outdated package.  But after installing a more current version, worked like a charm.




@ dmizer:

The result of "ls /home/andrew/Drivers":

"bcmwl5a.sys  bcmwl5.sys  WMP54GSa.inf  WMP54GS.cat  WMP54GS.inf"


was this what you were looking for?


Edit: 
OH! Forgot to mention that since I have ndisgtk working now, I clicked "install new driver" directed it to "WMP54GS.inf" (not sure if that's the right file or not since there's two .inf's) and a window came up saying "unable to see if hardware is present".  When I clicked "ok" on that, on the ndisgtk menu is said the driver and underneath the driver name "Hardware Present: Yes". So I have no idea whether or not it is properly detecting the card.

---

### Post by dmizer on 2009-06-16
You may have to install both.

You'll also have to disable the native driver:
```
sudo rmmod b43
sudo rmmod ssb
sudo modprobe ndiswrapper
```

---

### Post by ahndoruuu on 2009-06-17
this is the result I got from entering those commands:

"andrew@4XKB91:~$ sudo rmmod b43
[sudo] password for andrew: 
andrew@4XKB91:~$ sudo rmmod ssb
andrew@4XKB91:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."


I'm not sure if it worked or not.

---

### Post by dmizer on 2009-06-17
Looks like it did. Please post the output of:
```
lshw -C network
```
Also, check your network applet to see if you now have a wireless option available.

If you still get nothing, then install the second inf file. I've had a few cards that required two.

---

### Post by ahndoruuu on 2009-06-20
Sorry I took so long to reply, been a bit busy lately.

but here is the output of "lshw -C network" that you requested:

"root@4XKB91:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:97:b1:0b
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f8:30:a5:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e2:72:24:cd:ec:92
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes"



Additionally, I tried using the network applet to get a connection but it doesn't work.  When I start ndisgtk up it still informs me "Unable to see if hardware is present" in a window, then after clicking ok underneath the names of each driver (i did install both in ndisgtk) it says "Hardware Present: Yes" but if i click on one and then press the "configure network" option, it says "unable to find a network configuration tool"
maybe there's a package i never installed or something? because i haven't made any modifications to it, its just the base ubuntu freshly installed off the CD.

---

### Post by dmizer on 2009-06-20
Okay, run this series of commands:
```
sudo rmmod ndiswrapper
sudo rmmod b43legacy
sudo rmmod ssb
sudo modprobe ndiswrapper
```
Each command on a separate line. Then see if your card works. If it does, we can add some commands to /etc/rc.local to make that permanent.

---

### Post by ahndoruuu on 2009-06-20
This is the output:

"andrew@4XKB91:~$ sudo rmmod ndiswrapper
[sudo] password for andrew: 
ERROR: Module ndiswrapper does not exist in /proc/modules
andrew@4XKB91:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
andrew@4XKB91:~$ sudo rmmod ssb
ERROR: Module ssb is in use by b43
andrew@4XKB91:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."


my card still didn't work afterwards, perhaps because of the errors?

---

### Post by Ayuthia on 2009-06-20
It looks like the b43 module was left out by accident.  Please try:
```
sudo rmmod ndiswrapper
sudo rmmod b43legacy
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe ndiswrapper
```

---

### Post by ahndoruuu on 2009-06-20
:D :D :D :D :D
it worked! im now posting this from Ubuntu on my wireless network! Thanks a LOT. to dmizer and Ayuthia.

However I'm curious as to what exactly those commands did...just for educational purposes. In the future I'd like to be able to easily troubleshoot stuff like this on my own so I'm not such a bother and so I can help others with issues.

@dmizer: what are the edits to make it permanent?

---

### Post by Ayuthia on 2009-06-20
The rmmod commands remove the kernel modules.  In this case, we removed the possible conflicting modules--the open source Broadcom modules (b43, b43legacy, b44 (wired Broadcom modules), and ssb) and ndiswrapper.  We then reload the ndiswrapper.  

If the open source Broadcom modules are there before the ndiswrapper module is loaded the ndiswrapper module might not work.

dmizer, correct me if I am wrong, but you are going to edit the /etc/rc.local file:
```
gksu gedit /etc/rc.local
```
and before the exit 0 line in that file you are going to add:
```
rmmod ndiswrapper
rmmod b43
rmmod b43legacy
rmmod b44
rmmod ssb
modprobe ndiswrapper
```and save the file.

---

### Post by dmizer on 2009-06-20
> **Ayuthia said:**
> dmizer, correct me if I am wrong, but you are going to edit the /etc/rc.local file:
```
gksu gedit /etc/rc.local
```
and before the exit 0 line in that file you are going to add:
```
rmmod ndiswrapper
rmmod b43
rmmod b43legacy
rmmod b44
rmmod ssb
modprobe ndiswrapper
```and save the file.

That's the one.

Though it probably only needs this:
```
rmmod b43
rmmod ssb
modprobe ndiswrapper
```

So the file will look like this now:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod b43
rmmod ssb
modprobe ndiswrapper
exit 0
```

---

### Post by Ayuthia on 2009-06-20
> **dmizer said:**
> That's the one.

Though it probably only needs this:
```
rmmod b43
rmmod ssb
modprobe ndiswrapper
```


I agree.

---

### Post by ahndoruuu on 2009-06-21
I am wondering if I really need to edit that file though, because I have restarted/powered down several times since fixing the wireless and it still works.  Would it be better to just edit it and be safe?

---

### Post by dmizer on 2009-06-21
If it's not broken, don't fix it ;) Just keep this thread in mind in case you have trouble down the road.

---

### Post by ahndoruuu on 2009-06-22
> **dmizer said:**
> If it's not broken, don't fix it ;) Just keep this thread in mind in case you have trouble down the road.

Sounds good to me. :) Thanks for taking the time to assist.

---

### Post by beanko on 2009-06-23
Hello,

I have been following along with the exact same errors, and unfortunately, the last fix did not work for me.

victor@kids-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:39:c7:65
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.0.186 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:16:ce:47:9f:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+ASUS,02/11/2005, 3.100.64.0 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:d9:f6:ff:26:ad
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
victor@kids-laptop:~$ 

Any help would be appreciated.

EDIT: I take that back, it is working! thanks

---

### Post by dmizer on 2009-06-23
> **beanko said:**
> EDIT: I take that back, it is working! thanks

Fantastic!

---

### Post by ObsessiveMathsFreak on 2009-07-10
Hello there. I have the same card and the same issue, but an additional problem.

I don't have access to the windows drivers for the card. The Linksys site only provide a windows executable.

However, I am able to get online with the same PC using a LAN cable(apt-get works!). Something was mentioned earlier about Ubuntu being able to find appropriate drivers. Is this possible for this card, or do I need to go looking for the drivers elsewhere?

---

### Post by shalom on 2009-07-12
Thanks for this solution. I have spent many many hours trying to get my card to work, I dont know why I did not stumble into this thread earlier. 

One question, the rmmod b44 command disabled my ethernet card. How can I get it to work again?

Thanks again. I am so happy to be posting this wirelessly!

---

### Post by ahndoruuu on 2009-07-12
> **ObsessiveMathsFreak said:**
> Hello there. I have the same card and the same issue, but an additional problem.

I don't have access to the windows drivers for the card. The Linksys site only provide a windows executable.

However, I am able to get online with the same PC using a LAN cable(apt-get works!). Something was mentioned earlier about Ubuntu being able to find appropriate drivers. Is this possible for this card, or do I need to go looking for the drivers elsewhere?


No, that windows executable is exactly what you need.  Bring it over to linux and it'll open it like a folder, you should browse to a folder called "drivers" within the executable, copy that entire folder to your /home folder in Ubuntu then simply direct your ndiswrapper to use both of the included drivers and you're good to go.

---

### Post by dmizer on 2009-07-12
> **shalom said:**
> Thanks for this solution. I have spent many many hours trying to get my card to work, I dont know why I did not stumble into this thread earlier. 

One question, the rmmod b44 command disabled my ethernet card. How can I get it to work again?

Thanks again. I am so happy to be posting this wirelessly!

Do not include rmmod b44 in the /etc/rc.local file. If it's there, remove it and reboot. Then your wired network card should work fine.

---

### Post by davidjmorin on 2009-07-13
> **Ayuthia said:**
> It looks like the b43 module was left out by accident.  Please try:
```
sudo rmmod ndiswrapper
sudo rmmod b43legacy
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe ndiswrapper
```

this is what i get

david@david:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
david@david:~$ rmmod b43
ERROR: Module b43 does not exist in /proc/modules
david@david:~$ rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
david@david:~$ rmmod b44
ERROR: Module b44 does not exist in /proc/modules
david@david:~$ rmmod ssb
ERROR: Module ssb does not exist in /proc/modules
david@david:~$ modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.28-13-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko): Operation not permitted
david@david:~$

i also do not havfe a rc.local file in my etc folder??????

---

### Post by dmizer on 2009-07-13
> **davidjmorin said:**
> this is what i get

david@david:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
david@david:~$ rmmod b43
ERROR: Module b43 does not exist in /proc/modules
david@david:~$ rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
david@david:~$ rmmod b44
ERROR: Module b44 does not exist in /proc/modules
david@david:~$ rmmod ssb
ERROR: Module ssb does not exist in /proc/modules
david@david:~$ modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.28-13-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko): Operation not permitted
david@david:~$

i also do not havfe a rc.local file in my etc folder??????

You probably don't have an rc.local file in your etc folder. The rc.local file is located in the /etc folder (the "/" is very important).

Please post the output of the following command:
```
lshw -C network
```

---

### Post by ahndoruuu on 2009-07-14
> **davidjmorin said:**
> this is what i get

david@david:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
david@david:~$ rmmod b43
ERROR: Module b43 does not exist in /proc/modules
david@david:~$ rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
david@david:~$ rmmod b44
ERROR: Module b44 does not exist in /proc/modules
david@david:~$ rmmod ssb
ERROR: Module ssb does not exist in /proc/modules
david@david:~$ modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.28-13-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko): Operation not permitted
david@david:~$

i also do not havfe a rc.local file in my etc folder??????



uhh, try typing "sudo modprobe ndiswrapper" instead, that operation should be permitted.

---

### Post by rwalker83 on 2009-07-14
I am been trying a failing to fix this for awhile please help.

  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:67:5b:98
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.10.192 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 00
       serial: 00:0e:9b:78:d0:4c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.53+INPROCOMM,11/04/2004,3.03.1 latency=64 link=yes maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:2d:98:2e:17:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by dmizer on 2009-07-14
> **ahndoruuu said:**
> uhh, try typing "sudo modprobe ndiswrapper" instead, that operation should be permitted.
I don't think it's going to make a difference anyway, because I suspect that davidjmorin's card is not a broadcom chipset.

> **rwalker83 said:**
> I am been trying a failing to fix this for awhile please help.

  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:67:5b:98
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.10.192 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 00
       serial: 00:0e:9b:78:d0:4c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.53+INPROCOMM,11/04/2004,3.03.1 latency=64 link=yes maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:2d:98:2e:17:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Looks good to me. But you appear to have a different card than is discussed in this thread. You'll be better off posting your own thread.

---

### Post by burf87 on 2009-07-20
Please post the output of the following command:
```
lshw -C network
```[/quote]
 
Hi, I'm having the same problem, have followed all the steps so far to no avail. This is the output that was requested:
 
[EMAIL="tom@tom-laptop:~$"]tom@tom-laptop:~$[/EMAIL] lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: [EMAIL="pci@0000:08:02.0"]pci@0000:08:02.0[/EMAIL]
       logical name: eth0
       version: 10
       serial: 00:16:36:90:f2:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: [EMAIL="pci@0000:08:04.0"]pci@0000:08:04.0[/EMAIL]
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:60:50:bf:fa:6e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[EMAIL="tom@tom-laptop:~$"]tom@tom-laptop:~$[/EMAIL] 
 
All help greatfully received
 
Rgds

---

### Post by burf87 on 2009-07-20
> **dmizer said:**
>  
Please post the output of the following command:
```
lshw -C network
```
 
sorry didn't quote that properly in the previous post
 
cheers

---

### Post by aquilolumen on 2009-08-01
hey, i'm having the same problem as burf87.  

i did "rmmod" on b43, b43legacy, b44, ssb, and ndiswrapper, then did "modprobe" on ndiswrapper and b44.  i'm typing on a different computer, so copy-pasting is kind of a hassle, but the output of "lshw -C network" is pretty much the same as burf87's.  

when i did "modprobe ndiswrapper" and "lshw -C network", the output under "description: Network controller, product: BCM4318..." was:

```
configuration: latency=64
```(which doesn't seem to be very useful).  when i did "modprobe b44", i got:

```
configuration: driver=43-pci-bridge latency=64 module=ssb
```which is the same as the corresponding output provided by burf87. unlike the previous output, the driver appeared, but ndiswrapper wasn't the option.

i'm glad to see that this thread is recently active.  i can provide any output needed for further troubleshooting.  thanks for helping!

---

### Post by ObsessiveMathsFreak on 2009-08-24
I went through all the steps in this thread, installed the correct drivers and got the wireless card to work.

However, when I recently upgraded the system, which I beleive updated the kernel, the wireless card stopped working. I have gone through all the steps again and still no luck with it.

Strangely, the wireless card appears in iwconfig, and I can even run 'iwlist scan' and detect the network I want to connect to. Unfortuntately, running 'ifup wlan0' results in a network connection that hasn't connected to its gateway.

The network is encrypted with WEP, and I have quadruple check the key in /etc/network/interfaces. Perhaps the card is having problems connecting with encryption, but I have no way of finding this out. Does anyone know where the error logs would be?

---

### Post by ObsessiveMathsFreak on 2009-08-24
Well, after many guides and no luck at all, I finally came across something that "almost" works. Previously, the card needed only IP settings, the ESSID and the WEP key. However when I ran
```
#iwconfig wlan0 channel 11
```The card will actually connect. However, it's random, and usually takes a few ifup ifdown's to work.

In addition, when it does work the ping times are AWFUL. Ping times to the router were 1.5ms. Now they go up to 50ms or more. Actually, wait, right now they're back to around 3ms. It's very random.

I'm actually posting to this thread using the wireless card now, but while the situtation is tolerable, it isn't very satisfactory. Can anyone advise as to what exactly ent wrong in the last upgrade? Did ubuntu change some setting so that now channel must be specified or something?

EDIT:

I should add that to make this card select channels automatically at startup (by the way, mine still doesn't automatically start up, but never mind) you need to add the following at the proper location in /etc/network/interfaces
```

wireless-channel 11

```Here's my complete /etc/network/interfaces file as an example
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.2

auto wlan0
iface wlan0 inet static
wireless-key abcdaveryverylongwepkey
wireless-essid homesweethome
wireless-channel 11
address 192.168.2.35
netmask 255.255.255.0
gateway 192.168.2.1

```

EDIT x2:
After fixing a resolution problem, the pings have retuned to their customary 1.15ms ranges. I don't trust the result for an instant, but I think at least these configuration files are OK as they are written. Also, the card starts automatically on boot now.

---

### Post by easytaker on 2009-08-31
hi guys,

I've been fighting with this Broadcom bcm4318 for a while without success.

However after following this thread I feel I got close to a working solution. Not quite there yet.

My current status:

blacklisted all b43/b44/b43legacy/ssb drivers on /etc/modprobe.d/blacklist.conf (note that I had to put ssb as first one otherwise it would keep loading)

ndiswrapper installed (from Jaunty CD), ndisgtk gives me some weird errors (such as not able to find device) - the cli looks much better, so I'm using it. I have two INF files from the original Linksys driver installed and hardware present.

loading ndiswrapper without issues, but on /var/log/messages I'm getting "Windows driver couldn't initialize the device (C0000001)"
followed by some other errors.

Sorry I can't post the exact errors here since I'm working from my laptop. Hope you get the idea.

Any ideas would be much appreciated.


Thanks !:)

---

### Post by easytaker on 2009-08-31
ok, found the issue.

**lshw -C Network** shows which driver is loaded for your network cards, and I found out I had a weird 'b43-pci-bridge' loaded into my wireless card, preventing ndiswrapper to do its job.

now my problem is with WPA, time to jump to another thread :)

---

### Post by kulobrad on 2009-11-28
Hey, i followed your instruction, but i am stuck on, when you add these commands to terminal. Probably it is because i don't have the same card :). So please help me to solve it i am new to linux, so please be patiente :)

i wrote to terminal that command with network and result was:

*-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:26:2d:58:36:39
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.19 ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f5100000-f510ffff
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:1e:65:e9:92:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:f5200000-f5201fff

Please can you help me? what should i do to make it run.

Btw: I have the same problem. Says ''Unable to see if hardware is present'' And then ''Hardware present:yes'' but doesn't work. Thanks

---

### Post by BurkeJax on 2010-01-09
I recently reviewed all of this post post regarding wireless connection issues. I have followed all of the steps, and am now able to see all of my available wireless networks. But, I just have a spinning circle up by my clock once I select an available wireless network, and it continues to prompt for my network password, which I provide the correct values, and it does not attain a connection. I am new to Linux and have no idea where to go from here.

---

### Post by shoepolice on 2010-02-23
Hi

Same problem here. I'd really like to use Ubuntu but can't without wi-fi. Please help!

I get "Unable to see if Hardware is present". Have blacklisted BCN43xx and installed bcmwl5 and bcmwl5a.

DETAILS:

network.txt;

  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:c3:2e:ff
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:68000000-6801ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:23:a4:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,12/22/2004, 3.100. latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:e2000000-e2001fff

AND

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


AND (got this for a few of those commands)

jim@ubuntu:~$ sudo rmmod b43
[sudo] password for jim: 
ERROR: Module b43 does not exist in /proc/modules

---

### Post by Bohakku on 2010-03-15
```
sudo rmmod ndiswrapper
sudo rmmod b43legacy
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe ndiswrapper

```Thanks, **dmizer,** it works! Moreover, it works on Mint what is even greater. And my adapter real name is Asus 138G V2. I think it's about time i ended trying live-cds once a year, being pissed off by everything not working, and installed ubuntu to my harddrive!

---

