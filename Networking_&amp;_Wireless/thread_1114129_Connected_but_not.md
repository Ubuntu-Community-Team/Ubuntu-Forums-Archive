---
title: "Connected but not??"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by jaksef on 2009-04-02
I'm an extreme newbie to Linux. I just installed Ubuntu yesterday to my Dell Vostro 1500, and after I finally got my wireless to see our router, I still wasn't able to use Firefox or Pidgin.

"sudo dhclient" relays lots of "send_packet: Message too long" and ends with a "1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms" "SI0CSIFADDR: No buffer space available No working leases in persistent database - sleeping."

Being the n00b I am, I have no idea what most of that means.

"lshw -C network" reveals 
"WARNING: you should run this program as super-user. 
*-network
  description: Wireless interface
  product: BCM4312 802.11a/b/g
  vendor: Broadcom Corporation
  physical id: 0
  bus info: pci@0000:0c:00.0
  logical name: wlan0
  version: 01
  serial: 00:1f:e1:0b:69:73
  width: 32 bits
  clock: 33 MHz
  capabilities: bus_master cap_list ethernet physical wireless
  configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom, 10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11b"

"iwconfig" replies with wlan0 saying
"IEEE 802.11b ESSID:"<myessidname>"
Mode:Managed Frequency:2.437 GHz Access Point: 00:40:96:35:F0:13
Bit Rate=11 Mb/s   Tx-Power:32 dBm
RTS thr:2347 B   Fragment thr:2346 B
Power Management:off
Link Quality:75/100 Signal level:-48 dBm   Noise level:-96 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0"

That's all I've got, guys. Again, my network manager says that I'm connected to the wireless network, but I can't get on the internets. I'm sorry I have no idea what I'm doing, but any help would be greatly appreciated and replied to :)

---

### Post by johnjohn2 on 2009-04-02
Have you beeen able to use router before? (Connecting Wirelessly that is?)
With any other PC?

In the router settings you can c what is connected to the router, refer to the manual.

Try connecting via ethernet to just make sure that your connection is functioning correctly.

Regards 

John

---

### Post by jaksef on 2009-04-02
Yes, I'm able to connect via ethernet, and when I used Windows XP with my Dell I was able to connect to the router without a problem :( and like I said, I switched over yesterday.

---

