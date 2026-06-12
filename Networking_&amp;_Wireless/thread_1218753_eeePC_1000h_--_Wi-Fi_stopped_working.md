---
title: "eeePC 1000h -- Wi-Fi stopped working"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by joeinbend on 2009-07-21
I have 9.04 Desktop on my 1000h eeePC, and over the weekend my wi-fi stopped working. not sure what's going on! It's definitely something in Ubuntu, because if I reboot and go into Windows (ugh..), it is working normally. I'm guessing it's due to an update, unfortunately I'm sort of at a loss for where to look. I had turned on all update options (including the Jaunty Proposed, and Unsupported) to fix a problem a few months back, and I should have turned those updates off once the problem was fixed! Can you guys point me in the right direction to pull the info I need to diagnose this?

Thanks!

---

### Post by martinbaselier on 2009-07-21
Open a terminal (it's in accessories )

(you can copy the command and paste it in the terminal either by ctrl+shift+v or by choosing paste, in the right mouse button menu - if you use a 3 button mouse, you can use the middle mouse button to paste a selected text)

When you open a terminal and type **lspci**, you will see your card in between. 
next type 
sudo lspci -v -s CARDNUMBER. (replace this with the number you see in the list)

example: 
```

lspci
...
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
**06:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)**
06:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
...
sudo lspci -v -s 06:03.0
06:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 1001
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at c8214000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200



```
Could you please post the output for your card, to show a bit more details. (you can select the text in the terminal with your mouse and then copy with ctrl+shift+c or by selecting copy from the right mouse button menu)

Next thing interesting would be to know a bit more about the wireless connection. For this type:
**iwconfig**
please post the output of that too.

---

### Post by joeinbend on 2009-07-22
Sorry for the late reply, I did follow your guide, and got some strange results. My 802.11 card comes up as a RaLink RT2860. The line below that raises an eyebrow is the "access denied". Here's the output of my lspci -v -s 01:00.0

01:00.0 Network controller: RaLink RT2860
    Subsystem: RaLink Device 2790
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fbef0000 (32-bit, non-prefetchable) [size=64k]
    Capabilities: <access denied>
    Kernel driver in use: rt2860
    Kernel modules: rt2860sta

---

### Post by superprash2003 on 2009-07-23
post output of** lshw -C network**

---

### Post by joeinbend on 2009-07-23
Here is my output:

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:01:98:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=half firmware=L1e ip=192.168.4.189 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:5d:a8:62
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:15:d7:72:4e:f7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Crafty Kisses on 2009-07-23
> **joeinbend said:**
> I have 9.04 Desktop on my 1000h eeePC, and over the weekend my wi-fi stopped working. not sure what's going on! It's definitely something in Ubuntu, because if I reboot and go into Windows (ugh..), it is working normally. I'm guessing it's due to an update, unfortunately I'm sort of at a loss for where to look. I had turned on all update options (including the Jaunty Proposed, and Unsupported) to fix a problem a few months back, and I should have turned those updates off once the problem was fixed! Can you guys point me in the right direction to pull the info I need to diagnose this?

Thanks!

I guess the first thing to do is narrow down what wireless card you have, since it's an Eee PC, you probably have Atheros. What are the results of the following?
```
lspci
```

---

### Post by joeinbend on 2009-07-24
We actually already covered that, details are in post #3. Thanks!

---

### Post by joeinbend on 2009-07-24
Well unfortunately for "the cause", I didnt have time to monkey around with this problem anymore. I reinstalled 9.04, and turned on the Jaunty Proposed, but not the Unsupported updates, ran all updates, rebooted, and all is well, no more broken Wi-Fi. If anyone else experiences the problem I did, I hope a resolution will be found.

---

### Post by lambdacore on 2009-08-07
i do have this annoying, annoying problem.
i have an eee pc 1000 ha and ubuntu network remix (9.04).

once in a while, like almost once a day, the wifi just deconnects.
if i reboot, the wifi detects no networks at all.
sometimes, after a couple of reboots, it starts working again.
i hate that.

here's the output asked up to now :



link@lambdacore:~$ sudo lspci -v -s 01:00.0
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Device 1a3b:1026
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k 






link@lambdacore:~$ iwconfig
lo        no wireless extensions. 

eth0      no wireless extensions.  

wmaster0  no wireless extensions.  

wlan0     IEEE 802.11bg  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated              Tx-Power=0 dBm              Retry min limit:7   RTS thr:off   Fragment thr=2352 B              Power Management:off           Link Quality:0  Signal level:0  Noise level:0           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 







link@lambdacore:~$ sudo lshw -C network   *-network                       description: Ethernet interface        product: L1e Gigabit Ethernet Adapter        vendor: Attansic Technology Corp.        physical id: 0        bus info: pci@0000:03:00.0        logical name: eth0        version: b0        serial: 00:24:8c:68:12:11        capacity: 100MB/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair   *-network DISABLED        description: Wireless interface        product: AR242x 802.11abg Wireless PCI Express Adapter        vendor: Atheros Communications Inc.        physical id: 0        bus info: pci@0000:01:00.0        logical name: wmaster0        version: 01        serial: 00:22:43:7c:43:2b        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless        configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg   *-network DISABLED        description: Ethernet interface        physical id: 1        logical name: pan0        serial: ea:6c:6b:1a:51:bb        capabilities: ethernet physical        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by jdcipher on 2009-09-01
I'm in the same boat here... I have 9.04 Netbook Remix installed fresh - I can connect to unprotected wireless networks and even WEP enabled, but have had little luck getting my netbook to connect to my WPA2 Personal (TKIP) encrypted wifi access point.

I have tried the following:
Fresh install, no updates
Fresh install, recommended updates (approved)
Switched internal wifi card to dell 1390 card (and installed the correct drivers)

In each cae, the netbook was able to connect to unprotected wifi networks.  If I reboot into Windows XP, it works find (both the dell 1390 card and the RALink card work fine).

I have also installed 9.04 desktop edition on my thinkpad T60, and it works, but takes a LONG time to connect.  I used to have OS X on the thinkpad and my eee pc - and it could connect nearly instantly on both machines.

So, I'm sure it's not a hardware issue and I'm at a loss as to why it's happening.  If anyone can help out, that would be greatly appreciated.

Thanks,
Jeff

---

### Post by Flash858 on 2009-09-01
After you reboot Ubuntu, hit F2. I would wager the wlan is disabled in the bios. I have been having the same exact issue, and the workaround is to enable it in the bios, hit f10, say OK, then let it boot into Ubuntu.

---

### Post by jdcipher on 2009-09-01
Hi - Thanks for the response.  I know the WLAN adapter is enabled in the bios because it works fine with WEP and unencrypted networks.  It also works fine in XP.  So, it must be a driver issue.

Thanks,
Jeff

---

### Post by drpjkurian on 2009-09-01
Hi lambdacore

Well i think you can try madwifi drivers for your atheros card. I have posted a thread of how to install madwifi for jaunty. 
See my thread [http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)

with regards
Dr Kurian

---

### Post by DamITman on 2009-09-01
I recently encountered this problem, I'm willing to wager you're using EEEbuntu & you've just installed the linux-kernel-eb update. This killed my Atheros wireless card, and due to lack of previous experience lead to several clean re-installs to isolate which update killed it. 

After all that I decided it would be best to avoid that update until my knowledge of linux expands a bit.


*edit* Dr. Kurians' post regarding madwifi-ng came in handy though after official kernel updates.

---

### Post by jdcipher on 2009-09-01
> **drpjkurian said:**
> Hi lambdacore

Well i think you can try madwifi drivers for your atheros card. I have posted a thread of how to install madwifi for jaunty. 
See my thread [http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)

with regards
Dr Kurian


Thanks so much... I will try it tonight when I am home and report back.

Jeff

---

### Post by jdcipher on 2009-09-01
> **jdcipher said:**
> Thanks so much... I will try it tonight when I am home and report back.

Jeff


I followed the instructions, and think i have madwifi installed... but no change... still won't connect to my wpa2 personal network... :(

---

### Post by jdcipher on 2009-09-02
> **jdcipher said:**
> I followed the instructions, and think i have madwifi installed... but no change... still won't connect to my wpa2 personal network... :(

After much tweaking and playing around with wireless settings... i found the problem.  When I disable the SSID broadcast my ubuntu eeepc cannot connect to the access point.  I re-enabled ssid broadcast and now it works!

---

