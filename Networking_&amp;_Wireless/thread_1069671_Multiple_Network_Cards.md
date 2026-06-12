---
title: "Multiple Network Cards"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by pramod.gangoor on 2009-02-14
Hello All,

I am new to Ubuntu (in Linux) and unable to connect multiple NIC's in it

Earlier I tried using USB to Ethernet and wasn't successful. I am now using PCI NIC card and still getting error - when I type ifconfig eth1 it doesn't display.

One NIC is connected to DSL and other one is connected to my home router.

Can someone please help me on how to set this up.
__________________________________________________________________
I got migrated from Windows to Linux so that I could use (Dynamips); however these few things are unable to complete my setup. 
I would be really appreciate if anyone could help me with both things.

Thanks a lot :-)

---

### Post by theozzlives on 2009-02-14
Connect the DSL to the input on the router, and your PC(s) to the router.

---

### Post by pramod.gangoor on 2009-02-14
oops, Looks like I confused you...

DSL connection works fine. When I connect cable from my router (lab) to other NIC it doesn't work.

I swapped to both NIC and was able to use connection from DSL.

---

### Post by superprash2003 on 2009-02-14
could you be a bit more elaborate.. i didnt quite get you!!

---

### Post by pramod.gangoor on 2009-02-15
I'm trying to connect multiple NIC. When I tried using automatically get from DHCP it didn't work( Only one NIC used to get IP address). I was able to get workaround by assigning static to other NIC.

Could you please help in getting me work with USB to Ethernet. I see the system is detecting the device but unable to use device. 

I am using Ubuntu 8.1

---

### Post by superprash2003 on 2009-02-15
post the output of **ifconfig **from the terminal

---

### Post by pramod.gangoor on 2009-02-15
Here's the ifconfig output. Ethernet 2 (USB to Ethernet ) is one causing problem

eth0      Link encap:Ethernet  HWaddr 00:19:d1:fb:66:e5  
          inet addr:10.10.10.101  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fefb:66e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18704 (18.7 KB)  TX bytes:17272 (17.2 KB)
          Interrupt:222 Base address:0x2000 

eth2      Link encap:Ethernet  HWaddr 00:60:6e:00:02:e4  
          inet addr:172.16.160.160  Bcast:172.16.160.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth3      Link encap:Ethernet  HWaddr 00:e0:20:97:63:c7  
          inet6 addr: fe80::2e0:20ff:fe97:63c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24518111 (24.5 MB)  TX bytes:2304486 (2.3 MB)
          Interrupt:16 Memory:90000000-900000ff 

DMESG Output:
 7926.756023] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[ 7927.184204] usb 5-6.1: new full speed USB device using ehci_hcd and address 5
[ 7927.297393] usb 5-6.1: configuration #1 chosen from 1 choice
[ 7927.520081] eth1: register 'dm9601' at usb-0000:00:1d.7-6.1, Davicom DM9601 USB Ethernet, 00:60:6e:00:02:e4
[ 7927.520397] usbcore: registered new interface driver dm9601
[ 7927.532678] udev: renamed network interface eth1 to eth2
[ 7931.558243] eth2: link down
[ 7931.560552] ADDRCONF(NETDEV_UP): eth2: link is not ready

---

### Post by superprash2003 on 2009-02-16
is eth3 your usb connection?? cause it isnt getting an ip address.. try requesting for an ip from your router by typing **sudo dhclient eth3** at the terminal

---

