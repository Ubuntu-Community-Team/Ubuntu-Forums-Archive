---
title: "Sudden Wireless Loss after 3 months fine, No Router Association"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by thetorybear on 2010-10-28
Greetings and salutations. 

I decided to join the forums because I am quite at the end of my wits; I've been trying to restore my wireless for the last two days, to no avail. 

I'm running 10.4 on an old Inspiron E1405. It's been running pretty much flawlessly for the last two or three months. Then, two mornings ago, I logged in and discovered that my wireless for some reason would not connect. It had been perfectly fine up to that point. 

My card is still working, as far as I can tell: the computer recognizes the device, I can see the local networks, I just can't connect to them. Now, my adorable machine is not associating with router - I can't ping it, but as far as I know, NOTHING in my home network has changed this week.

I suppose the upshot of all this is that I've been learning how to use Terminal, so that's kinda fun, but really, I cannot figure this out. I've been through the trouble shooting guides and I've been browsing the forum posts and nothing is working.

I would love to not be purchasing a 100 foot ethernet cable during the next few days. 
Does anyone have any ideas? 
Many thanks.

---

### Post by thetorybear on 2010-10-28
And in case any of this helps shed some light:

> victoriarose@victoriarose-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:af:aa:c4  
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feaf:aac4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43173 errors:2 dropped:2 overruns:0 frame:0
          TX packets:21432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29779811 (29.7 MB)  TX bytes:3288924 (3.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20544 (20.5 KB)  TX bytes:20544 (20.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:b0:95:db  
          inet6 addr: fe80::213:2ff:feb0:95db/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46953 (46.9 KB)  TX bytes:6192 (6.1 KB)

victoriarose@victoriarose-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
victoriarose@victoriarose-laptop:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
unknown                  ether   00:14:bf:0a:f2:de   C                     eth0
victoriarose@victoriarose-laptop:~$ sudo iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 00:90:4C:5F:00:2A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:off
                    ESSID:"Joe's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000199c9db86
                    Extra: Last beacon: 1560ms ago
                    IE: Unknown: 000D4A6F652773204E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020103

---

### Post by DirtyPC on 2010-10-28
> **thetorybear said:**
> Greetings and salutations. 

I decided to join the forums because I am quite at the end of my wits; I've been trying to restore my wireless for the last two days, to no avail. 

I'm running 10.4 on an old Inspiron E1405. It's been running pretty much flawlessly for the last two or three months. Then, two mornings ago, I logged in and discovered that my wireless for some reason would not connect. It had been perfectly fine up to that point. 

My card is still working, as far as I can tell: the computer recognizes the device, I can see the local networks, I just can't connect to them. Now, my adorable machine is not associating with router - I can't ping it, but as far as I know, NOTHING in my home network has changed this week.

I suppose the upshot of all this is that I've been learning how to use Terminal, so that's kinda fun, but really, I cannot figure this out. I've been through the trouble shooting guides and I've been browsing the forum posts and nothing is working.

I would love to not be purchasing a 100 foot ethernet cable during the next few days. 
Does anyone have any ideas? 
Many thanks.
Did you have form of security (WEP/WPA?) also does it say you have connected to the router.. but you dont actually get internet? That seems to be a common problem, too much load on the internet, which only seems to happen on ubuntu. Unplug your modem first, than your router then plug all back in...

---

### Post by thetorybear on 2010-10-28
No, we're running an unsecured network, actually, with two laptops and two desktops accessing the system. Have never been kicked off before and it's fairly standard for all 4 computers to be online simultaneously, so I don't think overload is the issue. 

But no, it doesn't seem that I'm connected to the router.

Have tried unplugging the router and modem... I'll try again, though.

---

### Post by grahammechanical on 2010-10-28
From ifconfig I see that eth0 is "running" but wlan0 is not running. Is the wireless connection that you want in the printout from iwlist wlan0 scan? The fact that you are detecting wireless networks would indicate that wireless is working. Have you tried left clicking the network icon and choosing from the list of available connections? Is networking and wireless ticked as enabled as shown by a left click on the network icon? I am sorry if you have already played around with all this stuff.

regards.

---

### Post by thetorybear on 2010-10-28
I appreciate y'all taking time to respond. 

Yes, networking and wireless are enabled in the dropdown. When I select my wireless network and try to connect, the little bars in the wireless icon light up like they're trying to connect and this continues for approximately a full thirty seconds; then it tells me "Wireless Network - You are now disconnected."

I see what you mean when you say "that eth0 is "running" but wlan0 is not running." As for > Is  the wireless connection that you want in the printout from iwlist wlan0  scan?  
Yes- the network that shows up in the scan is the one I want to connect to.  If that's what you're asking -please correct me if I'm wrong. 

I know I didn't change any settings on my computer that night, and I'm fairly certain that no one altered the network.

Also, I didn't mention this previously, but I tried to solve the problem by upgrading to 10.10, and it still wouldn't let me connect to the local network. So then I did a re-install of 10.4 from the disc to no avail, and even tried running Ubuntu live from the CD, and I couldn't connect. Just to put a little more information on the table.

Any thoughts, Ubuntu companions?

---

### Post by maclenin on 2010-10-28
I am also [struggling with wireless issues, which came on suddenly]("http://ubuntuforums.org/showthread.php?t=1579095") (seemlingly just after a kernel upgrade). I can still connect - but the connection is sluggish at best - and there are frequent drop-outs....

A couple of additional bits you might want to toss on the table - using your newly-discovered terminal skills (so that those more able than I can help suss out your issue):

Type: **sudo lshw -C network** into the terminal to find out what kind of wireless card are you using.

Type: **dmesg** into the terminal and look through the output for anything suspicious.

Also, via your file manager of choice, take a peek at your *syslog*, found at /var/log/syslog for anything else that might provide a few additional clues.

Good luck!

---

### Post by thetorybear on 2010-10-28
Thanks maclenin, those two commands were new... Good luck to you as well. :)

Here's what they gave me:

> victoriarose@victoriarose-laptop:~$ sudo lshw -C network

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:b0:95:db
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:dfdff000-dfdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:af:aa:c4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.148 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:df9fe000-df9fffff


And now for the one that really means nothing to me, interesting though it is. 
Clarifications super welcome. **dmesg **produced a super lengthy result....

> [13320.288636] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[13320.288642] ata_piix 0000:00:1f.2: setting latency timer to 64
[13320.288676] ata1.00: _GTF evaluation failed (AE 0x1001)
[13320.288700] ata2.00: _GTF evaluation failed (AE 0x1001)
[13320.288757] b44 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[13320.366110] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[df9fd800-df9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[13320.372185] sdhci-pci 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[13320.400865] sd 0:0:0:0: [sda] Starting disk
[13321.356482] ata2.00: configured for UDMA/33
[13321.980500] ata1.00: configured for UDMA/100
[13321.997483] PM: resume of drv:sd dev:0:0:0:0 complete after 1596.613 msecs
[13322.016836] PM: resume of devices complete after 1853.253 msecs
[13322.016963] PM: resume devices took 1.860 seconds
[13322.016998] PM: Finishing wakeup.
[13322.016999] Restarting tasks ... done.
[13322.319894] Registered led device: iwl-phy0::radio
[13322.321190] Registered led device: iwl-phy0::assoc
[13322.322128] Registered led device: iwl-phy0::RX
[13322.323062] Registered led device: iwl-phy0::TX
[13322.324412] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13322.338859] ADDRCONF(NETDEV_UP): eth0: link is not ready
[13326.000311] b44: eth0: Link is up at 100 Mbps, full duplex.
[13326.000320] b44: eth0: Flow control is off for TX and off for RX.
[13326.000532] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[13335.410246] wlan0: deauthenticating from 00:90:4c:5f:00:2a by local choice (reason=3)
[13335.412694] wlan0: direct probe to AP 00:90:4c:5f:00:2a (try 1)
[13335.414758] wlan0: direct probe responded
[13335.414766] wlan0: authenticate with AP 00:90:4c:5f:00:2a (try 1)
[13335.416617] wlan0: authenticated
[13335.416649] wlan0: associate with AP 00:90:4c:5f:00:2a (try 1)
[13335.419040] wlan0: RX AssocResp from 00:90:4c:5f:00:2a (capab=0x401 status=0 aid=3)
[13335.419047] wlan0: associated
[13335.420806] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13336.112050] eth0: no IPv6 routers present
[13345.816121] wlan0: no IPv6 routers present
[13380.459521] wlan0: deauthenticating from 00:90:4c:5f:00:2a by local choice (reason=3)
[13824.000224] b44: eth0: Link is down.
[13860.000326] b44: eth0: Link is up at 100 Mbps, full duplex.
[13860.000335] b44: eth0: Flow control is off for TX and off for RX.
[15008.000195] b44: eth0: Link is down.
[15075.000323] b44: eth0: Link is up at 100 Mbps, full duplex.
[15075.000331] b44: eth0: Flow control is off for TX and off for RX.
[15344.963876] b44: eth0: powering down PHY
[15345.779052] PM: Syncing filesystems ... done.
[15345.779611] PM: Preparing system for mem sleep
[15345.779614] Freezing user space processes ... (elapsed 0.00 seconds) done.
[15345.782504] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[15345.782555] PM: Entering mem sleep
[15345.782570] Suspending console(s) (use no_console_suspend to debug)
[15345.782986] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[15345.980471] sd 0:0:0:0: [sda] Stopping disk
[15346.952349] PM: suspend of drv:sd dev:0:0:0:0 complete after 1169.357 msecs
[15347.359109] PM: suspend of drv:psmouse dev:serio1 complete after 406.673 msecs
[15347.461060] ACPI handle has no context!
[15347.461069] sdhci-pci 0000:02:01.1: PCI INT B disabled
[15347.461076] ACPI handle has no context!
[15347.496173] b44 0000:02:00.0: PCI INT A disabled
[15347.496183] ACPI handle has no context!
[15347.528314] ata_piix 0000:00:1f.2: PCI INT B disabled
[15347.544124] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[15347.544140] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[15347.544155] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[15347.544170] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[15347.544184] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[15347.648250] HDA Intel 0000:00:1b.0: PCI INT A disabled
[15347.664108] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.899 msecs
[15347.689607] i915 0000:00:02.0: PCI INT A disabled
[15347.704374] PM: suspend of devices complete after 1921.600 msecs
[15347.704381] PM: suspend devices took 1.924 seconds
[15347.720442] PM: late suspend of devices complete after 16.054 msecs
[15347.724897] ACPI: Preparing to enter system sleep state S3
[15347.725414] Disabling non-boot CPUs ...
[15347.725435] Back to C!
[15347.725435] CPU0: Thermal monitoring enabled (TM2)
[15347.725435] Force enabled HPET at resume
[15347.725435] ACPI: Waking up from system sleep state S3
[15347.732132] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[15347.732188] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[15347.732208] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xdfebc004)
[15347.732215] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[15347.732222] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[15347.732257] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[15347.732270] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x20312021)
[15347.732276] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0x20102000)
[15347.732282] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0x2020)
[15347.732288] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
[15347.732297] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[15347.732304] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[15347.732357] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[15347.732371] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x20512041)
[15347.732377] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xdfd0dfd0)
[15347.732383] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0x3030)
[15347.732388] pcieport 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0xc0c00)
[15347.732397] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[15347.732405] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[15347.732457] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x20400)
[15347.732470] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xd011d001)
[15347.732476] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xdfc0dfa0)
[15347.732482] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0xd0d0)
[15347.732487] pcieport 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0xe0d00)
[15347.732496] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[15347.732504] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[15347.732565] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[15347.732580] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[15347.732594] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0xbf61)
[15347.732609] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[15347.732623] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x307)
[15347.732638] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0xbf41)
[15347.732652] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[15347.732666] uhci_hcd 0000:00:1d.3: restoring config space at offset 0xf (was 0x400, writing 0x405)
[15347.732681] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x8 (was 0x1, writing 0xbf21)
[15347.732696] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[15347.732740] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[15347.732775] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x100f1, writing 0x1fff1)
[15347.732781] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x90, writing 0xdf90df90)
[15347.732787] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
[15347.732801] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100107)
[15347.732853] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[15347.732879] ata_piix 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x204)
[15347.732918] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x204)
[15347.732950] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800101)
[15347.733028] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[15347.733096] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfdff000)
[15347.733109] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[15347.733129] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[15347.733254] b44 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[15347.733275] b44 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fe000)
[15347.733281] b44 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[15347.733289] b44 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[15347.733314] ohci1394 0000:02:01.0: restoring config space at offset 0xf (was 0x4020100, writing 0x4020103)
[15347.733336] ohci1394 0000:02:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fd800)
[15347.733342] ohci1394 0000:02:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
[15347.733351] ohci1394 0000:02:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[15347.733376] sdhci-pci 0000:02:01.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[15347.733398] sdhci-pci 0000:02:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fd500)
[15347.733404] sdhci-pci 0000:02:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
[15347.733412] sdhci-pci 0000:02:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[15347.733438] pci 0000:02:01.2: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[15347.733460] pci 0000:02:01.2: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fd600)
[15347.733469] pci 0000:02:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100102)
[15347.733493] pci 0000:02:01.3: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[15347.733516] pci 0000:02:01.3: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fd700)
[15347.733526] pci 0000:02:01.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100102)
[15347.733903] PM: early resume of devices complete after 1.923 msecs
[15347.767755] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[15347.767761] i915 0000:00:02.0: setting latency timer to 64
[15347.864269] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[15347.864282] HDA Intel 0000:00:1b.0: setting latency timer to 64
[15347.864333] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[15347.864344] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[15347.864379] usb usb2: root hub lost power or was reset
[15347.864410] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[15347.864421] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[15347.864452] usb usb3: root hub lost power or was reset
[15347.864487] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[15347.864494] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[15347.864519] usb usb4: root hub lost power or was reset
[15347.864542] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[15347.864548] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[15347.864574] usb usb5: root hub lost power or was reset
[15347.864597] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[15347.864603] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[15347.864619] pci 0000:00:1e.0: setting latency timer to 64
[15347.864634] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[15347.864639] ata_piix 0000:00:1f.2: setting latency timer to 64
[15347.864675] ata1.00: _GTF evaluation failed (AE 0x1001)
[15347.864698] ata2.00: _GTF evaluation failed (AE 0x1001)
[15347.864755] b44 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[15347.942116] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[df9fd800-df9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[15347.948190] sdhci-pci 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[15347.976865] sd 0:0:0:0: [sda] Starting disk
[15348.932478] ata2.00: configured for UDMA/33
[15349.516500] ata1.00: configured for UDMA/100
[15349.528802] PM: resume of drv:sd dev:0:0:0:0 complete after 1551.934 msecs
[15349.548825] PM: resume of devices complete after 1808.741 msecs
[15349.548955] PM: resume devices took 1.816 seconds
[15349.548989] PM: Finishing wakeup.
[15349.548990] Restarting tasks ... done.
[15350.013070] Registered led device: iwl-phy0::radio
[15350.013874] Registered led device: iwl-phy0::assoc
[15350.014451] Registered led device: iwl-phy0::RX
[15350.015020] Registered led device: iwl-phy0::TX
[15350.018274] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15350.026611] ADDRCONF(NETDEV_UP): eth0: link is not ready
[15351.876882] wlan0: deauthenticating from 00:90:4c:5f:00:2a by local choice (reason=3)
[15351.910485] wlan0: direct probe to AP 00:90:4c:5f:00:2a (try 1)
[15351.912546] wlan0: direct probe responded
[15351.912558] wlan0: authenticate with AP 00:90:4c:5f:00:2a (try 1)
[15351.914431] wlan0: authenticated
[15351.914469] wlan0: associate with AP 00:90:4c:5f:00:2a (try 1)
[15351.916766] wlan0: RX AssocResp from 00:90:4c:5f:00:2a (capab=0x401 status=0 aid=4)
[15351.916775] wlan0: associated
[15351.918374] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15353.000269] b44: eth0: Link is up at 100 Mbps, full duplex.
[15353.000275] b44: eth0: Flow control is off for TX and off for RX.
[15353.000436] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[15362.284026] wlan0: no IPv6 routers present
[15363.004035] eth0: no IPv6 routers present
[15397.485546] wlan0: deauthenticating from 00:90:4c:5f:00:2a by local choice (reason=3)
[15643.272002] b44: eth0: powering down PHY
[15643.627409] PM: Syncing filesystems ... done.
[15643.627965] PM: Preparing system for mem sleep
[15643.627969] Freezing user space processes ... (elapsed 0.00 seconds) done.
[15643.629506] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[15643.629554] PM: Entering mem sleep
[15643.629570] Suspending console(s) (use no_console_suspend to debug)
[15643.629982] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[15643.826626] sd 0:0:0:0: [sda] Stopping disk
[15644.790062] PM: suspend of drv:sd dev:0:0:0:0 complete after 1160.075 msecs
[15645.192463] PM: suspend of drv:psmouse dev:serio1 complete after 402.313 msecs
[15645.294020] ACPI handle has no context!
[15645.294029] sdhci-pci 0000:02:01.1: PCI INT B disabled
[15645.294035] ACPI handle has no context!
[15645.328162] b44 0000:02:00.0: PCI INT A disabled
[15645.328173] ACPI handle has no context!
[15645.360310] ata_piix 0000:00:1f.2: PCI INT B disabled
[15645.376114] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[15645.376130] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[15645.376145] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[15645.376159] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[15645.376174] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[15645.376206] HDA Intel 0000:00:1b.0: PCI INT A disabled
[15645.416083] i915 0000:00:02.0: PCI INT A disabled
[15645.432370] PM: suspend of devices complete after 1802.600 msecs
[15645.432377] PM: suspend devices took 1.804 seconds
[15645.448439] PM: late suspend of devices complete after 16.055 msecs
[15645.452283] ACPI: Preparing to enter system sleep state S3
[15645.452764] Disabling non-boot CPUs ...
[15645.452785] Back to C!
[15645.452785] CPU0: Thermal monitoring enabled (TM2)
[15645.452785] Force enabled HPET at resume
[15645.452785] ACPI: Waking up from system sleep state S3
[15645.457336] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[15645.457392] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[15645.457412] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xdfebc004)
[15645.457418] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[15645.457426] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[15645.457461] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[15645.457475] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x20312021)
[15645.457481] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0x20102000)
[15645.457486] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0x2020)
[15645.457492] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
[15645.457501] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[15645.457509] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[15645.457561] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[15645.457575] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x20512041)
[15645.457581] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xdfd0dfd0)
[15645.457587] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0x3030)
[15645.457592] pcieport 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0xc0c00)
[15645.457601] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[15645.457609] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[15645.457660] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x20400)
[15645.457673] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xd011d001)
[15645.457679] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xdfc0dfa0)
[15645.457685] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0xd0d0)
[15645.457691] pcieport 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0xe0d00)
[15645.457700] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[15645.457707] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[15645.457768] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[15645.457783] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[15645.457798] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0xbf61)
[15645.457812] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[15645.457826] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x307)
[15645.457841] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0xbf41)
[15645.457855] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[15645.457869] uhci_hcd 0000:00:1d.3: restoring config space at offset 0xf (was 0x400, writing 0x405)
[15645.457884] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x8 (was 0x1, writing 0xbf21)
[15645.457899] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[15645.457943] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[15645.457978] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x100f1, writing 0x1fff1)
[15645.457985] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x90, writing 0xdf90df90)
[15645.457991] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
[15645.458004] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100107)
[15645.458056] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[15645.458083] ata_piix 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x204)
[15645.458122] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x204)
[15645.458154] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800101)
[15645.458232] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[15645.458300] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfdff000)
[15645.458314] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[15645.458333] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[15645.458459] b44 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[15645.458480] b44 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fe000)
[15645.458486] b44 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[15645.458493] b44 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[15645.458518] ohci1394 0000:02:01.0: restoring config space at offset 0xf (was 0x4020100, writing 0x4020103)
[15645.458541] ohci1394 0000:02:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fd800)
[15645.458547] ohci1394 0000:02:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
[15645.458554] ohci1394 0000:02:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[15645.458579] sdhci-pci 0000:02:01.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[15645.458603] sdhci-pci 0000:02:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fd500)
[15645.458609] sdhci-pci 0000:02:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
[15645.458617] sdhci-pci 0000:02:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[15645.458643] pci 0000:02:01.2: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[15645.458666] pci 0000:02:01.2: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fd600)
[15645.458676] pci 0000:02:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100102)
[15645.458700] pci 0000:02:01.3: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[15645.458723] pci 0000:02:01.3: restoring config space at offset 0x4 (was 0x0, writing 0xdf9fd700)
[15645.458732] pci 0000:02:01.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100102)
[15645.459116] PM: early resume of devices complete after 1.915 msecs
[15645.493130] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[15645.493136] i915 0000:00:02.0: setting latency timer to 64
[15645.588257] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[15645.588270] HDA Intel 0000:00:1b.0: setting latency timer to 64
[15645.588322] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[15645.588333] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[15645.588368] usb usb2: root hub lost power or was reset
[15645.588400] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[15645.588411] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[15645.588442] usb usb3: root hub lost power or was reset
[15645.588475] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[15645.588482] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[15645.588508] usb usb4: root hub lost power or was reset
[15645.588530] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[15645.588537] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[15645.588563] usb usb5: root hub lost power or was reset
[15645.588584] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[15645.588591] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[15645.588607] pci 0000:00:1e.0: setting latency timer to 64
[15645.588622] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[15645.588627] ata_piix 0000:00:1f.2: setting latency timer to 64
[15645.588662] ata1.00: _GTF evaluation failed (AE 0x1001)
[15645.588685] ata2.00: _GTF evaluation failed (AE 0x1001)
[15645.588743] b44 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[15645.666108] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[df9fd800-df9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[15645.672179] sdhci-pci 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[15645.700910] sd 0:0:0:0: [sda] Starting disk
[15646.680491] ata2.00: configured for UDMA/33
[15647.280499] ata1.00: configured for UDMA/100
[15647.300191] PM: resume of drv:sd dev:0:0:0:0 complete after 1599.277 msecs
[15647.320826] PM: resume of devices complete after 1856.800 msecs
[15647.320955] PM: resume devices took 1.864 seconds
[15647.320988] PM: Finishing wakeup.
[15647.320990] Restarting tasks ... done.
[15647.776444] Registered led device: iwl-phy0::radio
[15647.777527] Registered led device: iwl-phy0::assoc
[15647.778495] Registered led device: iwl-phy0::RX
[15647.779664] Registered led device: iwl-phy0::TX
[15647.781008] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15647.801946] ADDRCONF(NETDEV_UP): eth0: link is not ready
[15649.492419] wlan0: deauthenticating from 00:90:4c:5f:00:2a by local choice (reason=3)
[15649.526071] wlan0: direct probe to AP 00:90:4c:5f:00:2a (try 1)
[15649.528468] wlan0: direct probe responded
[15649.528478] wlan0: authenticate with AP 00:90:4c:5f:00:2a (try 1)
[15649.530371] wlan0: authenticated
[15649.530404] wlan0: associate with AP 00:90:4c:5f:00:2a (try 1)
[15649.532743] wlan0: RX AssocResp from 00:90:4c:5f:00:2a (capab=0x401 status=0 aid=3)
[15649.532750] wlan0: associated
[15649.534244] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15651.000270] b44: eth0: Link is up at 100 Mbps, full duplex.
[15651.000277] b44: eth0: Flow control is off for TX and off for RX.
[15651.000482] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[15659.692041] wlan0: no IPv6 routers present
[15661.536139] eth0: no IPv6 routers present
[15695.394691] wlan0: deauthenticating from 00:90:4c:5f:00:2a by local choice (reason=3)


It looks like there's some interesting information in there.... what can I do with it, ragazzi?

---

### Post by thetorybear on 2010-10-28
The ** dmesg** output is still mostly indecipherable to me, Ubuntu youngling that I am, but one area that interested me was this:
> 
[15350.018274] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15350.026611] ADDRCONF(NETDEV_UP): eth0: link is not ready
[15351.876882] wlan0: deauthenticating from 00:90:4c:5f:00:2a by local choice (reason=3)
[15351.910485] wlan0: direct probe to AP 00:90:4c:5f:00:2a (try 1)
[15351.912546] wlan0: direct probe responded
[15351.912558] wlan0: authenticate with AP 00:90:4c:5f:00:2a (try 1)
[15351.914431] wlan0: authenticated
[15351.914469] wlan0: associate with AP 00:90:4c:5f:00:2a (try 1)
[15351.916766] wlan0: RX AssocResp from 00:90:4c:5f:00:2a (capab=0x401 status=0 aid=4)
[15351.916775] wlan0: associated
[15351.918374] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15353.000269] b44: eth0: Link is up at 100 Mbps, full duplex.
[15353.000275] b44: eth0: Flow control is off for TX and off for RX.
[15353.000436] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[15362.284026] wlan0: no IPv6 routers present
[15363.004035] eth0: no IPv6 routers present
[15397.485546] wlan0: deauthenticating from 00:90:4c:5f:00:2a by local choice (reason=3)

It would appear that my wireless is associating and then for some reason "deauthenticates." 
Why on earth would it be doing that? Reason 3 means nothing to me, I gotta say. 

But this gives me hope. It's at least SEEING the access point.

---

### Post by maclenin on 2010-10-29
Molto bene!

Take a peek at my thread ([click here]("http://ubuntuforums.org/showthread.php?t=1579095")) - it looks like we migt be suffering similarly - perhaps some of the ideas shared there will help you through your difficulties....

I, too, soldier on....

maclenin

---

### Post by thetorybear on 2010-10-29
Ah maclenin, I do appreciate you.

After browsing your thread and thinking more about the genesis of my wireless problems, I am tempted to also try the kernel install. But if you're planning on trying it soon, maybe I'll let you trial run it. 

Either way, it is comforting to know that other people are having similar issues. I still think that it's totally bizarre for the wireless to just stop connecting before an upgrade. Sometimes all you can say is "bift," I suppose. 

Such fun times these are. I'm still totally considering buying that 100 ft ethernet cable.

---

### Post by thetorybear on 2010-10-29
Today I tried a delightful little thing called Linux Mint, the Debian version. 
I really dig the way it looks and runs... except for the fact booting it live from the install CD didn't restore my wireless. 

Same problem: can see the networks, but can't connect. 

Maybe if I start ritually sacrificing things that I've carved/burned the Ubuntu symbol into...

---

### Post by thetorybear on 2010-11-01
So, the older brother just handed me a USB wireless adapter and it is running just fine. 

This makes no sense to me. Why would a failed wireless card still be finding the networks? I do not understand. I suppose this works as a fix though. 

Many thanks to everyone who gave me feedback.

---

### Post by GreyGeek on 2010-11-05
I've been running Kubuntu 10.4 and wicd since 10.4 was in beta.  My Intel Wifi Link 5100 performed faultlessly.  About a month ago I noticed an intermittent hang while browsing.  After a few seconds or so, perhaps as long as 30, FF would resume browsing.  All other browsers showed the same symptoms.  I opened a console and pinged google.com after a FF hang.  Sometimes it would immediately return, and FF would resume, and sometimes it wouldn't.  After the kernel upgrade to 2.6.32-25-generic #45-Ubuntu SMP  UTC 2010 x86_64 GNU/Linux  FF would hang within a couple minutes of first use.  Testing with ping on a fresh wicd connection I found the pings would stop after the 46th return. The logs shows either a reason=2 or reason=3.  Wicd still shows a connection.  Ifconfig shows wlan0 is still assigned an IP address. Ifwconfig shows valid connection info.  The router table isn't changed.  Only ping shows that there is no connection. 

Googling the web, this problem appears to be a regression.  It has been and is being experienced by all distros and network managers, regardless of the kernel being used.   Disabling IPv6 doesn't solve this problem for everyone,  but it can significantly increase your connection speed.
[http://linuxpoison.blogspot.com/2010/10/how-to-disable-ipv6-in-ubuntu-linux.html](http://linuxpoison.blogspot.com/2010/10/how-to-disable-ipv6-in-ubuntu-linux.html)  
Hopefully, by the time IPv6 becomes the web's default protocol it will be working better.

**Here is the workaround that works for me, so far. ** After I turn on the modem and wireless router I let them stabilize, then I boot my notebook, which automatically makes a wireless connection to my access point.   When FF locks up I open wicd and disconnect my access point.  Leaving wicd's manager displaying, I power cycle my modem and wireless router.  When they are stabilized I click the connection button for my access point and it makes a connection.  I close wicd's manager.  My connection stays up the rest of the day.

---

