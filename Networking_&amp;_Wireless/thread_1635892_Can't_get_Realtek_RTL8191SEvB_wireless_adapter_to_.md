---
title: "Can't get Realtek RTL8191SEvB wireless adapter to work"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by jindrichm on 2010-12-02
I've got a new laptop with Ubuntu 10.10 (2.6.35-23-generic x86_64 architecture) and with a wireless adapter I can't get to work. The adapter is Realtek RTL8191SEvB:

```
$ lspci | grep Network
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
```

When I enabled the wireless via Network Manager, its status changed to "disconnected". This is what happened:

```
$ dmesg | tail
[ 4029.280117] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[ 4029.327637] ================>r8192_wx_set_scan(): hwradio off
```

What is installed by default is the linux driver for Realtek 8192 (not 8191):

```
$ lsmod | grep r8192
r8192se_pci           507324  0 
```

So I tried installing a proper driver from [Realtek's website]("http://www.realtek.com/downloads/searchView.aspx?keyword=linux") but I haven't managed to get either RTL8191SE-VA2 or RTL8191SU working (and which one is the correct one anyway?).

So I tried the Windows driver via ndiswrapper but it does not *fit* the hardware I've got - ndisgtk contains:

```
Hardware present: No
```

Here is the output of lshw:

```
 *-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:60:c7:7a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0500000-f0503fff

```

And here is the output of iwconfig:

```
$ iwconfig wlan0
wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I will be grateful for any suggestions of what should I try next.

---

### Post by miikos on 2010-12-02
I have the exact same problem!
EDIT: except I tried with the 32-bit version as well, but to no avail.

---

### Post by miikos on 2010-12-03
> **jindrichm said:**
> 
So I tried installing a proper driver from [Realtek's website]("http://www.realtek.com/downloads/searchView.aspx?keyword=linux") but I haven't managed to get either RTL8191SE-VA2 or RTL8191SU working (and which one is the correct one anyway?).

Actually, it seems neither the 8191SE-VA2 or RTL8191SU are correct, but rather the RTL8192SE. I have the last mentioned driver preinstalled in my windows 7 with the same device and it's working there. I also have 8192 installed by default in Ubuntu. But Realtek's site has no such driver/device listed! Is it exactly the same driver as 8192SE? :confused:

EDIT: I'm just blind, it IS the SE driver that is installed by default in Ubuntu too. I even tried updating the driver, but it still doesn't work. More precisely, it sees all the networks but cannot connect to internet.

---

### Post by jindrichm on 2010-12-03
So, if I understand it correctly, you have managed to get Realtek RTL8191SEvB working on Windows 7 with the driver for Realtek RTL8192SE but not in Ubuntu?

I have thought that if this driver works on Windows, it should also work with ndiswrapper on Ubuntu. But, as I have found out, it does not work because the hardware is not recognized as RTL8192SE.

Any ideas how to go about this?

---

### Post by miikos on 2010-12-03
> **jindrichm said:**
> So, if I understand it correctly, you have managed to get Realtek RTL8191SEvB working on Windows 7 with the driver for Realtek RTL8192SE but not in Ubuntu?

I have thought that if this driver works on Windows, it should also work with ndiswrapper on Ubuntu. But, as I have found out, it does not work because the hardware is not recognized as RTL8192SE.

Any ideas how to go about this?

That's correct. I just bought this Lenovo L412 yesterday and everything works fine in windows 7 right out of the box. Windows device manager shows rtl8192se.sys and vwifibus.sys as the driver files. In Ubuntu, it didn't work with the default driver nor with the latest 8192SE linux-driver from Realtek's site.

If the windows 8192SE driver with ndiswrapper doesn't work, I'm out of ideas.

---

### Post by jindrichm on 2010-12-03
When I tried Realtek 8192SE driver for Windows in ndiswrapper I got *Hardware present: No* message indicating that my wireless adapter was not recognized as Realtek 8192SE. 

The thing is that I got the exact same problems with an external USB wireless adapter (this time Ralink), so I wonder if it is really hardware/driver problem. But I should probably try some wireless adapters that are seen as non-problematic in Ubuntu (e.g., Atheros) first.

Now I tried Windows RTL8191SE-VA2 driver version 2017.2 with ndiswrapper and this time it seems it fits the hardware:

```
$ ndiswrapper -l
net8192se : driver installed
	device (10EC:8172) present (alternate driver: r8192se_pci)
```

But the problem is that I've lost the wlan0, it's now UNCLAIMED:

```
$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0500000-f0503fff
```

Maybe this is the way to go.

---

### Post by dylan noktum on 2010-12-03
i have the exact same problem only i am using the 2.6.35-22-generic kernel  so it will be great if this can be worked out

---

### Post by mcpastor on 2010-12-06
I have the same wireless controller and came here looking for answers. Mine works with whatever drivers Ubuntu assigned to it, but not always. Sometimes I can't connect from boot, other times I can. Sometimes I get bumped offline and cannot reconnect until 1/2 hour later or so. I don't know anything about the code running behind the scenes, but if you think it would help you to see what's going on in my machine I can try to copy the code and post it here. I'll need some help knowing where to look for the code 'cuz I'm a noob to the Ub.

PS: I have two wireless networks: HOME and WORK. Work logs on very quickly without a problem, but I can't get the internet. When trying to connect to Home, oftentimes I will get the spinning icon for long periods of time and finally a notice that Home is disconnected.

---

### Post by Jengu on 2010-12-09
I have the same problem with a Thinkpad 410s. I can /usually/ connect but sometimes I get disconnected and then it's impossible to reconnect without a reboot.


03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

---

### Post by frznlogic on 2010-12-10
I just solved this problem on a Toshiba Satellite T130-17E laptop with the following network card:

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

by adding hwwep=0 to the modprobe commandline. Either rmmod r8192se_pci and then:

modprobe r8192se_pci hwwep=0

Ubuntu should be able to join a network now. This turns off hardware wep acceleration. I am now having some problems with a lot of connections getting "stuck" (large downloads, apt-get update for example) and haven't solved that yet. Basically, a download will run for a while, then just get stuck, and I have to stop it and then restart it.

To automate the hwwep setting being set every time you reboot, edit /etc/modprobe.d/realtek.conf (probably doesn't exist) and add the following line:

options r8192se_pci hwwep=0

Good luck! :)

---

### Post by jindrichm on 2010-12-10
Unfortunately, this does not work for me.

However, it produced some changes of the wi-fi behaviour. When I follow your instructions Network Manager indicates that wireless is disabled and when I enable it, it is "disconnected" but, immediately after that wireless is disabled again and keeps disabling automatically.

Do you have an idea what might be the cause of this behaviour?

---

### Post by jindrichm on 2011-01-01
I still haven't solved this issue.

When I unload and load the [FONT="Courier New"]r8192se_pci[/FONT] driver with the hwwep=0 option:

```
rmmod r8192se_pci
modprobe r8192se_pci hwwep=0
```

And then, when I enable the wireless via the Network Manager, it says that the *"device is not ready"*. I've found some suggestions that this is an issue caused by the [FONT="Courier New"]rfkill[/FONT] blocking the wireless, so I've unblocked it:

```
rfkill unblock all
```

So that it was unblocked:

```
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

After re-enabling the wireless, at first Network Manager reported *"disconnected*" for the wireless networks, but immediately after that, inspecting the Network Manager the second time, it returned back to *"device is not ready"* message. I guess something must have been reset back to its original value.

---

### Post by jindrichm on 2011-01-28
*bump*

---

### Post by jindrichm on 2011-02-11
I have news. After I have installed newer Realtek's driver (rtl8192se_linux_2.6.0019.1207.2010), the wi-fi still doesn't work, however it is not disabling itself all the time.

So, when I [FONT="Courier New"]sudo modprobe r8192se_pci[/FONT] and enable the wireless via the Network Manager's widget, it is "disconnected" with no wi-fi networks found.

```
$ iwconfig wlan0 
wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:130 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```

$ dmesg
[28912.008580] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[28912.122642] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[28912.122651] InitializeAdapter8192SE(): Set MRC settings on as default!!
[28912.122656] HW_VAR_MRC: Turn on 1T1R MRC!
[28912.124413] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28912.291306] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[28912.291316] InitializeAdapter8192SE(): Set MRC settings on as default!!
[28912.291321] HW_VAR_MRC: Turn on 1T1R MRC!
[28912.930035] GPIOChangeRF  - HW Radio OFF
[28913.002552] ============>sync_scan_hurryup out
[28913.133424] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return

```

Any ideas?

---

### Post by miikos on 2011-02-16
I have given up on trying to make it work, not having the necessary know-how. But I'm still hoping you or someone will work out a solution, because even though windows 7 is better than vista, it's still inferior to Ubuntu.

---

### Post by zapho on 2011-02-20
I recently bought an Edimax 300Mbps Wireless (model #EW-7612PIN) which also uses the RTL8191SEvB chipset for a new build of mine.

I'm running ubuntu 10.10 x64. After a fresh install, I can confirm that this card is working for me!

Kernel is:
```
Linux black 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

```

Running *lshw -class network* gives:
```
*-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 00:1f:1f:fa:2a:23
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.1.24 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:16 ioport:de00(size=256) memory:fdcfc000-fdcfffff
```

And running *lsmod | grep r8192* gives:
```
r8192se_pci           512896  0 
cfg80211              170485  1 r8192se_pci
```

And *iwconfig wlan0* gives:
```
wlan0     802.11bg  ESSID:"starbuck"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: E0:CB:4E:62:C7:ED   
          Bit Rate=1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=89/100  Signal level=-50 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I can browse the net which is a little slower compared to my win7 laptop. File transfers over samba seem pretty good, averaging about 1.1MB/s. My wifi network uses WPA2 encryption as well. The only problem is that the bit rate seems to be stuck at 1 Mb/s and running *sudo iwconfig wlan0 rate 54M* doesn't seem to do anything.

I'm available to run commands for others who are trying to get this card working - so feel free to ask me! (Seems a bit of a fluke that mine worked :rolleyes:

-zapho

---

### Post by mesilikas on 2011-02-26
I have exactly the same problem with the same wireless card (RTL 8191 SEvB) in Thinkpad Edge 13 and installed Ubuntu 10.10 64b will be great pleasure if it can work with wireless internet :(

---

### Post by Alver on 2011-02-26
> **zapho said:**
> I recently bought an Edimax 300Mbps Wireless (model #EW-7612PIN) which also uses the RTL8191SEvB chipset for a new build of mine.

I'm running ubuntu 10.10 x64. After a fresh install, I can confirm that this card is working for me!

Kernel is:
```
Linux black 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

```

Running *lshw -class network* gives:
```
*-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 00:1f:1f:fa:2a:23
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.1.24 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:16 ioport:de00(size=256) memory:fdcfc000-fdcfffff
```

And running *lsmod | grep r8192* gives:
```
r8192se_pci           512896  0 
cfg80211              170485  1 r8192se_pci
```

And *iwconfig wlan0* gives:
```
wlan0     802.11bg  ESSID:"starbuck"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: E0:CB:4E:62:C7:ED   
          Bit Rate=1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=89/100  Signal level=-50 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I can browse the net which is a little slower compared to my win7 laptop. File transfers over samba seem pretty good, averaging about 1.1MB/s. My wifi network uses WPA2 encryption as well. The only problem is that the bit rate seems to be stuck at 1 Mb/s and running *sudo iwconfig wlan0 rate 54M* doesn't seem to do anything.

I'm available to run commands for others who are trying to get this card working - so feel free to ask me! (Seems a bit of a fluke that mine worked :rolleyes:

-zapho

I have the same card on my Toshiba L505-10M with Ubuntu 10.04 64b. It worked well out of the box from day 1 some 10 months ago. I do use an earlier software version however < driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 >. Hope this helps.

Alver

---

### Post by mesilikas on 2011-02-27
> **mesilikas said:**
> I have exactly the same problem with the same wireless card (RTL 8191 SEvB) in Thinkpad Edge 13 and installed Ubuntu 10.10 64b will be great pleasure if it can work with wireless internet :(


All problems were solved with the bios update and upgrade of the Linux kernel!

Thank :D

---

### Post by wildmanne39 on 2012-08-01
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

