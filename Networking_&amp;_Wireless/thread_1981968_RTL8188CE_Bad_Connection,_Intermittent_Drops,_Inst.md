---
title: "RTL8188CE Bad Connection, Intermittent Drops, Installed RTL Drivers?"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by caeso on 2012-05-17
I'm using Ubuntu 12.04 LTS on an HP Pavilion DV6. 

I am having several wireless issues, which I think stem around my system not using the correct driver. At the same time, I'm not sure if the system is using the manually compiled Realtek drivers.

The issue is that the connection, although showing still connected, stops functioning altogether for several seconds (upwards of a minute). It eventually will start working again, but as far as I can tell the connection never actually dropped.

I am using the downloaded drivers for the 8188CE from the Realtek website using the "sudo su/make/make install/reboot" method, which works without any hiccups, however I cannot be sure if it's using the correct driver because lsmod shows it's using the 8192CE drivers (which came install on the system and worked, although it had the same issues).

Furthermore, if I try to use the installer that came with the Realtek drivers using:
```
./compat/script/compat-install.sh
```
It errors out saying that it cannot find a specified file (I can't recall what the actual filename is, but when looking at the directory structure the file does indeed exist, considering it is one of the files newly compiled. I can't for the life of me figure out why it's stopping).

Anyone have any thoughts? This is starting to drive me nuts!


lscpic -v
```
0d:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 1629
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at 3000 [size=256]
	Memory at c4500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8192ce
	Kernel modules: rtl8192ce

```

iwconfig
```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"WCC-Public"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0B:86:AC:8A:90   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

eth0      no wireless extensions.

```

lshw
```

 *-network
                description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0d:00.0
                logical name: wlan0
                version: 01
                serial: 20:10:7a:33:fe:4e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-24-generic firmware=N/A ip=10.4.243.218 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 ioport:3000(size=256) memory:c4500000-c4503fff

```

lsmod
```
mac80211              506816  2 rtl8192ce,rtlwifi

```

---

### Post by IWantFroyo on 2012-05-17
Have you tried running "Additional Drivers"?

---

### Post by caeso on 2012-05-17
Hey, thanks for the response. 

I just ran it again in case I missed something, and the only drivers listed using the Additional Drivers utility are for my GPU.

---

### Post by caeso on 2012-05-18
/bump still trying to figure this out!

---

### Post by parth.s on 2012-05-19
I have the same damn problem! I have been grappling with it for about a year. I have a ASUS notebook and for me the problem spans over all the recent ubuntu distros, from lucid onwards.

I'm planning to try another distros and see if they have a better support (on second thoughts will that work?, but its worth a try) for the realtek card.

---

### Post by paintba11er89 on 2012-06-03
Same problem. Try manually compiling the driver using the instructions in the readme file that is included in the directory.  I have been trying to find a solution for this problem for a month, and still have found nothing that works!

---

### Post by caeso on 2012-06-03
I still haven't found a resolution yet. I've also noticed that sometimes it has trouble negotiating a connection at about 40-50% signal strength. When I reboot into windows it connects just fine and says the strength is about 70%. I know those numbers don't really mean anything beyond the fact that *there is* a fairly strong signal. Really irritating.

---

### Post by murtyvonna on 2012-06-09
**I am also facing with the same problem . I wrote to ASUS. :**
[Product Information]
*Product Type : Wireless
*Product Model : PCE-N15
*Product S/N : B8IEN1003176
Place of Purchase : eBay
*Date of Purchase : 2012/5/18

*Operating System : Linux 

[Problem Description]
The operaing sysem is Ubuntu 12.04. The driver is already is in the kernel. Any how I 
have installed the latest driver from ASUS. The adopter is for earlier driver as per y and it is very slow.
your instructions.
Wireless breaks frequenty and it is very slow.

Their reply is:
Dear Valued Customer,
Thank you for contacting ASUS Customer Service.

The support OS of PCE-N15 is Windows 7 32bit/64bit, Windows Vista 32bit/64bit, Windows XP 32bit/64bit and Linux Kernel 2.6 (Support Ubuntu only).

There are three possible reasons of Bad link quality or bad signal strength:

- Interference by other electronic devices that using 2.4 GHz radio frequency
- Wireless signal is blocked by thick wall, metal door, ceiling and other obstacles
- Exceed the effective coverage range of wireless router and access point (AP)

Please also keep the environment around the wlan clients and the router away from microwave ovens and large metal objects(such as microwaves, cordless phones, refrigerators, etc. If you live in an area that is highly saturated with wireless routers you may have to hard set your wireless channel. I recommend channel 1,6,11. 

I suggest you also cross test the card on other PCI-E slot or another PC.

In fact I have dual boot systems with windows7 . I have no issue with windows 7

---

### Post by 1i1g on 2012-06-09
I have had this problem with my gigabyte s1081 tablet that also uses the RTL8188CE for WiFi.

Seeing as nobody has tried to replace the firmware files in /lib/firmware/rtlwifi/ so far, I thought I would give it a try. For me replacing rtl8192cfw.bin with rtl8192cfwU_B.bin from the realtek homepage worked with Ubuntu 12.04 as well as Fedora 17. I, however, am not sure if selecting the wrong firmware file can damage your hardware. So if you do this it is at your own risk.

That aside, here is how I did it.
First you have to find out which firmware file is being used by the driver supplied with the kernel.

```
dmesg | grep rtl8192
```this will give you a line similar to this.

```
[    8.143578] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
```This reveals which firmware file is being used by the driver (rtl8192cfw.bin). 

Now to get all the firmware files. From the realtek page downloaded the rtl8188ce archive. Here is the link 
```
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4)
```If that does not work go to realtek.com/downloads and click through "Communications Network ICs > Wireless LAN ICs > WLAN NIC > IEEE 802.11 b/g/n > Software"

When you have the file, extract it and get to the firmware folder as follows

```
tar xfv 92ce_se_de_linux_mac80211_0005.1230.2011.tar.gz
cd ./92ce_se_de_linux_mac80211_0005.1230.2011/firmware/rtlwifi 

```Then backup the original firmware file incase you need it again later

```
sudo mv /lib/firmware/rtlwifi/rtl8192cfw.bin /lib/firmware/rtlwifi/rtl8192cfw.bin.bak

```and then try your way through one firmware file after the other. For me this worked

```
sudo cp rtl8192cfwU_B.bin /lib/firmware/rtlwifi/rtl8192cfw.bin
```As I said before, I don't know if this can harm your hardware in any way. So this is at your own risk. But I think it should be fairly safe, seeing as these are only variants of the same chip.

---

### Post by caeso on 2012-06-12
> **1i1g said:**
> I have had this problem with my gigabyte s1081 tablet that also uses the RTL8188CE for WiFi.

Seeing as nobody has tried to replace the firmware files in /lib/firmware/rtlwifi/ so far, I thought I would give it a try. For me replacing rtl8192cfw.bin with rtl8192cfwU_B.bin from the realtek homepage worked with Ubuntu 12.04 as well as Fedora 17. I, however, am not sure if selecting the wrong firmware file can damage your hardware. So if you do this it is at your own risk.

I am using the U_G firmware atm, and we'll see how it works. If there are still issues i'll try the other firmware as well and report back.

Thanks for the tip!

---

### Post by R. McC on 2012-06-24
Swapping out firmware didn't have any effect for me. If anything, the other firmware options (U and U_B) offered worse performance than the main one. :(

I've been contributing to [this bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557) on the matter. For what it's worth, the exact same symptoms are also present on a Ralink USB adapter.

The big clue to look for (at least for me) is a line talking about "Reason 6" in your syslog.

---

### Post by R. McC on 2012-07-02
I continue to have no success with connecting to either my home wireless network (to which my other ThinkPad, using iwl3945 connects without issue) or the wireless network on the train. However, I can connect without issue to my work wireless network (thank goodness, since this is my work laptop...). 

I continue to see the "Reason 6" errors.

---

### Post by caeso on 2012-07-06
I had to move back to the original firmware. The U_B firmware was worse than the original. I'm still having issues, but not as bad as before. If anyone has an update on a real solution, i'd love to hear it.

---

### Post by simon002 on 2012-07-07
Nothing new, but I have the same issue. 

wildmanne39 is helping me in this thread:

[http://ubuntuforums.org/showthread.php?t=2015554]("http://ubuntuforums.org/showthread.php?t=2015554")

---

### Post by R. McC on 2012-07-19
Thanks, Simon. I'll keep an eye on that thread, too. So far, it looks like all the same steps everyone has recommended, but with no success. Still no progress over here, either.

---

### Post by caeso on 2012-07-27
I am still having connectivity issues.

The weirdest one is that when I am connected just fine, and shut my laptop, then come back online, it won't reconnect to the same WiFi. It probes the airspace/network and finds it, but can never authenticate.

This issue is driving me NUTS!

I can't use a laptop functionally without the WiFi as well.

I'm almost ready to pay a developer to take a look at this. Is there a way to do that?

---

### Post by Skyjames on 2012-08-12
> **caeso said:**
> /bump still trying to figure this out!

And now August, still no solution.

I still have this issue, though mine is in reverse. If I am hard wired to a modem, (3 different 2 new) data flow slows to a crawl, site(s) dump me saying "lost connection" etc ... as one cause. 

For instance:
One site might be a backgammon game, another will be banking. The banking site times me out, backgammon site says "lost connection"

If I am connected using a neighbors wireless connection, all is well. No router, or I would try this at home with one.

Realtek diver page will not allow me to D/L, it says "not allowed to view page". (all d/l sites on realtec).
I am still looking to d/l the latest PCIe FE Family Controller driver. From reading this thread it doesn't look as if a new and improved driver will help.

Any new developments on this issue?

HP PAV g7.1365dx notebook PC
Motorola Surfboard SB1500

thx,
james

---

### Post by caeso on 2012-09-07
This  rather interesting.

I ordered a Realtek 8192CUS from ChinaVasion (pico USB,  so super small) in the hopes that I could just use an external WiFi adapter and forego the internal one I have. However after tinkering with it I causes my Ubuntu to not even boot even more (weird huh?). 

So I reinstalled 64bit Ubuntu with updates, and now my internal WiFi works! I haven't had alot of time to play with it, but so far it has worked fine (even after suspend/resume). Maybe it's a kernel thing?

Current info for my setup with working RTL8192cfw:

Note, the following is with my phone basically five inches away, however before I couldn't get it to connect at all with any reliability:
```

johnnyfive@beacon:~$ iwconfig
wlan1     IEEE 802.11bgn  ESSID:"AndroidTether"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 02:1A:11:F4:AA:15   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

```


```

johnnyfive@beacon:~$ lspci -v
0d:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 1629
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at 3000 [size=256]
	Memory at c4500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8192ce
	Kernel modules: rtl8192ce
```

```
johnnyfive@beacon:~$ uname -a
Linux beacon 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

If there's anything I can do to help others please let me know.

I will report back on reliability as well.

Best of luck!

---

### Post by R. McC on 2012-11-15
The [Launchpad bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557) has seen some more activity of late, with the release by RealTek of a new set of drivers (version 0007.*). While these new drivers have resolved the issue for some, I continue to see the same issues as before (frequent Reason 6 deauthentication leading to ~10% packet loss and terrible overall connection fidelity, despite strong signal strength). 

I'm now using 12.10 x64 rather than 12.04.

---

### Post by jardag on 2012-11-26
I solved this by using the linux default driver rtl8192ce and creating file
/etc/modprobe.d/rtl8192ce.conf
like this:

jardag@precise-HP:/etc/modprobe.d$ cat rtl8192ce.conf
options rtl8192ce ips=0 fwlps=0 debug=2

some guys also put in "swenc=1" but i did not need it.

---

### Post by adam.stokes on 2012-12-21
I stumbled across this particular post and I've tried everything short of switching out the firmware. Thanks for this post

---

### Post by umanohone on 2013-01-10
I've tried everything in this post as well.

Compiling and installing the drivers from realtek didn't seem to make a difference on my configuration.

Right now I'm trying to build and install the latest wpa_supplicant (1.1). No success yet.

---

### Post by thomas15v on 2013-01-26
Also performing this problems. But i can get internet 1 meters of the router. Farder i stay connected but no internet :(. The only thing i can do to get 30 seconds internet is. 

```
sudo modprobe rtl8192ce
```
And reconnect the router.

---

### Post by michael37 on 2013-01-29
The best way to tell which driver you are (*) using is to run command

```
$ modinfo rtl8192ce
```

(or whichever flavor of rtl8192 you have in your system)

Here is modinfo for the **standard** Ubuntu driver:
```
filename:       /lib/modules/3.2.0-36-generic/kernel/drivers/net/wireless/rtlwif
i/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     DA52BF758B7683607AFCB85
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.2.0-36-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

```

Here is modinfo for the **RTL** driver:
(instructions are download;make;sudo make install;reboot | see details in the original post in this thread)
```

filename:       /lib/modules/3.2.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8371CA3A9E899B11125FFDE
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.2.0-36-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)

```

* It's actually a driver that you will be running after the next reboot, not necessarily the one you are runnign now. Reboot if you are not sure.

---

### Post by adam.stokes on 2013-01-29
> **jardag said:**
> I solved this by using the linux default driver rtl8192ce and creating file
/etc/modprobe.d/rtl8192ce.conf
like this:

jardag@precise-HP:/etc/modprobe.d$ cat rtl8192ce.conf
options rtl8192ce ips=0 fwlps=0 debug=2

some guys also put in "swenc=1" but i did not need it.

This seems to be hit or miss, for my x230T it did not solve the issue. Still run into issues where I can't connect to my wireless router at home while other laptops will but can connect to other wireless routers.... This is the worst wireless chipset I've ever been locked into using. I say locked in because Lenovo apparently blacklists all other wireless chipsets unless it is one they provide so no use switching it out for an Intel one.

---

### Post by cblxub on 2013-02-03
I have had the same problem  with drops on my Toshiba Satellite with Realtek RTL8188CE.
ubuntu 12.04  64bit   with gnome shell 3.42 (PPA version)
I have wondered if it is a power management problem but I have power management disabled by default to the Wifi card.

I have a tip  that now works... and I am hoping someone more knowledgeable can make sense of it.

When my  connection gets sloppy (drops, bad connetions, timeouts)

I run in the command terminal... the program:
sudo iptraf

and monitor all connections.

I don't understand why this works... maybe this gives somebody a lead on what is going on.


Just running this program fixes the problem and my wireless is running like a champ.

---

### Post by abdulmajid on 2013-11-16
I have the same issue. Wifi keeps disconnecting intermittently on my Toshiba Satellite C640.

> eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Bait-ul-Amaan"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 74:44:01:34:4C:A0   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0




> lspci -v00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel


00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device fdf2
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4050 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915


00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at d6406100 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei


00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at d6405c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd


00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel


00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d5400000-d63fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d4400000-d53fffff
	Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=20, subordinate=22, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: d3400000-d43fffff
	Prefetchable memory behind bridge: 00000000d2400000-00000000d33fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d6405800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>


00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: lpc_ich


00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at 4048 [size=8]
	I/O ports at 405c [size=4]
	I/O ports at 4040 [size=8]
	I/O ports at 4058 [size=4]
	I/O ports at 4020 [size=32]
	Memory at d6405000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci


00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: medium devsel, IRQ 9
	Memory at d6406000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 4000 [size=32]
	Kernel modules: i2c-i801


00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at d6404000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel ips
	Kernel modules: intel_ips


01:00.0 Ethernet controller: Qualcomm Atheros AR8152 v1.1 Fast Ethernet (rev c1)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d5400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 3000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c


02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Askey Computer Corp. Device 7159
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d4400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k


3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0


3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0


3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0


3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0


3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0


3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0

---

### Post by pascalfares on 2013-12-13
I have same problem after installing 13.10.

---

### Post by rootuser2 on 2014-01-27
> **pascalfares said:**
> I have same problem after installing 13.10.

I can confirm the problem was solved for me on Ubuntu 13.10 AMD64 as discussed above.
I added the modprobe options below, updated my initramfs image and then reboot.

jardag@precise-HP:/etc/modprobe.d$ cat rtl8192ce.conf
options rtl8192ce ips=0 fwlps=0 debug=2

$ sudo update-initramfs -u

Thank you

---

