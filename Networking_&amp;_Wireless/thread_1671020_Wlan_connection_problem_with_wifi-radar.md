---
title: "Wlan connection problem with wifi-radar"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by noob.deb on 2011-01-19
Hello there fellow ubuntians!

I have this problem with my wlan on Acer Travelmate 2304 wlmi.
I'm trying to get it to work and I've tried so many solutions that I'm getting confused where the problem might be.
It seems that every solution thread that i try opens up a new problem.
I don't know where to start... I've been using different Linux distributions for a while but I'm no pro thats for sure.
Just copy pasting codes from threads and solving every problem that i face. But not this one...

I installed ndiswrapper and the right windows driver for the wlan and then been trying to use wifi-radar to connect wireless networks.
The radar sees networks but doesn't connect to them. It just keeps "Acquiring IP Address" but doesn't get any further.
No time out, nothing... When I start the wifi-radar on console it gives many errors when I press the connect button and the acquiring thing starts to loop forever:

[I]Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
/bin/sh: /usr/sbin/wpa_supplicant: not found
2011-01-19 21:35:20,990: connect_to_network: DHCP client not found, please set this in the preferences.
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1525, in connect_profile
    self.connection.connect_to_network(profile, self.status_window)
  File "/usr/sbin/wifi-radar", line 472, in connect_to_network
    waiting = dhcp_proc.poll()
UnboundLocalError: local variable 'dhcp_proc' referenced before assignment[/I]

And if this helps, the "ndiswrapper -l" gives:

[I]neti2220 : driver installed
    device (17FE:2220) present
[/I]
And the "sudo lshw -C network" gives:

[I]*-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:7d:9e:0f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.103 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:6 memory:e0200000-e0201fff memory:24000000-24003fff
  *-network:1 DISABLED
       description: Wireless interface
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 00
       serial: 00:0e:9b:99:83:c4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.56+LanExpress,03/29/2004,2.10. latency=64 link=no maxlatency=32 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: irq:10 ioport:3800(size=32) memory:e0203800-e020381f memory:e0203000-e02037ff
[/I]
At one point I managed to get that DISABLED out from that "**-network:1*" line there but still it didn't have any effect. Seems that it has gone disabled again somehow.:)

So, any kind of help would be appreciated. And sorry for my noobish questions but hey, it's my first post so go easy on me... :D
Let me know if there's any commands to use to give more output for the problem.

Thanks in advance!

---

### Post by noob.deb on 2011-01-21
Anyone?
It seems to be my only real unsolvable problem in linux systems that I've ever encountered.
I've tried many solutions that are out there but none of them seem to work.
Could anyone give some spesific info how to "shoot this trouble" :)
(btw. now i got rid of that DISABLED thingy somehow and like I said, still no effect)

---

### Post by noob.deb on 2011-03-24
What if I say please... Would then somebody help me? :)

---

### Post by bktango on 2011-03-24
Sorry, wish I could.  I'm new myself.

---

