---
title: "broadcom on acer 3023"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by farno on 2006-07-13
hi. i'm a new italian member, then my english is not very good. i ask you o use simple word, please.
i have this problem:
when i boot my pc (with ubuntu dapper) i try to let start my wireless connection with the command:
sudo iwconfig eth1 ap any
but it doesn't start. if i push on the led the light turn on but i can't be able to connect.
if i reboot and i retry to give the command:
sudo iwconfig eth1 ap any
and this time the led turn on automatically and i can go on the net.

now i explain how i configured my wireless
i downloaded wl_apsta.o
then i gave this commands:
sudo apt-get install bcm43xx-fwcutter
sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta.o
sudo modprobe bcm43xx

then i configured acerhk (for the led) like this:
sudo depmod -a
modprobe acerhk autowlan=1 poll=0 verbose=3 usedritek=1
echo 1 > /proc/driver/acerhk/wirelessled

please help me

---

### Post by MarkSheely on 2006-07-14
Which Broadcom card do you have?  A BCM4318, or a BCM4308, or a different one?

The method you used to configure your wireless doesn't work for all Broadcom cards.  That may be part of the problem.

---

### Post by farno on 2006-07-14
bcm4318
i don't know which the problem because when i reboot card works perfectly
maybe it's better to use ndiswrapper then bcm43xx?

---

### Post by MarkSheely on 2006-07-14
Yes, with this card it is better to use ndiswrapper.  There is a great how-to here:

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

Good luck,
Mark

---

### Post by farno on 2006-07-15
thank's
i installed the broadcom driver with ndiswrapper (and i added bcm43xx to blacklist)
i added this command at startup:
sudo echo 1 > /proc/driver/acerhk/wirelessled
(i created a script that i added ti init.d)
then i added ndiswrapper e acerhk to /etc/modules
but i have the same problem:
i need to reboot to let start my connection
i don't like to boot twice everytime...
please help me

---

### Post by MarkSheely on 2006-07-15
I'm not sure why you're having that problem.  You might try posting in the thread I pointed you to above - there are people who visit that thread regularly with more knowledge than I have.

I'm sorry I couldn't help you more.  But, I am sure someone else will be able to.

--Mark

---

### Post by compwiz18 on 2006-07-16
Hi,

Can you run **ndiswrapper -l** (that is a lowercase L, not a 1 [one]) and **cat /etc/modules** and post the output please?

Thanks.

---

### Post by farno on 2006-07-16
the output of ndiswrapper -l is:
Installed ndis drivers:
bcmwl5          driver present, hardware present
and the /etc/modules is:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
acerhk
ndiswrapper

thank's

---

### Post by compwiz18 on 2006-07-16
**First**: Can anyone tell me more exactly what acerhk does???

@**farno**: Run **sudo gedit /etc/modules** and remove the acerhk line, so that it is not there anymore.  And don't worry, your English is fine :D EDIT: And then try and see if it works.

---

### Post by farno on 2006-07-16
i removed acerhk but the situation is exactly the same

---

### Post by farno on 2006-07-19
nobody?

---

### Post by compwiz18 on 2006-07-19
Can you try running **sudo iwlist eth1 scan** and **sudo ifconfig** and **cat /etc/network/interfaces** and post the output here? Thank you :D

---

### Post by farno on 2006-07-19
this are the output:
(sudo iwlist eth1 scan)
eth1      Scan completed :
          Cell 01 - Address: 00:C0:49:ED:12:30
                    ESSID:"USR8054"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-55 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
(sudo ifconfig)
eth1      Link encap:Ethernet  HWaddr 00:14:A4:61:BC:E2
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe61:bce2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:157040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:100288505 (95.6 MiB)  TX bytes:67820068 (64.6 MiB)
          Interrupt:177 Memory:c0204000-c0206000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5828992 (5.5 MiB)  TX bytes:5828992 (5.5 MiB)
(cat /etc/network/interfaces)
auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid USR8054

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1

thank's

---

### Post by compwiz18 on 2006-07-19
So your problem is that you have to start the computer, reboot it, and then you can use the computer, right?

Can you run **dmesg | grep ndiswrapper** and **dmesg | grep eth1** and post outputs please?  Thank you :D

---

### Post by farno on 2006-07-20
yes, i have to reboot to use mi wireless card
so this are the output
1)dmesg | grep ndiswrapper
[17179594.280000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179594.368000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[17179594.376000] ndiswrapper: using irq 177
[17179595.636000] wlan0: ndiswrapper ethernet device 00:14:a4:61:bc:e2 using driver bcmwl5, 14E4:4318:1468:0311.5.conf
2)dmesg | grep eth1
[17179607.672000] eth1: no IPv6 routers present

thank's for your help

---

### Post by farno on 2006-07-21
i solved...
but i don't know exactly how i did it.
thank's for your help

---

### Post by compwiz18 on 2006-07-21
That happens a lot, but as long as it works, that's good :D

---

### Post by mdoube on 2006-08-04
Hi Farno

I'm using Ubuntu Dapper with NetworkManager, bcm43xx and acerhk on an Acer Aspire 3023 WLMi  - of course, with the accursed BCM4318!

Try following the instructions posted at [my site]("http://doube.net/ubuntu3023.html"). It's not a perfect solution yet, but I don't have to reboot twice ;-)

I can't see any advantage of NDISWrapper. It worked OK when there was no bcm43xx driver, but now there is one, it's just another layer of complication. So, try the driver instead. It works for me; I'm posting this message with it now!

Once you have NDISWrapper gone, and bcm43xx installed, you have to do this each time the connection changes:

1) Disable networking from nm-applet right click menu
2) run this:
] sudo modprobe -r bcm43xx; sudo modprobe bcm43xx; echo 1 > /proc/driver/acerhk/wirelessled
3) Enable networking from the nm-applet right click menu
4) It works.

Good luck

Mike

---

### Post by farno on 2006-08-13
i found a better solution
my card now works everytime i boot without do nothing

it's important to follow this instructions in that order:
to let function my led give this three commands:
sudo depmod -a
sudo modprobe acerhk autowlan=1 poll=0 verbose=3 usedritek=1
sudo echo 1 > /proc/driver/acerhk/wirelessled
then i created this script (start.wifi):
#!/bin/sh
modprobe acerhk autowlan=1 poll=0 verbose=3 usedritek=1
echo 1 > /proc/driver/acerhk/wirelessled
iwconfig eth1 ap any
then i gave this commands:
chmod 755 start.wifi
sudo mv start.wifi /etc/init.d/
sudo ln -s /etc/init.d/start.wifi /etc/rcS.d/S50start.wifi
then i installed the driver
i downloaded wl_apsta.o (i don't remember where)
sudo apt-get install bcm43xx-fwcutter
sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta.o
sudo apt-get install bcm43xx-fwcutter
that's all

---

