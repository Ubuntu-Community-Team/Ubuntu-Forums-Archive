---
title: "Wifi disabled, grayed out box, 10.04, Netbook"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by Raij523 on 2011-05-08
I have had an Acer Aspire One netbook running Ubuntu 10.04 for over a year now, and it has never had a problem with wireless connections until yesterday. The "Enable Wireless" ticker box is grayed out and I have dug through several threads on these forums searching for a way to return the ticker box to normal, but nothings working. I'm using the hardline for the internet now. Ive tried using different connections, rebooting the system several times over the course of yesterday, and several suggestions from various wifi threads in the terminal...

Any help is appreciated!

---

### Post by matt_symes on 2011-05-08
Hi

Open a termial and type these commands. Please post the output back here.

```

sudo lshw -C network
lspci -nnk | grep -iA2 Network
cat /var/lib/NetworkManager/NetworkManager.state
```

When asked for your password, enter it. It will not be echoed to the screen. This is normal.

The commands are case sensitive so the easiest way is to copy and paste them.

Post the output back here between code tags. To do that, highlight the text and hit the # button above where you are typing. Either that or wrap the text in code tags like so

[noparse]```
 output from commands 
```[/noparse]

That will make it easier to read.

Kind regards

---

### Post by Raij523 on 2011-05-09
p { margin-bottom: 0.08in; }  ```
 *-network                
        description: Ethernet interface 
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: eth0 
        version: 02 
        serial: 00:23:8b:74:78:e6 
        size: 10MB/s 
        capacity: 100MB/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
        resources: irq:28 ioport:3000(size=256) memory:51010000-51010fff(prefetchable) memory:51000000-5100ffff(prefetchable) memory:51020000-5103ffff(prefetchable) 
   *-network 
        description: Wireless interface 
        product: AR5001 Wireless Network Adapter 
        vendor: Atheros Communications Inc. 
        physical id: 0 
        bus info: pci@0000:03:00.0 
        logical name: wlan0 
        version: 01 
        serial: 00:24:2b:a6:d5:01 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg 
        resources: irq:18 memory:55200000-5520ffff 
 edenanarchy@edenanarchy-laptop:~$ lspci -nnk | grep -iA2 Network 
 03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01) 
     Kernel driver in use: ath5k 
     Kernel modules: ath5k 
 edenanarchy@edenanarchy-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state  
```
This is what it gave me with that command. I've never had to even use the terminal before now. This netbook has never had a single issue until now. Now my "enable wireless" box is not grayed out and its checked like it's supposted to be, but it still will not connect to any networks. I'm wondering if I need to upgrade to a newer version of Linux or something...

---

### Post by matt_symes on 2011-05-09
Hi
[FONT=monospace]
[/FONT]```
[FONT=monospace]cat /var/lib/NetworkManager/NetworkManager.state[/FONT]
```[FONT=monospace]
That command returned nothing ?

Can you post the output of these two commands please (copy and paste them into a terminal).

[/FONT]```

dpkg -l | grep network-manager
ls /var/lib/NetworkManager/
service network-manager status
```That is a small L after dpkg.

Lets see if we can identify the problem. Upgrading might or might not fix it.

Kind regards

---

### Post by inearlygaveup on 2011-05-09
**SORRY JUST SPOTTED THE 10.04 REF ON THIS POST :redface: - MINE IS A 11.04 PROBLEM**
Please ignore, unless you can point me in the right direction for a fix.


*Hi Matt - sorry to Hi-jack "Raij523" post but I have a Acer Aspire 5102WLMi with the same problem, while he is away can you help me.My print out is as follows*

---

### Post by matt_symes on 2011-05-09
Hi

@ineralygaveup. Glad you didn't give up ;)

There are a number of reason why network manager may be disabled. It could be due to a driver issue, a stopped service or network manager itself could be disabled.
[FONT=monospace]
These two commands will tell us about your hardware and any driver you have installed

[/FONT]```
sudo lshw -C network
lspci -nnk | grep -iA2 network

```

Enter your password when prompted. It will not be echoed to the screen. This is normal.

Linux is case sensitive. Copy and paste each command into a terminal using right click and paste. You can do the reverse and copy and paste from the terminal into your return post by highlighting the text in the terminal. It is easier than taking a screen shot.

This command will tell us if network manager is disabled. The file may not exist. That is not an issue.

 ```
cat /var/lib/NetworkManager/NetworkManager.state
```

To see if network manager is running enter.

```
service network-manager status
```

Post back the results of all these commands. Post the command back between code tags. To do this wrap the text like this

[noparse]```
 output from above commands 
```[/noparse]

Kind regards

---

### Post by inearlygaveup on 2011-05-09
Thanks for your reply - at the moment I am working in 10.10 and can't get back to 11.04 until a lot later tonight.
Will post the info as soon as I can.

---

### Post by sp176 on 2011-05-09
I have the exact same problem.  I never had a problem until yesterday, and suddenly it went down.  I didn't tinker with any settings recently.  

I am dual-booted, so I am working out of windows as I type this, and my wifi works fine, so I know it is not a hardware issue.

I will try your fix above and let you know.

---

### Post by matt_symes on 2011-05-09
Hi

@[sp176]("http://ubuntuforums.org/member.php?u=721631")

The above commands are not fixes. They are trying to identify the problem.

Kind regards

---

### Post by sp176 on 2011-05-09
```
*-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:65:08:79:5e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:dc000000-dc001fff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:0a:74:bf
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:5000(size=256) memory:d4010000-d4010fff(prefetchable) memory:d4000000-d400ffff(prefetchable) memory:d4020000-d402ffff(prefetchable)
```

```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
```

```
[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true

```

```
network-manager start/running, process 966

```

---

### Post by sp176 on 2011-05-09
I can tell the obvious that it is disabled.  How would I go about changing it?

---

### Post by matt_symes on 2011-05-09
Hi

Try these three commands in a terminal one after another. It is easiest if you copy and paste each one into the terminal.

```

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start
```

Enter your password when asked. It will not be echoed to the screen. This is normal.

Please report back.

Kind regards

---

### Post by sp176 on 2011-05-09
Thank you very much.  That worked great!

Do you happen to know how this could have happened in the first place?

---

### Post by inearlygaveup on 2011-05-09
Details as requested

[B]sudo lshw -C network
lspci -nnk | grep -iA2 network[/B]

 *-network:0             

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 1

       bus info: pci@0000:06:01.0

       logical name: eth0

       version: 10

       serial: 00:16:d4:13:8c:71

       size: 10Mbit/s

       capacity: 100Mbit/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s

       resources: irq:21 ioport:a000(size=256) memory:c0210000-c02100ff

  *-network:1

       description: Wireless interface

       product: AR2413 802.11bg NIC

       vendor: Atheros Communications Inc.

       physical id: 2

       bus info: pci@0000:06:02.0

       logical name: wlan0

       version: 01

       serial: 00:16:ce:7f:cf:63

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.3 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg

       resources: irq:22 memory:c0200000-c020ffff

martin@martin-Aspire-5100:~$ 


**cat /var/lib/NetworkManager/NetworkManager.state**

[main]

NetworkingEnabled=true

WirelessEnabled=true

WWANEnabled=true

martin@martin-Aspire-5100:~$ 



**service network-manager status**

martin@martin-Aspire-5100:~$ service network-manager status

network-manager start/running, process 1056

martin@martin-Aspire-5100:~$ 

[B][I]MOVE AWAY FROM ROUTER 10 - 15 mtrs

Results in are exactly the same but the Network Connections just doesn’t connect to wireless and eventually times out with the Disconnected signal.

Plug the eth0 in and it connects wifi for a while then disconnects again.

(I have been using 10.10 wireless all evening with no problems)[/I][/B]

---

### Post by matt_symes on 2011-05-09
Hi

@inearlygaveup.

I take it then wireless on 11.04 is not disabled but you just cannot connect as it disconnects you right away ?

Let's have a look at the revision of the card. Your lspci command did not work correctly so please you could repost the output of

```
lspci -nnk | grep -iA2 network
```Also, i want you to try to connect, using 11.04, to your access point. When it disconnects open a terminal and type

```
dmesg | grep -E "wlan0|ath5k" | tail -n30
```Post the output of those two commands between code tags to make it easier to read. To do this wrap the output in code tags so it will look like this.

[noparse]```
 output from commands
```[/noparse]

It will look like this on the forums

```
 output from commands
```Much easier to read.

BTW: What type of encryption are you using ? WEP, WPA ?

Kind regards

---

### Post by inearlygaveup on 2011-05-10
```
martin@martin-Aspire-5100:~$ lspci -nnk | grep -iA2 network
martin@martin-Aspire-5100:~$ 
```

No response

```
martin@martin-Aspire-5100:~$ dmesg | grep -E "wlan0|ath5k" | tail -n30
[   81.276049] wlan0: authentication with 00:e0:4d:13:5a:74 timed out
[   91.695503] wlan0: authenticate with 00:e0:4d:13:5a:74 (try 1)
[   91.697258] wlan0: authenticated
[   91.697339] wlan0: associate with 00:e0:4d:13:5a:74 (try 1)
[   91.699783] wlan0: RX AssocResp from 00:e0:4d:13:5a:74 (capab=0x431 status=0 aid=1)
[   91.699791] wlan0: associated
[   91.700886] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  101.840058] wlan0: no IPv6 routers present
[  816.634750] wlan0: deauthenticating from 00:e0:4d:13:5a:74 by local choice (reason=3)
[  819.351551] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  828.439131] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 1/3)
[  828.636088] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 2/3)
[  828.836095] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 3/3)
[  829.036116] wlan0: direct probe to 00:e0:4d:13:5a:74 timed out
[  831.998688] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  831.998784] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 1/3)
[  832.196072] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 2/3)
[  832.422822] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  832.607841] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 1/3)
[  832.804091] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 2/3)
[  833.008135] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 3/3)
[  833.208140] wlan0: direct probe to 00:e0:4d:13:5a:74 timed out
[  835.488260] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 1/3)
[  835.688113] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 2/3)
[  835.888148] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 3/3)
[  836.088123] wlan0: direct probe to 00:e0:4d:13:5a:74 timed out
[  845.123397] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 1/3)
[  845.320092] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 2/3)
[  845.520092] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 3/3)
[  845.720082] wlan0: direct probe to 00:e0:4d:13:5a:74 timed out
martin@martin-Aspire-5100:~$ 

```

> BTW: What type of encryption are you using ? WEP, WPA ?
WPA2

NOTE
I have also installed the Wicd Network Manager this shows that I am connect even though I am not

---

### Post by matt_symes on 2011-05-10
Hi

> No responseI did not expect that. Could you post the output of

```
lspci -nnk
```and also 

```
lsusb
```Can i ask why you are using WICD. Did network manager also give you problems ?
[FONT=monospace]
[/FONT]> 819.351551] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[  828.439131] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 1/3)
[  828.636088] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 2/3) 
[  828.836095] wlan0: direct probe to 00:e0:4d:13:5a:74 (try 3/3) 
[  829.036116] wlan0: direct probe to 00:e0:4d:13:5a:74 timed outThis looks like it might be an issue here

Kind regards

---

### Post by matt_symes on 2011-05-10
Hi

@inearlygaveup

Have a read of this

[https://lkml.org/lkml/2011/5/5/152](https://lkml.org/lkml/2011/5/5/152)

I looks like it might be a kernel bug, a regression. They are aware of it (it's dated 5th May 2011).

Thst would make sense if the same card and driver worked in 10.10 but not in 11.04.

Same card and driver as you, and by the looks of it same kernel 2.6.38.

Might have to sit tight for a fix to come down from on high.

Kind regards

---

### Post by inearlygaveup on 2011-05-10
```
martin@martin-Aspire-5100:~$ lspci -nnk
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel modules: ati-agp
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
	Kernel modules: shpchp
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: ohci_hcd
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Kernel driver in use: k8temp
	Kernel modules: k8temp
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
06:02.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0418]
	Kernel driver in use: ath5k
	Kernel modules: ath5k
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
06:04.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
06:04.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
martin@martin-Aspire-5100:~$ 

```

```
martin@martin-Aspire-5100:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
martin@martin-Aspire-5100:~$ 
```

Network Manager is the first one I had installed giving the original problem. I installed WICD just to see if it made any difference - it didn't.

Should I remove WICD and stick with Network Manager.

---

### Post by inearlygaveup on 2011-05-10
Hi and thanks for your time, I did have a look at [https://lkml.org/lkml/2011/5/5/152](https://lkml.org/lkml/2011/5/5/152)

Got the drift of the conversation although most went straight over the top of my head.

I agree that you can sometimes get it to connect then walk to another room and if lucky it stays connected, I have had it connect all evening but then on others it drops the connection within a couple of minutes.

Then I have to reboot into 10.10.

As you said I will wait for the fix.

Thanks again for your help.

kind regards

Martin

---

