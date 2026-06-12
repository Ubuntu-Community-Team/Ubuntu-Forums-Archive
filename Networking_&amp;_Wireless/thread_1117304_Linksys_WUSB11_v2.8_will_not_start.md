---
title: "Linksys WUSB11 v2.8 will not start"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by battlebison on 2009-04-05
I'm a first-time linux user who's been struggling for about a day now trying to get a USB wireless dongle to work. It's a Linksys WUSB11 v2.8, I'm running a Wubi Ubuntu Intrepid v8.10 installation on a Windows XP machine. I've read as many forums posts and help files as I could, but still no luck.

From what I've read, this device *should* work right out of the box, but I guess not for me. Here's my story, maybe someone can tell me what I'm doing wrong?

Try #1:
First, I manually compiled ndiswrapper-1.54 and did it all via command line. I was able to get to a point where in my iwconfig, I had a wireless connection listed as being controlled by AT76_USB drivers. Nothing I could do from there seemed to be working and those definitely aren't the ndiswrapper drivers I installed, so I figured since it was a Wubi install, I would just reset the whole thing. So I uninstalled the whole shabang, fresh install!

Try#2:
This time, I installed [linux-wlan-ng]("http://packages.ubuntu.com/intrepid/linux-wlan-ng") even though I didn't have to (just in case!) as well as [ndisgtk]("http://packages.ubuntu.com/intrepid/ndisgtk"). I installed the driver with the ndisgtk GUI: still didn't work. Back to the terminal! Here's what I did (maybe this will help someone figure out my problem?) with annotations to help point things out:
```

tom@ubuntu:~$ lsusb
Bus 002 Device 004: ID 1915:2233 Linksys WUSB11 v2.8 802.11b Adapter

tom@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

tom@ubuntu:~$ ifconfig
eth0      [some stuff here]

lo        [some stuff here too]

#Here I unplugged and replugged my device
tom@ubuntu:~$ dmesg
[  757.808063] usb 2-1: USB disconnect, address 6
[  767.720014] usb 2-1: new full speed USB device using uhci_hcd and address 7
[  767.870159] usb 2-1: configuration #1 chosen from 1 choice
[  767.988027] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[  768.140429] ndiswrapper (load_wrap_driver:108): couldn't load driver netusb; check system log for messages from 'loadndisdriver'

#Time to check that system log!
tom@ubuntu:~$ sudo gedit /var/log/syslog
Apr  5 15:37:15 ubuntu kernel: [  757.808063] usb 2-1: USB disconnect, address 6
Apr  5 15:37:25 ubuntu kernel: [  767.720014] usb 2-1: new full speed USB device using uhci_hcd and address 7
Apr  5 15:37:25 ubuntu kernel: [  767.870159] usb 2-1: configuration #1 chosen from 1 choice
Apr  5 15:37:26 ubuntu kernel: [  767.988027] usb 2-1: reset full speed USB device using uhci_hcd and address 7
Apr  5 15:37:26 ubuntu loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver netusb 
Apr  5 15:37:26 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netusb 
Apr  5 15:37:26 ubuntu kernel: [  768.140429] ndiswrapper (load_wrap_driver:108): couldn't load driver netusb; check system log for messages from 'loadndisdriver'

#Too many .sys files?
tom@ubuntu:~$ cd driver

#Well, here they are in all their glory! These came straight from the linksys website, is this where my mistake is? I tried installing it with just NETUSB.sys but that caused an error.
tom@ubuntu:~/driver$ dir
netrfm2k.cat  NETUSBXP.SYS  vnet58l.sys   VNETUSBA.SYS
NETUSB.inf    PRISM9x.SYS   vnet58lx.sys  vnetusbl.sys
NETUSB.SYS    PRISMXP.SYS   vnetu9xl.sys  vnetusbxp.sys

tom@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       [stuff in here]
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       [stuff in here]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

#JUST to make sure that the blacklist is okay... yup, everything checks out.
tom@ubuntu:~$ gksudo gedit /etc/modprobe.d/blacklist

```

Help?

---

### Post by avdistribution on 2009-04-20
Exact same problem here-same adapter, same inf/sys files present, the driver is recognized, but get the same error "too many sys files". The XPSYS file was apparently the one that was working with this box under Windows, but how do I delete/rename the others? Or is there some other way to point Ubuntu to the correct one?

---

