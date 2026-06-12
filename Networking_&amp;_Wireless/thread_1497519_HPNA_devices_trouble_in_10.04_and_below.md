---
title: "HPNA devices trouble in 10.04 and below"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by isync on 2010-05-30
Hi there,

for weeks now I am trying to get some older HomePNA devices to work with Ubuntu in various flavours. A 3COM 3c420 USB HPNA to LAN adapter and a ALLNET ALL0187 USB HPNA to LAN adapter. With both device I had zero luck.

The **3COM** seems to be based on a broadcom chip with the id 0506:4200, which is apparently used in a number of devices, the D-Link DHL-120, the 3COM 3C420 which I own and some more.

It is not recognized by Ubuntu out of the box, not in 10.04 i386 and not in the older 7.04 i386. I tried to get it to work with its ancient Windows drivers via ndiswrapper 1.56 whcih detect the device and tells me the driver is installed and the hardware is present. It further registers the device as wlan0 after *sudo modpobe ndiswrapper* and properly shows as being managing the device in *lshw Network*.

Some source seem to be indicating that older ndiswrapper versions would enable the driver. Versions prior to 1.20! I don't know which thing makes them work while newer versions break support for (some) Windows 98 drivers. Still, I couldn't get ndiswrapper versions older than ~ 1.3x to compile under 10.04 and 7.04, compare this thread [here]("http://ubuntuforums.org/showthread.php?t=55185").

Still, pings tell me "network not reachable" and I get zero packets out.

The **ALLNET** seems to be more compatible. As a number other devices it seems to be based on the ADMtek 8511 chipset, and as such should be supported out of the box. And yes, Ubuntu properly assigns the pegasus II driver to manage it, but with no success. Zero ping success, zero packets out.

Doing a similar limbo as above with ndiswrapper and the Windows driver gave similar unsuccessful results.

Any help?
(3Com Windows 98 driver attached)

---

### Post by chili555 on 2010-05-30
I used HPNA in 2001, when Linux was hard. Beyond that, I have no further experience with these devices. I saw this:```
$ modinfo pegasus
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/net/usb/pegasus.ko
license:        GPL
description:    Pegasus/Pegasus II USB Ethernet driver
author:         Petko Manolov <petkan@users.sourceforge.net>
srcversion:     DBDDB8CA0D48A394D8A2E5C
alias:          usb:v067Cp1001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15E8p9110d*dc*dsc*dp*ic*isc*ip*
         ---snip---
alias:          usb:v0506p4601d*dc*dsc*dp*ic*isc*ip*
depends:        mii
vermagic:       2.6.32-22-generic SMP mod_unload modversions 586 
parm:           loopback:Enable MAC loopback mode (bit 0) (bool)
[COLOR="Red"]parm:           mii_mode:Enable HomePNA mode[/COLOR] (bit 0),default=MII mode = 0 (bool)
parm:           devid:The format is: 'DEV_name:VendorID:DeviceID:Flags' (charp)
parm:           msg_level:Override default message level (int)
```I then read this: [http://ubuntuforums.org/showthread.php?t=24695](http://ubuntuforums.org/showthread.php?t=24695)

You might do:```
sudo gedit /etc/modprobe.d/pegasus.conf
```Add two lines:```
alias wlan0 pegasus
options pegasus mii_mode=1
```Proofread, save and close. Then reload the module:```
sudo rmmod -f pegasus
sudo modprobe pegasus
```Any improvement?

---

### Post by isync on 2010-05-30
I had my stint with the mii mode thing (followed directions from exactly the thread you mentioned), and tried it in 1 and 0...

I am not sure if my options actually "reached" the driver, but this made no difference. Anyway, when I get the chance to try the ADMtek based device again, I will exactly duplicate your steps and check again.

Any ideas for the 3Com device?

And what is this [here]("http://ubuntuforums.org/showthread.php?t=193167"), with forcing the ethernet device via /etc/modules into hpna mode? Is this the same as the mii mode??

---

### Post by chili555 on 2010-05-30
> Any ideas for the 3Com device?None.> And what is this here, with forcing the ethernet device via /etc/modules into hpna mode? Is this the same as the mii mode?? The same idea, but the wrong way to do it in 2010.

You could certainly try it the temporary way:```
sudo rmmod -f pegasus
sudo modprobe pegasus mii_mode=1
```Afterwards, I'd check /var/log/syslog for any clues:```
sudo cat /var/log/syslog | grep pegasus
```I am not at all sure the /etc/modules method will reach the driver, either, if it's already loaded. While I have not tried an HPNA device in ages, I am quite sure the modprobe.d method works correctly for wireless drivers and I see no reason why it shouldn't for yours.

Substitute the interface identifier that gets created if it's not wlan0; I'm confident it's not.

---

### Post by isync on 2010-06-01
So after your posts I entered round two...

and syslog tells me:
```
read_mii_word failed
set_registers, status -22
update_eth_regs_async, status -22
```

Which I had read before, here [error -19]("http://www.linuxquestions.org/questions/linux-hardware-18/problem-with-adm8511-pegasus-ii-usb-ethernet-converter-fc5-510300/"), and here [error code -22]("http://www.linuxquestions.org/questions/linux-networking-3/problem-with-admtek-adm8511-usb-homepna-adapter-pegasus-ii-driver-582002/")...

going thorugh ifconfig and lshw I thought I noticed that I wasn't able to actually unload the pegasus module as long as the device was plugged in. Which motivated me to do an unplug, then *sudo modpobe -r pegasus*.

Then I reconfigured pegasus for future loads by editing sudo *nano /etc/modprobe.d/pegasus.conf* with
```
alias eth1 pegasus
options pegasus mii_mode=1
```

Then I made a reload of pegasus via *sudo modprobe pegasus*

And re-attached the device, syslog then logs:
```
new ethernet device (driver: pegas)
...
now managed
device state change 1-2 (reason 2)
bringing up device
deactivating device (reason: 2)

```

After that I can't reactivate the device with *sudo ifconfig eth1 up*. I get: "SIOCSIFFLAGS up: cannot assign requested address". Huh? Wrong ifconfig syntax?

/etc/modprobe.d/pegasus.conf is actually properly loaded/accessed by the driver loading, as a sneaked in homepna=1 instead of mii_mode=1 brought up a warning...

No ping successes- ever....

BTW: I am doing all this under Ubuntu 10.04 LiveCD. As long as this device isn't running, this box will continue to run Windoze. :( Any implications for the issues? Would a boot with the options for pegasus set change the game?



[INDENT]Some sidetrack ramblings:

After reading [this (ndiswrapper for ADM8511 instead of pegasus) here]("http://dev.doorul.com/2008/11/ndiswrapper-rocks.html") I tried this route as well. Result was, lshw properly stated that ndiswrapper+ADM8511 would be managing the device, but the hpna LED on the adapter didn't come up again and in dmesg I dug up the error "Link not present".

Anyone? Is it because this guy used ndiswrapper 1.53 and I tried with 10.04's 1.55? Is the Trendnet Variant of the ADM8511 so much different from my Allnet? What changed since Nov 2008 when this blog post was done??[/INDENT]

---

### Post by chili555 on 2010-06-01
> I am doing all this under Ubuntu 10.04 LiveCD. As long as this device isn't running, this box will continue to run Windoze.  Any implications for the issues? Would a boot with the options for pegasus set change the game?Not really. In my experience, with a very few exceptions, if it works live, it works installed and vice-versa. 

I would love to see the result of:```
sudo cat /var/log/syslog | grep pegasus
```I also think that, because you have had two devices installed, that udev may have named the latter one eth[COLOR="Red"]2[/COLOR] or some such. I am therefor not persuaded by:> sudo ifconfig eth1 up. I get: "SIOCSIFFLAGS up: cannot assign requested address". I am running low on talent. My expertise on HPNA expired many years ago. It is a fascinating technology, however.

---

### Post by isync on 2010-06-01
Device pluged in and connected to hpna line.
Fresh boot into Ubuntu Desktop 10.04 LiveCD.

```
ubuntu@ubuntu:~$ sudo cat /var/log/syslog | grep pegasus
Jun  2 01:53:51 ubuntu kernel: [   60.915963] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
Jun  2 01:53:51 ubuntu kernel: [   60.951838] pegasus 2-1:1.0: setup Pegasus II specific registers
Jun  2 01:53:51 ubuntu kernel: [   61.155083] pegasus 2-1:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:e0:7d:9b:9d:b1
Jun  2 01:53:51 ubuntu kernel: [   61.155146] usbcore: registered new interface driver pegasus
Jun  2 01:53:54 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'pegasus')
Jun  2 01:53:54 ubuntu kernel: [   63.834416] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 01:53:54 ubuntu kernel: [   63.834481] pegasus 2-1:1.0: update_eth_regs_async, status -22
```

```
ubuntu@ubuntu:~$ lshw -C Network 
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: ISDN network controller [HFC-PCI]
       vendor: Cologne Chip Designs GmbH
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: driver=hfcpci latency=16 maxlatency=16
       resources: irq:16 ioport:9000(size=8) memory:e6004000-e60040ff
  *-network:1
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:20:ed:1f:33:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:e6008000-e6008fff ioport:9400(size=64)
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: eth1
       serial: 00:e0:7d:9b:9d:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=pegasus driverversion=v0.6.14 (2006/09/27) multicast=yes
```

```
sudo lsusb -v
Bus 002 Device 002: ID 07a6:8511 ADMtek, Inc. ADM8511 Pegasus II Ethernet
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x07a6 ADMtek, Inc.
  idProduct          0x8511 ADM8511 Pegasus II Ethernet
  bcdDevice            1.01
  iManufacturer           1 ADMtek
  iProduct                2 USB To LAN Converter
  iSerial                 3 0001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              160mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)
```

sudo nano /etc/modprobe.d/options
```
alias eth1 pegasus
options pegasus mii_mode=1
```

after that sudo modprobe pegasus && sudo /etc/init.d/networking restart
No success.

What puzzles me is:
```
sudo modprobe -r pegasus
ubuntu@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: ISDN network controller [HFC-PCI]
       vendor: Cologne Chip Designs GmbH
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: driver=hfcpci latency=16 maxlatency=16
       resources: irq:16 ioport:9000(size=8) memory:e6004000-e60040ff
  *-network:1
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:20:ed:1f:33:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:e6008000-e6008fff ioport:9400(size=64)
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: eth1
       serial: 00:e0:7d:9b:9d:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=pegasus driverversion=v0.6.14 (2006/09/27) multicast=yes

```
That even after modprobe -r pegasus is still liested as managing driver...
Anyway, continuing with:
```
ubuntu@ubuntu:~$ sudo modprobe pegasus
ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                      [ OK ] 
ubuntu@ubuntu:~$ ping 192.168.1.1 -I eth1
connect: Network is unreachable



Jun  2 02:09:59 ubuntu kernel: [ 1029.309535] usbcore: deregistering interface driver pegasus
Jun  2 02:10:00 ubuntu kernel: [ 1029.647323] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
Jun  2 02:10:00 ubuntu kernel: [ 1029.679201] pegasus 2-1:1.0: setup Pegasus II specific registers
Jun  2 02:10:00 ubuntu kernel: [ 1029.839645] pegasus 2-1:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:e0:7d:9b:9d:b1
Jun  2 02:10:00 ubuntu kernel: [ 1029.839941] usbcore: registered new interface driver pegasus
Jun  2 02:10:00 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'pegasus')
Jun  2 02:10:00 ubuntu kernel: [ 1029.944191] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 02:10:00 ubuntu kernel: [ 1029.944271] pegasus 2-1:1.0: update_eth_regs_async, status -22


ubuntu@ubuntu:~$ sudo ifconfig eth1 192.168.1.66 netmask 255.255.255.0
ubuntu@ubuntu:~$ ping 192.168.1.1 -I eth1
PING 192.168.1.1 (192.168.1.1) from 192.168.1.66 eth1: 56(84) bytes of data.
From 192.168.1.66 icmp_seq=1 Destination Host Unreachable
From 192.168.1.66 icmp_seq=2 Destination Host Unreachable
From 192.168.1.66 icmp_seq=3 Destination Host Unreachable
```


Then accidentally I dialed in the IP of my router...
```
ubuntu@ubuntu:~$ sudo ifconfig eth1 down
ubuntu@ubuntu:~$ sudo modprobe -r pegasus
ubuntu@ubuntu:~$ sudo modprobe pegasus
ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                      [ OK ] 
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:20:ed:1f:33:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  Hardware Adresse 00:e0:7d:9b:9d:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:1686 (1.6 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:12112 (12.1 KB)  TX bytes:12112 (12.1 KB)

ubuntu@ubuntu:~$ sudo ifconfig eth1 up
ubuntu@ubuntu:~$ sudo ifconfig eth1 192.168.1.1 netmask 255.255.255.0
ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                      [ OK ] 
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:20:ed:1f:33:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  Hardware Adresse 00:e0:7d:9b:9d:b1  
          inet Adresse:192.168.1.1  Bcast:192.168.1.255  Maske:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:3972 (3.9 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:12112 (12.1 KB)  TX bytes:12112 (12.1 KB)

ubuntu@ubuntu:~$ ping 192.168.1.1 -I eth1
PING 192.168.1.1 (192.168.1.1) from 192.168.1.1 eth1: 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.063 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.044 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.044 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.052 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.053 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.048 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.054 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.051 ms

```


When I reverted this and down'ed eth0 just to be sure, this was agin the result:
```
ubuntu@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  Hardware Adresse 00:e0:7d:9b:9d:b1  
          inet Adresse:192.168.1.1  Bcast:192.168.1.255  Maske:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:33528 (33.5 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:787 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:63772 (63.7 KB)  TX bytes:63772 (63.7 KB)

ubuntu@ubuntu:~$ sudo ifconfig eth1 192.168.1.56 netmask 255.255.255.0
ubuntu@ubuntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.56 icmp_seq=1 Destination Host Unreachable
```


Does the ability to reach the machine itself on 192.168.1.1 mean hpna is basically working, or is this just the loopback simulating traffic on the line?

I am still wondering how the section "RX packets:28" came across. At that time I had the device set to IP 192.168.1.66 and ping had no success, still, packets were counted. Were these the unsuccessful packages of the ping?

Could it be that the device "likes" my hpna line under Windows, but "doesn't like" it under the Linux driver? In the past I had issues with my hpna line. Could it be that the Windows driver compensates these and pegasus doesn't?

---

### Post by chili555 on 2010-06-01
Does this tell us a link is detected? Is there any other interesting information?```
sudo ethtool eth1
```What is the result of:```
sudo /etc/init.d/network-manager stop
sudo dhclient eth1
```When you set the IP address to 192.168.1.1 and then ping that same address, you are just pinging yourself. You mailed a letter to yourself and you got the letter, but the post office never handled it. It's basically meaningless.

If you left-click the Network Manager icon, do you see the option to connect? Have you tried?

Again, all the settings look really good; I see nothing to dislike.

---

### Post by isync on 2010-06-02
After a fresh boot into 10.04, device was connected, "hpna" LED now lit:

```
ubuntu@ubuntu:~$ sudo cat /var/log/syslog | grep pegasus
Jun  2 13:19:06 ubuntu kernel: [   61.363118] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
Jun  2 13:19:06 ubuntu kernel: [   61.394951] pegasus 2-1:1.0: setup Pegasus II specific registers
Jun  2 13:19:06 ubuntu kernel: [   61.595267] pegasus 2-1:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:e0:7d:9b:9d:b1
Jun  2 13:19:06 ubuntu kernel: [   61.595387] usbcore: registered new interface driver pegasus
Jun  2 13:19:09 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'pegasus')
Jun  2 13:19:09 ubuntu kernel: [   64.272852] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 13:19:09 ubuntu kernel: [   64.272919] pegasus 2-1:1.0: update_eth_regs_async, status -22

ubuntu@ubuntu:~$ sudo cat /var/log/syslog | grep eth1
Jun  2 13:19:06 ubuntu kernel: [   61.595267] pegasus 2-1:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:e0:7d:9b:9d:b1
Jun  2 13:19:08 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-1/2-1:1.0/net/eth1, iface: eth1)
Jun  2 13:19:08 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-1/2-1:1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun  2 13:19:09 ubuntu NetworkManager: <info>  (eth1): carrier is OFF
Jun  2 13:19:09 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'pegasus')
Jun  2 13:19:09 ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  2 13:19:09 ubuntu NetworkManager: <info>  (eth1): now managed
Jun  2 13:19:09 ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Jun  2 13:19:09 ubuntu NetworkManager: <info>  (eth1): bringing up device.
Jun  2 13:19:09 ubuntu NetworkManager: <info>  (eth1): preparing device.
Jun  2 13:19:09 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jun  2 13:19:09 ubuntu kernel: [   64.272912] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  2 13:19:09 ubuntu NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-1/2-1:1.0/net/eth1
Jun  2 13:19:09 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-1/2-1:1.0/net/eth1, iface: eth1)
Jun  2 13:19:09 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-1/2-1:1.0/net/eth1, iface: eth1): no ifupdown configuration found.

sudo modinfo pegasus
filename:       /lib/modules/2.6.32-21-generic/kernel/drivers/net/usb/pegasus.ko
license:        GPL
description:    Pegasus/Pegasus II USB Ethernet driver
author:         Petko Manolov <petkan@users.sourceforge.net>
srcversion:     DBDDB8CA0D48A394D8A2E5C
alias:          usb:v067Cp1001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15E8p9110d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15E8p9100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707p0201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707p0200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08D1p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B39p0901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B39p0109d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p1020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v045Ep007Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v066Bp200Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v066Bp400Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v077Bp08B4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v066Bp2206d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v066Bp2204d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v066Bp2203d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v066Bp2202d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ep200Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056EpABC1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ep400Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ep4005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ep4002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0951p000Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp092Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0913d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0904d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p811Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p400Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05CCp3000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1342p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ep4010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB7p0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001pABC1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p4003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p200Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p400Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p4102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p4002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp8511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp0988d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v049Fp8511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp0987d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp0986d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp0121d*dc00dsc*dp*ic*isc*ip*
alias:          usb:v07C9pB100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3334p1701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07A6p07C2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07A6p0986d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07A6p8515d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07A6p8513d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07A6p8511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap5046d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap1046d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p200Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pABC1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p400Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p400Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p4002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p4102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p4007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p4004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p4104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p110Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0557p2007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0506p4601d*dc*dsc*dp*ic*isc*ip*
depends:        mii
vermagic:       2.6.32-21-generic SMP mod_unload modversions 586 
parm:           loopback:Enable MAC loopback mode (bit 0) (bool)
parm:           mii_mode:Enable HomePNA mode (bit 0),default=MII mode = 0 (bool)
parm:           devid:The format is: 'DEV_name:VendorID:DeviceID:Flags' (charp)
parm:           msg_level:Override default message level (int)
```



ethtool is not on the LiveCD and I've got no Internet (obviously) - sorry.


A click on the Netwrok-manager Icon (icon has an exclamation mark) shows the drop-down menu and has 
an entry:
Cable network (ADMtek USB to LAN converter)
  not connected

with "not connected" being greyed out, so I can't click it to connect.

When I was there I dug into the settings and dialed in a static IP for the device, my gateway etc.
Then I did a "deactivate network" via the drop down and a "activate network", resulting in a
"you are now offline" message and on activation again a "you are now offline" info. Which I think is 
in sync with the lower output of dmesg:

```
$ dmesg
[   64.272852] pegasus 2-1:1.0: update_eth_regs_async, status -22
[   64.272912] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   64.272919] pegasus 2-1:1.0: update_eth_regs_async, status -22
[   64.318070] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   66.159634] ENS1371 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   71.003292] lp0: using parport0 (interrupt-driven).
[   74.022554] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   74.023932] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   87.724065] end_request: I/O error, dev fd0, sector 0
[   87.920029] end_request: I/O error, dev fd0, sector 0
[  145.749916] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 1
[  151.029447] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[  151.030716] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[  917.925661] pegasus 2-1:1.0: update_eth_regs_async, status -22
[  917.925718] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  917.925725] pegasus 2-1:1.0: update_eth_regs_async, status -22
[  917.945989] ADDRCONF(NETDEV_UP): eth0: link is not ready
```


Then your requests:

```
ubuntu@ubuntu:~$ sudo /etc/init.d/network-manager stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
ubuntu@ubuntu:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:e0:7d:9b:9d:b1
Sending on   LPF/eth1/00:e0:7d:9b:9d:b1
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
^C
```


That eth1 still seems to be set on DHCP autodiscovery again hardens my belief that the GUI network-manager is crappy in terms of actually managing the network.
Proof:

```
ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:20:ed:1f:33:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  Hardware Adresse 00:e0:7d:9b:9d:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:11952 (11.9 KB)  TX bytes:11952 (11.9 KB)
```


No IP settings reached the device. So...

```
ubuntu@ubuntu:~$ sudo ifconfig eth1 192.168.1.66 netmask 255.255.255.0
ubuntu@ubuntu:~$ sudo ifconfig eth1 up
ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:20:ed:1f:33:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  Hardware Adresse 00:e0:7d:9b:9d:b1  
          inet Adresse:192.168.1.66  Bcast:192.168.1.255  Maske:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:11952 (11.9 KB)  TX bytes:11952 (11.9 KB)

ubuntu@ubuntu:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:e0:7d:9b:9d:b1
Sending on   LPF/eth1/00:e0:7d:9b:9d:b1
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
^C
ubuntu@ubuntu:~$ ping 192.168.1.1 -I eth1
connect: Network is unreachable

ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                                         [ OK ] 
ubuntu@ubuntu:~$ ping 192.168.1.1 -I eth1
connect: Network is unreachable
ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:20:ed:1f:33:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  Hardware Adresse 00:e0:7d:9b:9d:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:11952 (11.9 KB)  TX bytes:11952 (11.9 KB)
```


Then starting over again:

```
ubuntu@ubuntu:~$ sudo ifconfig eth1 down
ubuntu@ubuntu:~$ sudo modprobe -r pegasus
ubuntu@ubuntu:~$ sudo nano /etc/modprobe.d/pegasus.conf

  alias eth1 pegasus
  options pegasus mii_mode=1

ubuntu@ubuntu:~$ sudo modprobe pegasus
ubuntu@ubuntu:~$ sudo ifconfig eth1 up
ubuntu@ubuntu:~$ sudo ifconfig eth1 192.168.1.66 netmask 255.255.255.0
ubuntu@ubuntu:~$ sudo /etc/init.d/networking force-reload
 * Reconfiguring network interfaces...                                                                                                                                                         [ OK ] 
ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                                         [ OK ] 
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:20:ed:1f:33:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  Hardware Adresse 00:e0:7d:9b:9d:b1  
          inet Adresse:192.168.1.66  Bcast:192.168.1.255  Maske:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:4812 (4.8 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:11952 (11.9 KB)  TX bytes:11952 (11.9 KB)

ubuntu@ubuntu:~$ ping 192.168.1.1 -I eth1
PING 192.168.1.1 (192.168.1.1) from 192.168.1.66 eth1: 56(84) bytes of data.
From 192.168.1.66 icmp_seq=1 Destination Host Unreachable
From 192.168.1.66 icmp_seq=2 Destination Host Unreachable
From 192.168.1.66 icmp_seq=3 Destination Host Unreachable
^C
```

Strangely network unreachable is now "destination host unreachable" but is this any better... :(


$ sudo cat /var/log/syslog of the above operation (doknow where exactly my actions start):
```
Jun  2 13:40:32 ubuntu avahi-daemon[1466]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.66.
Jun  2 13:40:32 ubuntu avahi-daemon[1466]: New relevant interface eth1.IPv4 for mDNS.
Jun  2 13:40:32 ubuntu avahi-daemon[1466]: Registering new address record for 192.168.1.66 on eth1.IPv4.
Jun  2 13:41:20 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jun  2 13:41:20 ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jun  2 13:41:20 ubuntu dhclient: All rights reserved.
Jun  2 13:41:20 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  2 13:41:20 ubuntu dhclient: 
Jun  2 13:41:20 ubuntu avahi-daemon[1466]: Withdrawing address record for 192.168.1.66 on eth1.
Jun  2 13:41:20 ubuntu avahi-daemon[1466]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.66.
Jun  2 13:41:20 ubuntu avahi-daemon[1466]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  2 13:41:20 ubuntu kernel: [ 1395.287099] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 13:41:20 ubuntu kernel: [ 1395.287116] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 13:41:20 ubuntu dhclient: Listening on LPF/eth1/00:e0:7d:9b:9d:b1
Jun  2 13:41:20 ubuntu dhclient: Sending on   LPF/eth1/00:e0:7d:9b:9d:b1
Jun  2 13:41:20 ubuntu dhclient: Sending on   Socket/fallback
Jun  2 13:41:21 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jun  2 13:41:25 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jun  2 13:41:30 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Jun  2 13:41:42 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
Jun  2 13:43:34 ubuntu kernel: [ 1529.276732] usbcore: deregistering interface driver pegasus
Jun  2 13:43:34 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-1/2-1:1.0/net/eth1, iface: eth1)
Jun  2 13:43:34 ubuntu NetworkManager: <info>  (eth1): now unmanaged
Jun  2 13:43:34 ubuntu NetworkManager: <info>  (eth1): device state change: 2 -> 1 (reason 36)
Jun  2 13:43:34 ubuntu NetworkManager: <info>  (eth1): cleaning up...
Jun  2 13:43:40 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  2 13:43:40 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  2 13:45:33 ubuntu kernel: [ 1647.821704] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
Jun  2 13:45:33 ubuntu kernel: [ 1647.853852] pegasus 2-1:1.0: setup Pegasus II specific registers
Jun  2 13:45:33 ubuntu kernel: [ 1648.023098] pegasus 2-1:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:e0:7d:9b:9d:b1
Jun  2 13:45:33 ubuntu kernel: [ 1648.024440] usbcore: registered new interface driver pegasus
Jun  2 13:45:33 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-1/2-1:1.0/net/eth1, iface: eth1)
Jun  2 13:45:33 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-1/2-1:1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun  2 13:45:33 ubuntu NetworkManager: <info>  (eth1): carrier is OFF
Jun  2 13:45:33 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'pegasus')
Jun  2 13:45:33 ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Jun  2 13:45:37 ubuntu NetworkManager: <info>  (eth1): now managed
Jun  2 13:45:37 ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Jun  2 13:45:37 ubuntu NetworkManager: <info>  (eth1): bringing up device.
Jun  2 13:45:37 ubuntu NetworkManager: <info>  (eth1): preparing device.
Jun  2 13:45:37 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jun  2 13:45:37 ubuntu kernel: [ 1652.358781] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 13:45:37 ubuntu kernel: [ 1652.358836] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  2 13:45:37 ubuntu kernel: [ 1652.358843] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 13:46:15 ubuntu avahi-daemon[1466]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.66.
Jun  2 13:46:15 ubuntu avahi-daemon[1466]: New relevant interface eth1.IPv4 for mDNS.
Jun  2 13:46:15 ubuntu avahi-daemon[1466]: Registering new address record for 192.168.1.66 on eth1.IPv4.
Jun  2 13:46:15 ubuntu kernel: [ 1689.643571] pegasus 2-1:1.0: update_eth_regs_async, status -22
```

and modinfo after the mii_mode=1 introduction:
```
ubuntu@ubuntu:~$ sudo modinfo pegasus
filename:       /lib/modules/2.6.32-21-generic/kernel/drivers/net/usb/pegasus.ko
license:        GPL
description:    Pegasus/Pegasus II USB Ethernet driver
author:         Petko Manolov <petkan@users.sourceforge.net>
srcversion:     DBDDB8CA0D48A394D8A2E5C
alias:          usb:v067Cp1001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15E8p9110d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15E8p9100d*dc*dsc*dp*ic*isc*ip*
...snip...
alias:          usb:v0506p4601d*dc*dsc*dp*ic*isc*ip*
depends:        mii
vermagic:       2.6.32-21-generic SMP mod_unload modversions 586 
parm:           loopback:Enable MAC loopback mode (bit 0) (bool)
parm:           mii_mode:Enable HomePNA mode (bit 0),default=MII mode = 0 (bool)
parm:           devid:The format is: 'DEV_name:VendorID:DeviceID:Flags' (charp)
parm:           msg_level:Override default message level (int)
```


Now something radical - disconnecting and re- plugging in the device:

```
ubuntu@ubuntu:~$ tail -f /var/log/syslog
Jun  2 13:45:37 ubuntu NetworkManager: <info>  (eth1): bringing up device.
Jun  2 13:45:37 ubuntu NetworkManager: <info>  (eth1): preparing device.
Jun  2 13:45:37 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jun  2 13:45:37 ubuntu kernel: [ 1652.358781] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 13:45:37 ubuntu kernel: [ 1652.358836] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  2 13:45:37 ubuntu kernel: [ 1652.358843] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 13:46:15 ubuntu avahi-daemon[1466]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.66.
Jun  2 13:46:15 ubuntu avahi-daemon[1466]: New relevant interface eth1.IPv4 for mDNS.
Jun  2 13:46:15 ubuntu avahi-daemon[1466]: Registering new address record for 192.168.1.66 on eth1.IPv4.
Jun  2 13:46:15 ubuntu kernel: [ 1689.643571] pegasus 2-1:1.0: update_eth_regs_async, status -22
Jun  2 13:53:04 ubuntu kernel: [ 2099.254011] usb 2-1: USB disconnect, address 2
Jun  2 13:53:04 ubuntu avahi-daemon[1466]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  2 13:53:04 ubuntu avahi-daemon[1466]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.66.
Jun  2 13:53:04 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-1/2-1:1.0/net/eth1, iface: eth1)
Jun  2 13:53:04 ubuntu NetworkManager: <info>  (eth1): now unmanaged
Jun  2 13:53:04 ubuntu NetworkManager: <info>  (eth1): device state change: 2 -> 1 (reason 36)
Jun  2 13:53:04 ubuntu NetworkManager: <info>  (eth1): cleaning up...
Jun  2 13:53:04 ubuntu avahi-daemon[1466]: Withdrawing address record for 192.168.1.66 on eth1.
Jun  2 13:53:04 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

--cable was out here--

Jun  2 13:53:04 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  2 13:53:35 ubuntu kernel: [ 2130.440022] usb 2-2: new full speed USB device using ohci_hcd and address 3
Jun  2 13:53:36 ubuntu kernel: [ 2130.661186] usb 2-2: configuration #1 chosen from 1 choice
Jun  2 13:53:36 ubuntu kernel: [ 2130.711953] pegasus 2-2:1.0: setup Pegasus II specific registers
Jun  2 13:53:36 ubuntu kernel: [ 2130.872543] pegasus 2-2:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:e0:7d:9b:9d:b1
Jun  2 13:53:36 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-2/2-2:1.0/net/eth1, iface: eth1)
Jun  2 13:53:36 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/usb2/2-2/2-2:1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun  2 13:53:36 ubuntu NetworkManager: <info>  (eth1): carrier is OFF
Jun  2 13:53:36 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'pegasus')
Jun  2 13:53:36 ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/3
Jun  2 13:53:36 ubuntu NetworkManager: <info>  (eth1): now managed
Jun  2 13:53:36 ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Jun  2 13:53:36 ubuntu NetworkManager: <info>  (eth1): bringing up device.
Jun  2 13:53:36 ubuntu NetworkManager: <info>  (eth1): preparing device.
Jun  2 13:53:36 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jun  2 13:53:36 ubuntu kernel: [ 2130.957982] pegasus 2-2:1.0: update_eth_regs_async, status -22
Jun  2 13:53:36 ubuntu kernel: [ 2130.958036] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  2 13:53:36 ubuntu kernel: [ 2130.958042] pegasus 2-2:1.0: update_eth_regs_async, status -22
```


Then on:

```
^C
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:20:ed:1f:33:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  Hardware Adresse 00:e0:7d:9b:9d:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:6558 (6.5 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:12512 (12.5 KB)  TX bytes:12512 (12.5 KB)

ubuntu@ubuntu:~$ ping 192.168.1.1 -I eth1
connect: Network is unreachable
ubuntu@ubuntu:~$ sudo ifconfig eth1 192.168.1.66 netmask 255.255.255.0
ubuntu@ubuntu:~$ ping 192.168.1.1 -I eth1
PING 192.168.1.1 (192.168.1.1) from 192.168.1.66 eth1: 56(84) bytes of data.
From 192.168.1.66 icmp_seq=1 Destination Host Unreachable
From 192.168.1.66 icmp_seq=2 Destination Host Unreachable
From 192.168.1.66 icmp_seq=3 Destination Host Unreachable
```



Strangely this:
ubuntu@ubuntu:~$ sudo nano /etc/modprobe.d/pegasus.conf

 and setting mii_mode=0

there gives me this same picture:

```
ubuntu@ubuntu:~$ sudo modprobe -r pegasus
ubuntu@ubuntu:~$ sudo modprobe pegasus
ubuntu@ubuntu:~$ sudo modinfo pegasus
filename:       /lib/modules/2.6.32-21-generic/kernel/drivers/net/usb/pegasus.ko
license:        GPL
description:    Pegasus/Pegasus II USB Ethernet driver
author:         Petko Manolov <petkan@users.sourceforge.net>
srcversion:     DBDDB8CA0D48A394D8A2E5C
alias:          usb:v067Cp1001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15E8p9110d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15E8p9100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707p0201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707p0200d*dc*dsc*dp*ic*isc*ip*
 ....
alias:          usb:v0557p2007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0506p4601d*dc*dsc*dp*ic*isc*ip*
depends:        mii
vermagic:       2.6.32-21-generic SMP mod_unload modversions 586 
parm:           loopback:Enable MAC loopback mode (bit 0) (bool)
parm:           mii_mode:Enable HomePNA mode (bit 0),default=MII mode = 0 (bool)
parm:           devid:The format is: 'DEV_name:VendorID:DeviceID:Flags' (charp)
parm:           msg_level:Override default message level (int)
```



then I was ready to rip everything out...
sudo modprobe -r pegasus
ndiswrapper -i NET8511.INF
ndiswrapper -l
 installed and present
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart

strangely lshw and ifconfig showed me pegasus was still managing the device, and no action stopped it from doing so.
As last resort I disconnected and reconnected the device and - ndiswrapper took over!

```
$ dmesg
[ 3179.382271] usb 2-2: USB disconnect, address 3
[ 3184.276027] usb 3-1: new full speed USB device using ohci_hcd and address 2
[ 3184.497178] usb 3-1: configuration #1 chosen from 1 choice
[ 3184.696025] usb 3-1: reset full speed USB device using ohci_hcd and address 2
[ 3184.908299] ndiswrapper: driver net8511 (ADMtek Incorp.,08/30/2000, 2.00.830.2000) loaded
[ 3188.257161] wlan0: ethernet device 00:e0:7d:9b:9d:b1 using NDIS driver: net8511, version: 0x205, NDIS version: 0x500, vendor: 'NET8511 USB To Fast Ethernet Adapter NDIS 5.0 Miniport Driver', 07A6:8511.F.conf
[ 3188.338228] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3188.534939] usb 3-1: USB disconnect, address 2
[ 3190.012084] ndiswrapper: device wlan0 removed
[ 3192.612033] usb 2-2: new full speed USB device using ohci_hcd and address 4
[ 3192.833191] usb 2-2: configuration #1 chosen from 1 choice
[ 3193.036033] usb 2-2: reset full speed USB device using ohci_hcd and address 4
[ 3193.248340] ndiswrapper: driver net8511 (ADMtek Incorp.,08/30/2000, 2.00.830.2000) loaded
[ 3196.594914] wlan0: ethernet device 00:e0:7d:9b:9d:b1 using NDIS driver: net8511, version: 0x205, NDIS version: 0x500, vendor: 'NET8511 USB To Fast Ethernet Adapter NDIS 5.0 Miniport Driver', 07A6:8511.F.conf
[ 3196.620709] ADDRCONF(NETDEV_UP): wlan0: link is not ready
ubuntu@ubuntu:/$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:20:ed:1f:33:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:13072 (13.0 KB)  TX bytes:13072 (13.0 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:e0:7d:9b:9d:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:/$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: ISDN network controller [HFC-PCI]
       vendor: Cologne Chip Designs GmbH
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: driver=hfcpci latency=16 maxlatency=16
       resources: irq:16 ioport:9000(size=8) memory:e6004000-e60040ff
  *-network:1
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:20:ed:1f:33:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:e6008000-e6008fff ioport:9400(size=64)
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: wlan0
       serial: 00:e0:7d:9b:9d:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ndiswrapper+net8511 driverversion=1.55+ADMtek Incorp.,08/30/2000, multicast=yes
```

But the hpna LED on the unit was dark.
Network still dead.
Desperation kicked in...

And Windows dancing on my grave with this same machine booted into Windows, over the same HPNA line - obviously working! Giving knowledge about drivers and C, the time I've spent so far trying to get this to work, I've could had written a linux driver for it!!

---

### Post by chili555 on 2010-06-02
> <info>  (eth1): carrier is OFFNot sure what this tells us.

*modinfo* only tells you details about the driver; version number, authors, which devices it attaches, parameters that may be passed, et al. It won't change as you add and remove parameters and is not a source of clues except to learn if there are other, more useful parameters that have not yet been tried.

Network Manager is set as DHCP by default because most people use it and want it just that way. Ask 95% of users here why they might want a static IP address and what to do about resolv.conf and you'll get a blank stare. This is a new world. The noobs want Linux to be just like Windows, but free. Free of cost and free of virii.

Yuck!

I don't know what else to suggest. As I've said, I ran out of talent in HPNA about seven years ago. I am happy to help in any way I can, but, beyond a general understanding of HPNA, Ubuntu and driver modules, I am not sure I have any silver bullets.

---

### Post by isync on 2010-06-02
You've been a great sport and donated far too much of your time already. I think am am lost here. So thank you very much!

I've noticed this "*<info> (eth1): carrier is OFF*" as well. I will see when I'll find the nerves to drill more into this direction. If ever...

Anyway,
thanks a lot!

---

