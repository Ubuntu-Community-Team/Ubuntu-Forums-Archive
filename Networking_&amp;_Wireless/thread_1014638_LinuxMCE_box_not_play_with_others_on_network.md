---
title: "LinuxMCE box not play with others on network"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by marawuti on 2008-12-18
My LinuxMCE (Kubuntu 7.10) box is accessing the internet fine through either of its NICs. I can neither ping other machines on my private network nor can they ping the LinuxMCE unit.  I'm sure there is something fundamental I am missing within the Linux configuration.

My setup is 
DSL modem
     |
  Wifi router (DHCP server)
   | |
   | wire
   | |
   | +-- Windows XP Pro running McAfee network mapping SW  (static IP)
   | |                           
   | +-- LinuxMCE (static IP)
   | 
   Wifi
   |
   + PlayStation3
   |
   + Wii
   |
   + Windows XP laptop

The McAfee network mapping SW sees all units correctly.
All units excluding the MCE box are pingable from the 
Windoz Pro unit and the laptop.


> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:...
          inet addr:192.168.1.80  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ... Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8682 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:966237 (943.5 KB)  TX bytes:788431 (769.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:...
          inet addr:192.168.1.81  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9064 (8.8 KB)  TX bytes:9064 (8.8 KB)

---

### Post by MishMich on 2009-02-26
When I first set up ubuntu I could ping XP PC's, but not Vista.  It  may bee that the PC's are set up not to be pinged (this is a way intruders can test what is on the  network).  Don't assume the problem is with the new linux box.  Windows is grubby, historically networking especially so.

I know this is a bit fundamental, but have you gone onto the original McAfee network manager (the one the network is named by) and accepted the linux box as a friend rather than intruder?  It may just be that McAfee is doing its job - not letting unknown PC's into the boxes it is installed on.

I know when the PC I nominated as the manager (the first one to boot on the network when first installing the McAfee network suite) is switched off I cannot attach to any windows shares or devices from linux, so I'm guessing McAfee assigns this PC to act like a DNS - as soon as it comes up again everything works.  I discovered this because I wanted to turn that PC into an ubuntu desktop (& tested it with a live CD).

You can remove all thee McAfee network management settings, PC by PC, and unless the service is disabled as a windows service, it is automatically re-assigned to the first PC that comes back onto the network (you can download a tool at McAfee to remove the existing PC configuration).  I have asked McAfee how to incorporate ubuntu into this setup, but I think they only support RedHat & Suse & Novell linuxes.  Unless I hear otherwise I reckon disabling the McAfee windows-based network security & let linux  manage the network is the best solution.

---

### Post by marawuti on 2009-02-28
Hate to sound like Spock but fascinating.  I had not idea McAfee formed network relationships.  Please post any URLs you obtain from McAfee.

---

