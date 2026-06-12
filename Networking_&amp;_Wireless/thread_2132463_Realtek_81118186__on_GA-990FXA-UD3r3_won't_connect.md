---
title: "Realtek 8111/8186  on GA-990FXA-UD3r3 won't connect to gateway"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by JoeStIdes on 2013-04-04
Stop me if you heard this one....

I built this computer about a month ago using the Gigabyte GA-990FXA-UD3 rev 3 motherboard.
I initially put in Windows 7 64 bit professional. everthing went well, not a problem.

Then I decided to go ahead and install Ubuntu 12.10. From what I've read online, this wasn't for the faint of heart among those who own a GA-990FXA-UD3 but did it anyway.

Big suprise, the wired network won't connect. It tries, doesn't get a connection. then it disables, then tries again. 

I have done the following steps to no success
 
[LIST]
[*]I have swapped out the seemingly     faulty r8169.ko and replaced it with the r8168.ko available [Here.]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false") 
[*]I've tried just about every method     from what is directed in the README in the tarball, to various     methods mentioned elsewhere on the web. 
[*]I've attempted to reboot even     unplugging the machine from the wall for a bit. 
[*]I have tried installing 12.04 
[*]I managed to find an old Netgear     WG111 usb adapter and got it to work thus giving me internet. So I     did a clean install of Ubuntu with network connection (preivious     installs did not have a network connection), then updated the system     upon first boot. *FYI: after the update the ethernet was still     using r8169 so updated it with r8168.* 
[*]I've set IPv6 to "Ignore" 
[*]I've attempted the [HTML]sudo     modprobe r8168[/HTML] 
[*]I have tried using alternatives to the default network     manager like Wicd 
[/LIST]
 
Stll the result is the same. The wired network attempts to connect, fails, a pop up states "Wired network disconnected" then tries again.

When I unplug the cable from the network port, it does detect that it's been disconnected and discontinues the cycle of attempting to connect.

I have manually put in the connection details into the network configuration, this said I was connected but I had no network access.

I've edited etc/network/Interfaces and put in the following lines

[HTML]# The Ethernet card
auto eth0
iface eth0 inet dhcp
[/HTML]

When I rebooted the splash screen comes up and tells me that it is waiting for a network connection. It never finds one and then boots up without any network connection (wireless or wired) nor can I configure it until a comment or remove the eth0 lines and reboot.

The Win 7 64 pro install on the same machine using the same cable is able to connect no problem.

I have a Playstation 3 that is wired to the same gateway and it connects no problem.

I have two laptops, two android smartphones, and a Win764pro machine that connect, no problem, wireless, to the same gateway (a Motorola SBG6480 D3 cable gateway).

In fact I had an older machine that I had Ubuntu 12.04 on it and it was able to connect to the same gateway some months ago.

Too much detail? I'm in technical support so I tend to answer questions before they are asked  :smile: Speaking of which..

A common problem I know, but it may be related.. the networking stop and restart command lines crash ubuntu in my case.

Here is yet more info

I type in the "ifdown" and "ifup" command line and get the following
[HTML]$ sudo ifdown eth0
ifdown: interface eth0 not configured
$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
[/HTML]

However...
[HTML]$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 up
$
[/HTML]

Ifconfig -v output
[HTML]eth0      Link encap:Ethernet  HWaddr 94:de:80:0b:90:fd  
          inet6 addr: fe80::96de:80ff:fe0b:90fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1748 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:318849 (318.8 KB)  TX bytes:318849 (318.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:73:cd:80  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fe73:cd80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17515782 (17.5 MB)  TX bytes:2803016 (2.8 MB)[/HTML]

lspci -v

[HTML]xpress Gigabit Ethernet controller (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5/GA-EG45M-DS2H Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 75
    I/O ports at a000 [size=256]
    Memory at da104000 (64-bit, prefetchable) [size=4K]
    Memory at da100000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-68-4c-e0-00
    Kernel driver in use: r8168
    Kernel modules: r8168
[/HTML]

looks like the componant is using the correct driver.

So after scouring the net I've tried everything, Any assistance would be greatly appreciated. I'd rather not switch flavors, and since this is giving me the headache my natural inclination as a per my occupation is to take an issue by the horns and figure out a solution rather than cast it on the trash heap. Also I am a community guy so I'd like to beable to compile solutions in order to make this motherboard work for others who have such aspirations.

Thanks :)

---

### Post by JoeStIdes on 2013-04-06
Well in an update Ive disabled all of the power saving and sleep options on Win 7, and attempted to engage WOL on the mobo.. Same result.

---

### Post by Charlie Loberz on 2013-04-16
Same motherboard GA-990FXA-UD3 revision 3, two network interfaces:
eth0 device: Realtek Semiconductor Co., Ltd. RTL8111/8168B (the one built-in)
eth1 device: Intel Corporation 82541PI Gigabit Ethernet Co (PCI Express)
I went though several installs of various versions of Linux (SLES 11 SP1 works fine, it's kernel v2.6.32; SLES 11 SP2 fails, it's kernel 3.0.13; Ubuntu 12.04 fails-Kernel 3.2).
Something to do with kernel v3.x I think, maybe the Realtek drivers that come with the distributions do not work with Kernel v3.x - At least not for this motherboard.
Note that with Windows 7, after adding the extra drivers that come with the MB, it all works fine.

Sorry I don't have the fix. Maybe rebuilding the drivers on a v3 kernel? Advice welcome! :)
Thanks!
CL.

---

### Post by JoeStIdes on 2013-04-17
wait, so all your usb's and network work fine now?

---

### Post by Charlie Loberz on 2013-04-17
SLES11 SP1: YES out of the box; 
Windows 7 with the extra drivers: YES. 
SLES11 SP2 or Ubuntu 12.04, both kernel v3.x: NO.

---

### Post by Resistent on 2013-12-08
Now I have the same problems with  [COLOR=#000000]GA-990FXA-UD7 and Ubuntu 13.10, latest BIOS Version 07/09/2013
[/COLOR]
:cry:[COLOR=#000000]

[/COLOR]Network connection not possible,

[COLOR=#000000]also with "sudo service networking stop" or [/COLOR][COLOR=#000000]"sudo service networking restart"  ubuntu get a black screen with a cross white cursor.[/COLOR][COLOR=#000000]

[/COLOR]The problem is visible, on a working Ubuntu 13.10, there is an extra[COLOR=#0000ff] IPv4 (inet) [/COLOR]line..
for example, in [COLOR=#0000ff]blue[/COLOR]:

> [COLOR=#000000][FONT=Ubuntu Mono]eth0      Link encap:Ethernet  HWaddr 94:de:80:0b:90:fd  [/FONT][/COLOR]          inet6 addr: fe80::96de:80ff:fe0b:90fd/64 Scope:Link
          [COLOR=#0000ff]inet addr:192.168.0.131  Bcast:192.168.0.255  Mask:255.255.255.0[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1748 overruns:0 carrier:0
          collisions:0 txqueuelen:1000  [COLOR=#000000][FONT=Ubuntu Mono]          RX bytes:60 (60.0 B)  TX bytes:0 (0.0 B)[/FONT][/COLOR]

---

### Post by Resistent on 2013-12-10
I solved the problem withj the [COLOR=#000000]GA-990FXA-UD7 wired network.
[/COLOR]--> I bought a LAN - USB adapter for about 8 USD. I jut plugged in and works works works immediatelly.

---

### Post by 7182818 on 2013-12-10
I notice your eth0 dropped count is pretty high.  It'd be interesting to see the reason for this.  Try running some of the commands in the article mentioned here:

[http://www.linuxjournal.com/content/fun-ethtool](http://www.linuxjournal.com/content/fun-ethtool)

Specifically, it'd be interesting to see the output of the '-S' flag and the '-t' flag.  Maybe the former will provide some insight into why lots of packets are being dropped, and hopefully the latter will tell us whether the driver/hardware is the problem.

After that, it'd be good to take out the line in /etc/network/interfaces enabling dhcp and see whether an address can be configured manually.  Then, see whether you can ping the address of the router.

Post back and we can go from there

---

### Post by Resistent on 2013-12-23
Enable the BIOS setting IOMMU helps !

I solved the problem.The BIOS setting IOMMU was mentioned in other blog posts, 
I enabled it in BIOS, now Ethernet works, also USB port works all. :-)

I have a [COLOR=#000000]GA-990FXA-UD7 motherboard.[/COLOR]

---

### Post by kb5won on 2014-01-04
> **Resistent said:**
> Enable the BIOS setting IOMMU 

I've had the same problem -- strange because it worked for a while then stopped.  I had IOMMU enabled.  (I turned it on to fix the USB not working)  At the same time, I enabled 'network stack' in the BIOS settings.

Well, I turned off 'network stack' and my Realtec Ethernet port is working again.

---

### Post by nitsujz28 on 2014-01-14
I have the identical problem to the OP, JoeStldes.  Same GA-990FXA-UD3 motherboard except Rev 4.  Running Ubuntu 13.10 and I've done nearly the same steps in troubleshooting.  Currently using (trying) the r8168 driver.

I just now enabled IOMMU in the BIOS and it prevented any USB ports from working, thus no keyboard or mouse.  No network difference it seemed.
JoeStldes, have you tried enabling IOMMU and has it worked?

Resistent, when you enabled IOMMU was there anything else that you had done to get that to help you?  Any ideas why my case is the opposite result?


Couple more days and I'm going to buy an Intel NIC and use the functioning internet connection to research ways of coping with failure...

---

### Post by nitsujz28 on 2014-01-15
For what it's worth... I bought this:  [http://www.microcenter.com/product/360498/Gigabit_PCIe_X1_Adapter](http://www.microcenter.com/product/360498/Gigabit_PCIe_X1_Adapter)

And I was connected immediately upon first boot with it.  Ubuntu 13.10.  Zero problems.  Finally gave that PCIe slot something to do.

---

