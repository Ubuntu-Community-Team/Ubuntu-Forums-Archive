---
title: "Linksys Wireless G USB Network Device"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by LinuxForTheWorld on 2006-01-09
Hello all I'm pretty new to linux. I have briefly messed with several linux's and up until now I have ran Xandros but wanted to try something different Here is my problem so far.

I just moved my computer into a different room and went out and bought a Linksys Wireless G Network USB Device.  This unit installed and works fine in Windows XP When I boot into Ubuntu 5.10 I cannot get it to see the device. I have installed ndiswrapper and installed the GUI that goes with it. I have installed the driver and ndiswrapper says it sees the device but when I goto set up the network all it shows is my built in ethernet card and a dial up modem (which I do not have I'm guessing this is default).  I have tried disableing the ethernet but this does not seem to help.  I have tried several different things and I think I may need to uninstall the ethernet driver all together but have no clue on how to do this. Any help or suggestions anyone? 

Thanks.

---

### Post by healychan on 2006-01-10
I don't think you need to uninstall your eth0 driver.

You said you are using ndiswrapper, but did you install the driver using "ndiswrapper -i"??

can you post the output of "ndiswrapper -l" and "iwconfig" and "ifconfig", also the output of "more /etc/network/interfaces"

I suggest you read this page first. [https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

---

### Post by hockeyk242 on 2006-01-10
im having trouble with mine too, cept mine is a pci, and i did everything that it says on [https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29) but when i do step three, it says that the driver that i installed is an invalid driver.  im using ndiswrapper to install it.  any tips?

---

### Post by healychan on 2006-01-10
[QUOTE=hockeyk242]im having trouble with mine too, cept mine is a pci, and i did everything that it says on [https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29) but when i do step three, it says that the driver that i installed is an invalid driver.  im using ndiswrapper to install it.  any tips?[/QUOTE]
Post the output of "ndiswrapper -l" and "iwconfig" and "ifconfig", also the output of "more /etc/network/interfaces" please.

---

### Post by LinuxForTheWorld on 2006-01-13
[QUOTE=healychan]I don't think you need to uninstall your eth0 driver.

You said you are using ndiswrapper, but did you install the driver using "ndiswrapper -i"??

can you post the output of "ndiswrapper -l" and "iwconfig" and "ifconfig", also the output of "more /etc/network/interfaces"

I suggest you read this page first. [https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)[/QUOTE]

Yes I did.

chad@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
rt2500usb       driver present

chad@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

chad@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:7B:B0:73
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe7b:b073/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2477957 (2.3 MiB)  TX bytes:316255 (308.8 KiB)
          Interrupt:19 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372912 (364.1 KiB)  TX bytes:372912 (364.1 KiB)

chad@ubuntu:/etc$ more network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0


There you go. I sure hope you can help me.  Sorry it took me so long you probably gave up on me. Hope not.

Thanks,

---

### Post by trubblemaker on 2006-01-13
ok I'm not sure where your going wrong 'cause step 3 is ```
ndiswrapper -l
``` and that just listed a driver for you so I think you can now move onto the next step which is: 
```
sudo modprobe ndiswrapper
``` and continue on with the steps

---

### Post by healychan on 2006-01-14
[QUOTE=trubblemaker]ok I'm not sure where your going wrong 'cause step 3 is ```
ndiswrapper -l
``` and that just listed a driver for you so I think you can now move onto the next step which is: 
```
sudo modprobe ndiswrapper
``` and continue on with the steps[/QUOTE]
sudo modprobe ndiswrapper will load the ndiswrapper module. Give it a try first to see if it works.

Do "ndiswrapper -l" again, the result should say something like "hardware present". If you can see that phrase, try "iwconfig" to see if your network interface appears. Once you get the interface show up, you can move on to configure the interface.

---

