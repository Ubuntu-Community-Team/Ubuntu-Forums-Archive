---
title: "nm-applet/wired connection stopped inexplicably"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by schlesinger on 2009-10-21
Hi, 

My wired connection just stopped working this morning and I'm not sure why. I've tried: killing and restarting nm-applet, and running ifconfig eth0 down and ifconfig eth0 up. connecting to wireless networks still works. I think maybe it's using the wrong device all of the sudden? I didn't install anything since last night. 

I know my ethernet cable and connection is fine because when I dual boot into Windows I can connect to the Internet using a wired connection, so it's definitely a Linux software or configuration problem.

My ifconfig looks like this: 
>> ifconfig

ath0      Link encap:Ethernet  HWaddr 00:19:7e:57:3d:6a  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe57:3d6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3645555 (3.4 MB)  TX bytes:646158 (631.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:d3:b4:17:7a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:2908944 (2.7 MB)  TX bytes:26399 (25.7 KB)
          Base address:0x2000 Memory:ee000000-ee020000 

with lo and wifi0 devices also. But I'm not sure how to decipher it or figure out what's wrong. 

Any help would be greatly appreciated! 

Thanks, 
Shannon

---

### Post by coffeeaddict22 on 2009-10-21
what's the output of ```
lshw -C network
``` and what network connections do you think you should have?

---

### Post by schlesinger on 2009-10-21
>> sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:d3:b4:17:7a
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 latency=0 link=no module=e1000 multicast=yes port=twisted pair

----------

And then it has a similar list for my wireless card. I think I should be using eth0. nm-applet seems to be working in that it shows the normal icon and status when I'm connected to Ethernet, I just can't load any pages.

Thanks and let me know if you have any ideas

---

### Post by Iowan on 2009-10-21
Have you tried turning off the wireless? It looks like "something" is getting IP address, and under NM only one will.

---

### Post by schlesinger on 2009-10-21
Yes, I did, but it didn't help. 

Actually, I do remember that I ran an apt-get update/install that night, and shortly afterwards it stopped working, so maybe another program is affecting my networking. Also, when I run Network-Tools, it tells me that my eth0 (ethernet interface) "doesn't exist" or "isn't installed correctly." 

Any ideas? Maybe I should figure out how to roll back updates.

---

### Post by Iowan on 2009-10-21
*/etc/udev/rules.d/70-persistent-net.rules*might be have your interface defined as ath0. (also check **lshw -C network**).

---

### Post by schlesinger on 2009-10-21
When I run lschw -C network it has two devices, eth0 and wifi0, both I think are correct. Checking /etc/udev/rules.d/70-persistent-net.rules has both eth0 and ath0, thanks for your help :) 

One more thing--when I run nm-applet from command line and try to connect Ethernet cable: 

** Message: <info>  Forcing device '/org/freedesktop/NetworkManager/Devices/ath0'
** (nm-applet:8204): WARNING **: <WARN>  nma_dbus_device_properties_cb(): dbus returned an error.
  (org.freedesktop.NetworkManager.DeviceNotFound) The requested network device does not exist.

---

### Post by Goodlooking on 2009-10-21
I am on ethernet, using the wired connection, and i type in ifconfig and this is what i get.

[CENTER][LEFT]eth0    Link encap:Ethernet HWaddr 00:08:02:d8:96:db

          UP BROADCAST MULTICAST MTU:1500 Metric:1

          RX packets:0 errors:0 dropped: 0overruns:0 frame:0                                      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000 

RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo Link encap:Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr:  : :1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets: 12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:852  (852.0 B) TX bytes:852 (852.0 B)

My pc is a Compaq Avo. my os is of corse ubuntu. I am connecting threw the same wire as for my laptop to get on the pc i am on now, only I am using Windows. My ISP is Charter. I am using Jaunty Ubuntu. I cannot get online with any other method. 
[/LEFT]
[/CENTER]

---

### Post by coffeeaddict22 on 2009-10-22
Hi goodlooking,
What's the question?  Are you trying to use wireless?  Is the wired not working?  Is it slow?

---

### Post by Goodlooking on 2009-10-27
I am using a wired connection, The lights light up on the back of the laptop, but No connection.

---

### Post by Iowan on 2009-10-27
DHCP address or manual configuration? [This]("http://ubuntuforums.org/showthread.php?t=1156441") fixed my wired DHCP problem. Otherwise, post **lshw -C network**.

---

