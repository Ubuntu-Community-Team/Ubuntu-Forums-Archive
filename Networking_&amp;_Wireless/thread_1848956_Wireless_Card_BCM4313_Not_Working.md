---
title: "Wireless Card BCM4313 Not Working"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by eclipsechasers2 on 2011-09-23
Before Natty, my wireless card had not had a problem. After Natty was installed, it would intermittently come up with the wireless card not working (about 50% of the time). This week, a Broadcom update was pushed, and, since that was installed, the wireless card is not working 100% of the time. (Machine is dual boot - no problem in Windows.) Have uninstalled and reinstalled bmcwl-kernel-source several times; no effect. Documentation indicates that b43 isn't usable for BMC4313, but tried some of the suggested b43 solutions just in case - no joy. Machine is a Dell Inspiron 14R. What can I do to get this working?

---

### Post by eclipsechasers2 on 2011-09-23
Meant to mention that the following are all installed:
bcmwl-kernel-source
broadcom-sta-common
broadcom-sta-source
No b43 packages are installed.

---

### Post by garvinrick4 on 2011-09-23
**Installing STA drivers**

  
**10.04 (Lucid Lynx), 10.10 (Maverick Meerkat) **11.04 (Natty Narwhal)**

 Issue: _eth%d: 5.100.82.38 driver failed with code 21_ and wireless doesn't work.  You need to install Maverick's driver from [http://packages.ubuntu.com]("http://packages.ubuntu.com/") 
Supported models include: 
BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, **BCM43227, **BCM43228 
 
**STA - Internet access**

 **Step 1.**  
Install the STA hybrid drivers/firmware from the [restricted repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") using the **Software Centre** or the **Synaptic Package Manager** (Under the desktop menu **System > Administration > Synaptic Package Manager**) and search for the bcmwl-kernel-source package and install **or** in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**) issue the following commands: 

~$ sudo apt-get update ~$ sudo apt-get install bcmwl-kernel-source**Step 2.** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use. 
**Note:**[COLOR=Red]  In Ubuntu 11.04[/COLOR], if the driver fails to load, you may need to reinstall  the bcmwl-kernel-source package. This can be done from Synaptic ->  Mark for Reinstallation.  
**Note:** A computer restart may be required before using the wifi card.

Keep link handy:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by hreichgott on 2011-09-23
I also started having this problem after yesterday's update.
My wireless works on about 1 out of 10 boots.
The non-working boots take about 90 seconds, and the working boots take about 35 seconds, which was normal booting time before the update.

Here is lspci | grep Network
07:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

Anyone have suggestions either on how to fix this, or on how to revert back to the previous Broadcom driver? It worked fine.

I tried garvinrick4's advice, and got only "bcmwl-kernel-source is already the newest version".

---

### Post by garvinrick4 on 2011-09-23
Have you checked additional drivers in system to make sure activated and rebooted or ran:
```
sudo modprobe -r b43 ssb wl
``` ```
sudo modprobe wl
```If does not work will it work in live cd.
Install driver then run above two pieces of code.

---

### Post by nickfank on 2011-09-23
My problem is nearly identical, so I'll add it to this thread. My most recent attempt at a solution is the one listed in #3 Here's the whole saga:


I just did an upgrade from 10.10 32 bit to **11.04, 64 bit**. Before the upgrade, my wireless worked fine. 

My computer is a **Dell Vostro 1720 laptop with a BCM4312** controller. It has a switch on the side to turn wireless on/off, and a blue light to indicate when the wirelss controller is on. During all of my attempts, the switch was on, and the "active" light was also on.

Here's the log of basic diagnostic info:

nickf@nickf-Vostro-1720:~$ **lspci -vvnn| grep 14e4**
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

nickf@nickf-Vostro-1720:~$** ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:24:e8:d6:9c:fe  
          inet addr:172.18.64.214  Bcast:172.18.255.255  Mask:255.255.0.0
          inet6 addr: fe80::224:e8ff:fed6:9cfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5577994 (5.5 MB)  TX bytes:828915 (828.9 KB)
          Interrupt:47 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

nickf@nickf-Vostro-1720:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

nickf@nickf-Vostro-1720:~$ **lsmod | grep sta**
nickf@nickf-Vostro-1720:~$ **lsmod | grep b43**
nickf@nickf-Vostro-1720:~$ **lsmod | grep wl**
wl                   2568244  0 
lib80211               14991  2 lib80211_crypt_tkip,wl


A chunk of **dmesg **that might apply:

[   12.055726] r8169 0000:08:00.0: eth0: link down
[   12.055735] r8169 0000:08:00.0: eth0: link down
[   12.056697] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.059489] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.059493] Disabling lock debugging due to kernel taint
[   12.100728] wl 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.100742] wl 0000:0e:00.0: setting latency timer to 64
[   12.146586] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.146662] HDA Intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   12.146694] HDA Intel 0000:00:1b.0: setting latency timer to 64


nickf@nickf-Vostro-1720:~$ **sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:d6:9c:fe
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.18.64.214 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 0c:60:76:01:7a:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa000000-fa003fff

**iwlst scan** reports  no interfaces supporting scanning.

nickf@nickf-Vostro-1720:~$ **sudo /etc/init.d/networking restart**
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                            Ignoring unknown interface eth0=eth0.



Here's what I've already tried:

1) I read a number of suggestions in the "sticky" thread for Broadcom 43xx cards about dealing with this problem, but none seemed to work. Many suggested amounted to "get rid of the current driver & get the old (10.10) version", but I couldn't seem to get the old version removed, so...

2)I did "clean" reinstall of 11.04 on my laptop using the "replace" option. I did not opt for downloading updates or obtaining third-party drivers, hoping that this would give me a clean slate to work from.

3)I then used synaptic package manager to install "firmware-b43lpphy-installer" and rebooted. Still no wireless. Used "Additional Drivers" to active the listed STA driver and rebooted. No luck still.

4) Following advice that I should replace the current version with the older driver, I uninstalled the current version using sudo apt-get remove bcmwl-kernel-source(was told it wasn't installed, so not removed. Then downloaded bcmwl-kernel-source-5.60.48.36+bdcom-0ubuntu5_amd64.deb and installed it. Activated the driver via "Additional Drivers" and restarted. still no wireless.

5) Following the troubleshooting chart posted in the sticky thread, decided I needed the "wl" driver. Uninstalled firmware-b43-lpphy-installer and b43-fwcutter using synaptic package manager. Installed broadcom-sta-common and broadcom-sta-source via synaptic. Restarted. No Wireless. Activated in "Additional Drivers" and rebooted. Still No wireless.

6) Decided I'm shooting in the dark & need help on diagnosis, and posted this... What diagnostics should I try next to narrow down the problem?

Thanks!

---

### Post by garvinrick4 on 2011-09-23
> Anyone have suggestions either on how to fix this, or on how to revert back to the previous Broadcom driver? It worked fine.

I tried garvinrick4's advice, and got only "bcmwl-kernel-source is already the newest version".Seems like you want or need anothers advice I will drop out, hope you get up and running, i would see
if live Cd works, if does it is in your install, might have other bcm installed check your bcm and b43 in synaptics in search 
just to make sure nothing else loaded. Make sure you have nothing blocked.
rfkill list
lots of good users out there for network cards (bcm has oodles of cards out there not usually a problem)

---

### Post by garvinrick4 on 2011-09-23
@ elipsechaser2
 Others started posting and thought it was you wanting other help.

[COLOR=Red]Other users please start your own post instead of highjacking this one.[/COLOR]

elipsechaser2 are you running?

---

### Post by nickfank on 2011-09-23
More info:

I've also tried simply booting from the "live" usb and get the same symptoms, so it appears to be something specific to my hardware rather than something odd about my installed version.

Also tried garvinrick4's suggestion about using modprobe to inactivate/reactivate drivers. No Luck there. (sigh!)

Any other thoughts?

---

### Post by nickfank on 2011-09-23
Sorry about the "highjack" I'm new to the forum and thought I should join in here. Will start a new thread now that I know the etiquette. Thanks for the correction.

Sheepishly, 
        -Nick

---

### Post by eclipsechasers2 on 2011-09-23
No, my wireless is still not working. My attempts, and symptoms, are similar to the others who posted. None of the suggestions so far seems to be effective, in particular reinstalling bcmlw-kernel-source had no effect. I have not yet tried to obtain the driver for maverick.

---

### Post by eclipsechasers2 on 2011-09-23
Also, sudo modprobe was not effective. I do not have a live CD to use. Before I try that, let me ask - if it does work there, what would that suggest that I need to get it working from my hard drive?

BTW, although I'm not sure of the proper protocol, I certainly have no objection to others with the same problem joining this thread; I'm sure that if a solution is ultimately determined, it would be good to have it centralized in one thread. (Which I suppose is the purpose of the "sticky" thread, but the solutions mentioned there aren't working for me and this weeks push which seems to have broken things is a new factor.)

---

### Post by nickfank on 2011-09-23
I'll cross-post back here if I get a good solution on the thread I started. (I think we're in a nearly identical position.) -Nick

---

### Post by garvinrick4 on 2011-09-23
> **nickfank said:**
> Sorry about the "highjack" I'm new to the forum and thought I should join in here. Will start a new thread now that I know the etiquette. Thanks for the correction.

Sheepishly, 
        -Nick That is OK nickfank it takes a bit to get used to forum, start your own threads and when
you see something close to your problem read that thread for help also. 
Welcome to the Forums Nick and enjoy your Ubuntu and feel welcome here.

---

### Post by garvinrick4 on 2011-09-23
List these so other Network users can see so as to know what they are working with.
```
lscpi -k
``````
rfkill list
```Do not give up it is broadcom and they will work in ubuntu they are a previlent card in a lot
of machines, Dells use them often. If not driver could be a switch or hard blocked or softblocked. Post info you will get help. Broadcom is usually so simple
am sorry you are not running as of yet.

---

### Post by garvinrick4 on 2011-09-23
> BTW, although I'm not sure of the proper protocol, I certainly have no  objection to others with the same problem joining this thread; I'm sure  that if a solution is ultimately determined, it would be good to have it  centralized in one thread. (Which I suppose is the purpose of the  "sticky" thread, but the solutions mentioned there aren't working for me  and this weeks push which seems to have broken things is a new factor.) When you get your thread solved you will mark it as Solved in Thread tools in upper
right of page and others will see your title and Solved and use it. There are also things called spiders
crawling around in here and when you google search your thread will pop up. Look at home page
of Ubuntu forums says 663 members 5000 guests and 63 spiders. People all over the World get to
see your fix and this is about the biggest Linux Forum there is. You can post on another distro and wait
2 days for first reply.  Search engines need info so they have spiders crawling around the web.
#It is hard for users to try to follow two and three or more users in one thread so it is better if everyone has
their own thread. Plus you do want the thread to be about your specific problem so others searching may
benifit from. Rick

## Was kind of you to worry about the others though, a Ubuntu users quality.

---

### Post by eclipsechasers2 on 2011-09-23
Here is the response from "lspci -k":

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
        Subsystem: Dell Device 0456
        Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
        Subsystem: Dell Device 0456
        Kernel driver in use: i915
        Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
        Subsystem: Dell Device 0456
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
        Subsystem: Dell Device 0456
        Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
        Subsystem: Dell Device 0456
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
        Subsystem: Dell Device 0456
        Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
        Subsystem: Dell Device 0456
        Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
        Subsystem: Dell Device 0456
        Kernel driver in use: ahci
        Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
        Subsystem: Dell Device 0456
        Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
        Subsystem: Dell Device 0456
        Kernel driver in use: intel ips
        Kernel modules: intel_ips
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
        Subsystem: Dell Device 0010
        Kernel driver in use: wl
        Kernel modules: wl, brcm80211
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
        Subsystem: Dell Device 0456
        Kernel driver in use: atl1c
        Kernel modules: atl1c
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
        Subsystem: Intel Corporation Device 8086
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
        Subsystem: Intel Corporation Device 8086
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
        Subsystem: Intel Corporation Device 8086
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
        Subsystem: Intel Corporation Device 8086
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
        Subsystem: Intel Corporation Device 8086
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
        Subsystem: Intel Corporation Device 8086

---

### Post by eclipsechasers2 on 2011-09-23
Here is the output from "rfkill list":

0: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

---

### Post by eclipsechasers2 on 2011-09-23
Just noticed that the forum changed some of the text in the output from lspci to smileys. In both cases, the relevant text actually reads "(rev 18)"

---

### Post by eclipsechasers2 on 2011-09-23
Hmm, it changed it even though "preview" showed it as text. It should be:
Left parenthesis, followed by rev 18, followed by right parenthesis.

---

### Post by garvinrick4 on 2011-09-23
> I do not have a live CD to use. Before I try that, let me ask - if it does work there, what would that suggest It would suggest that works fine, just have tried so many drivers there are just to many
installed and they are hendering the correct driver from loading. Something strange here get quite a few
new users who need to load correct broadcom drivers but usually not a problem. There are a lot of
users with your card and not a lot of Threads not Solved in Broadcom.

---

### Post by pirlouis on 2011-09-24
My card (bcm4313) also "stopped working" after the update - no sign of it anywhere (ifconfig or iwconfig).

I reloaded b43 module manually and it appeared now as ***eth1*** instead of its previous ***wlan0***. 
Works again.

---

### Post by eclipsechasers2 on 2011-09-26
Could you please expand on "loading b43 manually"? Does that mean uninstalling broadcom-sta-common, broadcom-sta-source, and bcmwl-kernel-source, and installing b43-fwcutter (and firmware-b43-installer?) in their place? Any additional steps?

---

### Post by pirlouis on 2011-09-28
> **eclipsechasers2 said:**
> Could you please expand on "loading b43 manually"? Does that mean uninstalling broadcom-sta-common, broadcom-sta-source, and bcmwl-kernel-source, and installing b43-fwcutter (and firmware-b43-installer?) in their place? Any additional steps?

Just a modprobe b43 (module wasn't loaded automatically after update) and card popped up as eth1 (eth0 being the wired nic) while before it was wlan0. I reconfigured wicd to use eth1 instead of wlan0 and it took over fine. Maybe not the same problem as you, but since this issue occurred after the same update, I thought it could be related.

---

