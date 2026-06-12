---
title: "Blased Netgear WG511T &amp; IPv6 error - No wireless connection"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by robodude666 on 2006-06-20
***** NOTE: The title should be "Blasted Netgear WG511T & IPv6 error - No wireless connection" I made a typo and it won't let me fix it. *****

Hello,

For the past 9 or so hours I have been trying to get my WG511T card to work. Almost got it to work, but then I got an error. When I run dmesg I get an error that says:
ath0: No IPv6 router found.

That is when I disconnect my ethernet cable. Whenever I have the cable plugged in and the computer is set to ath0 (wireless connection) it works, but if i take out the cable wireless doesnt work anymore. Sort of kills the whole "wireless internet" thing :P

So lets start from the beginning. I tried to install madwifi about 5 times... Tried like 3 or 4 different tutorials and then I gave up on madwifi. The best I got with madwifi was that a wireless network option was added to my networking panel. I configed it and the computer would not connect to the wireless internet. I found ndiswrapper and I installed that, on first attempt it worked! I got the driver files from the cd and used them. everything worked fine. I reconfigged the internet and poof! It connected to wireless. Internet with just the card didn't work. I tried DHCP which didn't work and I tried static ip. I left it as static ip since thats how it worked before on windows. Now, as I said before I get the "No IPv6 router found." error in dmesg.

I searched around ubuntuforums and around on google and I found some topics at ubuntu forums on how to disable ipv6. I tried the first method (comment the line and add 3 other ones) which didnt work. When I ran

ip a | grep inet6

I get ipv6 entries, so i tried the second method (blacklisting ipv6) and it sort of worked. When i ran

ip a | grep inet6

It came up with nothing. Now when I disconnect my ethernet cable and just have my wireless card on I dont get that

ath0: No IPv6 router found.

error... I don't get anything actually. Only thing I get is a not working wireless internet.

Any suggestions? Help?

Since this is a laptop, it would be nice to have wireless internet so I wont be on a cable all the time.. After all, thats the point of a laptop :P

Thanks,
-robodude666

---

### Post by robodude666 on 2006-06-20
Sorry for the bump, thought I could add in some more info to help you all out.

When I run ifconfig I get this:
```

ath0      Link encap:Ethernet  HWaddr 00:14:6C:1A:9F:CA
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:08:02:63:C9:3E
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:605150 (590.9 KiB)  TX bytes:47365 (46.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7120 (6.9 KiB)  TX bytes:7120 (6.9 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-1A-9F-CA-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24780 errors:0 dropped:0 overruns:0 frame:53412
          TX packets:20478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:3316835 (3.1 MiB)  TX bytes:1029461 (1005.3 KiB)
          Interrupt:11 Memory:d0ba0000-d0bb0000

```

When I run iwconfig I get this:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Vileng12"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:7673-3531-7436-3030-7272   Security mode:restricted
          Power Management:off
          Link Quality=42/94  Signal level=-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:323  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

lo is the modem connection ubuntu comes with. eth0 is my ethernet (wired) connection, ath0 is the wireless connection I setup w/ ndiswrapper and wifi0 no idea what that is. When I go to connection properties (doubleclick on the network connection icon in the top corner) it says that the ath0 connection is idle and no packets are being sent.

If I go to System -> Administration -> Networking Tools and I scroll through all my connections, ath0 has all the correct ip info and stuff, but there are no packets moving. HOWEVER, when I go to wifi0 I can see the numbers changing. But for wifi0 there is no IP info or interface info. Also, when I click on configure next to wifi0, it gives me an error that this interface does not exist. (Yet it is active? what the?)

Here are the last like 20 or so entries I get from dmesg:

```

[42949646.680000] pccard: card ejected from slot 0
[42949647.530000] wifi0: ath_chan_set: unable to reset channel 7 (2442Mhz) flags 0xc0 '' (HAL status 9999993)
[42949648.370000] wifi0: ath_chan_set: unable to reset channel 6 (2437Mhz) flags 0xc0 '' (HAL status 3501695649)
[42949649.350000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[42949654.520000] pccard: CardBus card inserted into slot 0
[42949654.520000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[42949654.520000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [C0B9] -> GSI 11 (level, low) -> IRQ 11
[42949655.090000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[42949655.090000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[42949655.090000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[42949655.090000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[42949655.090000] wifi0: mac 7.9 phy 4.5 radio 5.6
[42949655.090000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[42949655.090000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[42949655.090000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[42949655.090000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[42949655.090000] wifi0: Use hw queue 8 for CAB traffic
[42949655.090000] wifi0: Use hw queue 9 for beacons
[42949655.090000] wifi0: Atheros 5212: mem=0x24000000, irq=11
[42950891.580000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[42951099.580000] e100: eth0: e100_watchdog: link down
[42951247.580000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex

```

The last 3 about eth0 is when I unplugged/plugged in the cable to see if wireless worked. The firstone is when I took out the card. I think that it is trying to use wifi0 for the wireless connection even though it does not exist.

I think wifi0 was created from my failed attempts at madwifi. Could it have something to do with this command not working?

wlanconfig ath0 create wlandev wifi0 wlanmode sta

Whenever I try to run that I get

wlanconfig: ioctl: Input/output error


Is there a way I can remove everything from madwifi and just have ndiswrapper as it seems to work better? And, um, without reinstalling ubuntu. I spent 36 hours installing it so that I would have a working GUI...

---

