---
title: "Reset all network settings?"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by Gelupah on 2011-03-06
Hi all,

I've been having major problems with my wifi connection, the internet getting worse and worse, slower, bad connections, VPN dropping out all of the time etc (more info here: [http://ubuntuforums.org/showthread.php?t=1692353](http://ubuntuforums.org/showthread.php?t=1692353))

Anyway, the wifi connection works impeccably under windows, and is worsening under Ubuntu. Ideally I do not want to have to format my linux drive and reinstall Ubuntu, thereby losing all of my settings, packages installed, etc. Is there a way of resetting all of the network settings to standard, as if a fresh copy of ubuntu had just been installed? Maybe removing the packages? Removing config folders? No idea how to go about that so I'd rather ask an opinion before breaking everything!

Thanks

---

### Post by chili555 on 2011-03-06
Why don't we troubleshoot the wireless driver first before we try to reset everything. Open a terminal and run and post:```
lspci -nn
sudo lshw -C network
```If your wireless device is USB, post:```
lsusb
```If you know you have made some changes specifically related to your wireless card and driver, please tell us about it.

---

### Post by Gelupah on 2011-03-06
Thanks for helping out, much appreciated.

'lspci -nn' output (I assume you are mainly interested in the WAN chipset but here goes the whole lot):
> 00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) [1022:9609]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Juniper [Radeon HD 5700 Series] [1002:68b8]
01:00.1 Audio device [0403]: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series] [1002:aa58]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
03:06.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
03:0e.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]


And 'sudo lshw -C network' gives us the following:

>   *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:db:0c:9d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.137.1 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdbe0000-fdbeffff memory:fdb00000-fdb0ffff
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 01
       serial: 00:19:5b:35:d0:a8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-27-generic firmware=N/A ip=192.168.1.13 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:fdde0000-fddeffff


The drivers remain unchanged. I've installed Samba to share my internet connection with another PC, with my Ethernet having a fixed IP address (I edited a config file for this to happen at each boot), but the wireless remains untouched. It's set to DHCP, wifi security is WPA (or possibly WPA2, would have to check). One more thing, I'm running 10.10  32bits, just to avoid any (additional) unnecessary problems :)

I'm starting to think my VPN had nothing to do with the problem in the first place, the internet just stops working after random amounts of time (as far as I can tell), and I have to manually disconnect and reconnect each time for it to work again!

Thanks again...

---

### Post by chili555 on 2011-03-06
I wonder why you have both a wired ethernet and a wireless connection. If you detach the wire does the wireless perform as expected?

---

### Post by inkrypted on 2011-03-06
I often have problems with wireless connections in Linux and have found that using an alternative network manager has solved alot of problems. WICD has been a huge help for me.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
PPA Repository: ppa:dpaleino/wicd

---

### Post by Gelupah on 2011-03-06
> **chili555 said:**
> I wonder why you have both a wired ethernet and a wireless connection. If you detach the wire does the wireless perform as expected?

I connect to the house internet through WiFi, and the onboard Ethernet card is just used on very rare occasions, when I wish to share the internet connection with a device that has no WiFi. I can possibly try disabling Eth0, if you think that might help though?

---

### Post by Gelupah on 2011-03-06
> **inkrypted said:**
> I often have problems with wireless connections in Linux and have found that using an alternative network manager has solved alot of problems. WICD has been a huge help for me.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
PPA Repository: ppa:dpaleino/wicd

Thanks, I'll give that a try.

---

### Post by chili555 on 2011-03-06
> I can possibly try disabling Eth0, if you think that might help though?All you have to do is detach the cable. I think Network Manager stumbles trying to juggle two interfaces and I think that may be the cause of your problem.

I wouldn't abandon Network Manager in favor of Wicd until we sort this out. I have Wicd on one computer and NM on another; both work equally well for me.

---

### Post by Gelupah on 2011-03-06
> **chili555 said:**
> All you have to do is detach the cable. I think Network Manager stumbles trying to juggle two interfaces and I think that may be the cause of your problem.

I wouldn't abandon Network Manager in favor of Wicd until we sort this out. I have Wicd on one computer and NM on another; both work equally well for me.

I gave that a go, but to no avail unfortunately. Same problem with the RJ45 physically pulled out. FYI my /etc/network/interfaces is the following:

> auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.137.1
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by Gelupah on 2011-03-06
Well, before reading your suggestion on **not** installing wicd yet, I gave it a go, and it's no better now. I have both the network manager installed and wicd running, the only difference is that wicd keeps telling me I am disconnected and establishing a connection every few minutes...!

---

### Post by chili555 on 2011-03-06
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.[COLOR="Red"]137[/COLOR].1
netmask 255.255.255.0
gateway 192.168.[COLOR="Red"]1[/COLOR].1 
```Are you sure the listing shouldn't be:```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.[COLOR="Red"]1.137[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.1 
```I'd love to see:```
route -n
```

Would you mind rebooting with the ethernet *detached* after you make these changes? How does the wireless work?

---

### Post by chili555 on 2011-03-06
Do you really think two conflicting network GUIs and two conflicting network connections are really the way to do it? Good luck.

---

### Post by Gelupah on 2011-03-06
> **chili555 said:**
> Do you really think two conflicting network GUIs and two conflicting network connections are really the way to do it? Good luck.

Nope... Lesson learned, wicd removed! I'll give your instructions a go now.

---

### Post by Gelupah on 2011-03-06
> **chili555 said:**
> ```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.[COLOR="Red"]137[/COLOR].1
netmask 255.255.255.0
gateway 192.168.[COLOR="Red"]1[/COLOR].1 
```Are you sure the listing shouldn't be:```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.[COLOR="Red"]1.137[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.1 
```I'd love to see:```
route -n
```

Would you mind rebooting with the ethernet *detached* after you make these changes? How does the wireless work?

The IP is currently set to 192.168.137.1 because this what windows seven configures it to be when use ICS, so I set it this way out of consistency for the other device, to be independent from the OS I am using. I set the gateway to 192.168.1.1 since this is the wireless router.

'route -n' gives the following:
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1.5.128.1       0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
213.232.200.171 192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
178.239.51.82   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
178.239.51.82   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.137.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
1.2.116.0       0.0.0.0         255.255.252.0   U     0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
1.0.0.0         1.2.116.1       255.0.0.0       UG    0      0        0 tun0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0


I can try to change the IP as you suggested and reboot... Fingers crossed!

---

### Post by Gelupah on 2011-03-06
No luck...

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
1.2.116.0       0.0.0.0         255.255.252.0   U     0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
1.0.0.0         1.2.116.1       255.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

---

### Post by chili555 on 2011-03-06
> The IP is currently set to 192.168.137.1 because this what windows seven configures it to be when use ICS, so I set it this way out of consistency for the other device, to be independent from the OS I am using. I set the gateway to 192.168.1.1 since this is the wireless router.
So the ethernet cable attaches to another computer in ICS? And the wireless signal comes directly from the router? I can see that if we could get the wireless going reliably, it would solve many issues.

No luck ... meaning what? That the wireless is still slow and unreliable?

---

### Post by Gelupah on 2011-03-06
> **chili555 said:**
> So the ethernet cable attaches to another computer in ICS? And the wireless signal comes directly from the router? I can see that if we could get the wireless going reliably, it would solve many issues.

The WiFi router is very reliable, used on a laptop across the house, another PC and even on my phone! Basically the other PC just connects through RJ45 because it has no WiFi card/dongle. But under the other OS, the WiFi works impeccably, fast and reliable, I don't think it's a WiFi issue, not would it be a hardware issue, probably more likely a setting or possibly a driver problem?

TBH I don't care about ICS relative to this problem, I just want to get the WiFi working reliably on my main PC now...

---

### Post by Gelupah on 2011-03-06
> **chili555 said:**
> So the ethernet cable attaches to another computer in ICS? And the wireless signal comes directly from the router? I can see that if we could get the wireless going reliably, it would solve many issues.

No luck ... meaning what? That the wireless is still slow and unreliable?

Ah, yes, "no luck" solving the problem: basically the internet works for a few minutes, then I have to manually disconnect and reconnect it to the router for it to work again. I have to do that very often, every few minutes, but always at different times intervals; it can be a few seconds, it can be a few minutes...

It seems to act as though it is disconnected but the icon does not indicate it has, and I have to manually disconnect and reconnect... Quite odd, really.

---

### Post by chili555 on 2011-03-06
Wow! I'm even more confused. Let's leave ethernet and ICS for another day. My head's gonna explode. I think I see some flaws there.

Please try:```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up
```Is the performance better? This is a temporary change; if it works, we'll need to write one file to make it effective on boot.

One other thing you might try is to install linux-backports-modules-compat-wireless-2.6.37-maverick-generic in System > Administration > Synaptic. It contains a newer ath5k driver.

---

### Post by Gelupah on 2011-03-07
> **chili555 said:**
> Wow! I'm even more confused. Let's leave ethernet and ICS for another day. My head's gonna explode. I think I see some flaws there.

Please try:```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up
```Is the performance better? This is a temporary change; if it works, we'll need to write one file to make it effective on boot.

One other thing you might try is to install linux-backports-modules-compat-wireless-2.6.37-maverick-generic in System > Administration > Synaptic. It contains a newer ath5k driver.

Hi,

I've tried your code, but that hasn't helped. I then installed the linux-backports-modules-compat-wireless-2.6.37-maverick-generic package, rebooted, and sadly still seem to have the same problem. I need to manually disconnect and reconnect the WiFi all of the time, whilst the eth0 remains unplugged and untouched.

Not sure what to check next, maybe I can try temporarily connecting to the internet through the RJ45 to see where the problem might come from, wlan0 specifically or something on a grander scale?

Thanks again for the advice and patience, this one is a tough one!

---

### Post by chili555 on 2011-03-07
What does this tell us?```
sudo iwlist wlan0 scan
```

---

### Post by Gelupah on 2011-03-07
Here goes:

```
wlan0     Scan completed :
          Cell 01 - Address: AE:F0:C1:XX:XX:XX
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"eeenh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000133495b00e8
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00056565656E68
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: AE:F0:C1:XX:XX:XX
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013349553bdc
                    Extra: Last beacon: 464ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 03 - Address: AE:F0:C1:XX:XX:XX
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001334956d05b
                    Extra: Last beacon: 360ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: AE:F0:C1:XX:XX:XX
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001334956d507
                    Extra: Last beacon: 360ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

```

---

### Post by inkrypted on 2011-03-07
Does this seem to happen after the laptop sleeps or hibernates? Or is just a progressive slow down over a few minutes?

---

### Post by chili555 on 2011-03-07
I can't see anything to change or fix about your settings. I'm out of suggestions. I'm sorry I couldn't be more help.

---

### Post by Gelupah on 2011-03-08
> **chili555 said:**
> I can't see anything to change or fix about your settings. I'm out of suggestions. I'm sorry I couldn't be more help.

It's OK, thanks for trying... If you know a way of fully resetting all of the network settings that would be amazing, I just don't want to go through the hassle of reconfiguring and resintalling everything again...

---

### Post by Gelupah on 2011-03-08
> **inkrypted said:**
> Does this seem to happen after the laptop sleeps or hibernates? Or is just a progressive slow down over a few minutes?

Hi, it's a desktop computer, sleeping/hibernating is disabled. It happens within minutes, if that, of starting.

---

### Post by chili555 on 2011-03-08
> fully resetting all of the network settings that would be amazingI suggest the following. Look in System > Administration > Synaptic and see what versions of Network Manager and its cousins, network-manager-gnome, for example are installed. Download the same versions to your desktop here: [http://packages.ubuntu.com/maverick/network-manager](http://packages.ubuntu.com/maverick/network-manager)

Keep them available for the repair after we remove and purge the current versions.```
sudo apt-get remove --purge network-manag*
```Next, reinstall Network Manager from the packages on your desktop:```
cd Desktop
sudo dpkg -i networ*
```The wildcard * will include all packages with networ in the name. Best of all, new configuration files will be written.

Leave the packages on your desktop for now. They may be helpful if we need to try again.

Next, amend the /etc/network/interfaces file to not automatically start the ethernet; we can revert at any time if needed:```
auto lo
iface lo inet loopback

**[COLOR="Red"]#[/COLOR]**auto eth0
iface eth0 inet static
address 192.168.137.1
netmask 255.255.255.0
gateway 192.168.1.1
```Detach the ethernet cable and reboot. Before you fill in any configurations manually, simply click the Network Manager icon. Do you see your network? Can you connect?

If it slows down or drops, you might look in:```
sudo tail -n50 /var/log/syslog
```See if there are clues as to why it's misbehaving.

---

### Post by Gelupah on 2011-03-08
> **chili555 said:**
> I suggest the following. Look in System > Administration > Synaptic and see what versions of Network Manager and its cousins, network-manager-gnome, for example are installed. Download the same versions to your desktop here: [http://packages.ubuntu.com/maverick/network-manager](http://packages.ubuntu.com/maverick/network-manager)

Keep them available for the repair after we remove and purge the current versions.```
sudo apt-get remove --purge network-manag*
```Next, reinstall Network Manager from the packages on your desktop:```
cd Desktop
sudo dpkg -i networ*
```The wildcard * will include all packages with networ in the name. Best of all, new configuration files will be written.

Leave the packages on your desktop for now. They may be helpful if we need to try again.

Next, amend the /etc/network/interfaces file to not automatically start the ethernet; we can revert at any time if needed:```
auto lo
iface lo inet loopback

**[COLOR="Red"]#[/COLOR]**auto eth0
iface eth0 inet static
address 192.168.137.1
netmask 255.255.255.0
gateway 192.168.1.1
```Detach the ethernet cable and reboot. Before you fill in any configurations manually, simply click the Network Manager icon. Do you see your network? Can you connect?

If it slows down or drops, you might look in:```
sudo tail -n50 /var/log/syslog
```See if there are clues as to why it's misbehaving.

OK Thanks; so I did a full remove as instructed, and even went to the extent of deleting the /etc/network and /etc/NetworkManager folders just to be sure to remove settings. After reinstalling the packages, and creating a new interfaces file, and rebooting, Ubuntu automatically reconnected to the WiFi, remembering the WPA code apparently. So I tried the internet and similar problem, I had to manually reconnect it for it to work. I'm on it now though, and so far it seems sharper and more stable (fingers crossed). In the last ten minutes I haven't had to manually reconnect, which is already short of a miracle really... Here's the output if you are interested:

```
Mar  8 22:52:56 BBF kernel: [   53.833393] wlan0: associate with 86:f7:3b:xx:xx:xx (try 1)
Mar  8 22:52:56 BBF kernel: [   53.835660] wlan0: RX AssocResp from 86:f7:3b:xx:xx:xx (capab=0x11 status=0 aid=1)
Mar  8 22:52:56 BBF kernel: [   53.835668] wlan0: associated
Mar  8 22:52:56 BBF wpa_supplicant[1067]: Associated with 86:f7:3b:xx:xx:xx
Mar  8 22:52:56 BBF NetworkManager[1042]: <info> (wlan0): supplicant connection state:  associating -> associated
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar  8 22:52:57 BBF wpa_supplicant[1067]: WPA: Key negotiation completed with 86:f7:3b:xx:xx:xx [PTK=CCMP GTK=TKIP]
Mar  8 22:52:57 BBF wpa_supplicant[1067]: CTRL-EVENT-CONNECTED - Connection to 86:f7:3b:xx:xx:xx completed (reauth) [id=0 id_str=]
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'eeenh'.
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> dhclient started with pid 1847
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar  8 22:52:57 BBF dhclient: Internet Systems Consortium DHCP Client V3.1.3
Mar  8 22:52:57 BBF dhclient: Copyright 2004-2009 Internet Systems Consortium.
Mar  8 22:52:57 BBF dhclient: All rights reserved.
Mar  8 22:52:57 BBF dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar  8 22:52:57 BBF dhclient: 
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar  8 22:52:57 BBF dhclient: Listening on LPF/wlan0/00:19:5b:xx:xx:xx
Mar  8 22:52:57 BBF dhclient: Sending on   LPF/wlan0/00:19:5b:xx:xx:xx
Mar  8 22:52:57 BBF dhclient: Sending on   Socket/fallback
Mar  8 22:52:57 BBF dhclient: DHCPREQUEST of 192.168.1.11 on wlan0 to 255.255.255.255 port 67
Mar  8 22:52:57 BBF dhclient: DHCPACK of 192.168.1.11 from 192.168.1.1
Mar  8 22:52:57 BBF dhclient: bound to 192.168.1.11 -- renewal in 412864 seconds.
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Mar  8 22:52:57 BBF NetworkManager[1042]: <info>   address 192.168.1.11
Mar  8 22:52:57 BBF NetworkManager[1042]: <info>   prefix 24 (255.255.255.0)
Mar  8 22:52:57 BBF NetworkManager[1042]: <info>   gateway 192.168.1.1
Mar  8 22:52:57 BBF NetworkManager[1042]: <info>   nameserver '212.27.40.240'
Mar  8 22:52:57 BBF NetworkManager[1042]: <info>   nameserver '212.27.40.241'
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar  8 22:52:57 BBF avahi-daemon[1030]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.11.
Mar  8 22:52:57 BBF avahi-daemon[1030]: New relevant interface wlan0.IPv4 for mDNS.
Mar  8 22:52:57 BBF avahi-daemon[1030]: Registering new address record for 192.168.1.11 on wlan0.IPv4.
Mar  8 22:52:58 BBF NetworkManager[1042]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Mar  8 22:52:58 BBF NetworkManager[1042]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar  8 22:52:58 BBF NetworkManager[1042]: <info> Policy set 'Auto eeenh' (wlan0) as default for IPv4 routing and DNS.
Mar  8 22:52:58 BBF NetworkManager[1042]: <info> Activation (wlan0) successful, device activated.
Mar  8 22:52:58 BBF NetworkManager[1042]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar  8 22:52:58 BBF nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
```

Seems pretty OK really, apart from:

```
Mar  8 22:52:57 BBF NetworkManager[1042]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
```
```
Mar  8 22:52:58 BBF nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
```

Let me do some more testing and try to fix the VPN I broke, but this is promising, definitely progress so far!

---

### Post by Gelupah on 2011-03-08
After a reboot, the same thing seems to occur: initially, the allegedly connected WiFi pings the router fine, but does not get any internet, no matter how long I wait... I have to manually disconnect and reconnect for it to work.

However, once this is done, the internet does seem a lot swifter, and so far more stable... Strange indeed.

---

### Post by chili555 on 2011-03-08
I suspect Unmanaged Device is eth0, your wired ethernet interface. By having it listed in /etc/network/interfaces, you tell NM not to handle eth0; your settings will handle it instead.> nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.I'm not sure what this means. It may have to do with eth0, I'm googling.

EDIT: It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/661951](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/661951) 

Please note:> Would suggest increasing the priority a little, because it seems that if the 01ifupdown script fails, [I]other scripts in the

 /etc/NetworkManager/dispatcher.d/

directory don't get run.[/I] Or perhaps the fault is will NetworkManager - should it error out if one script stops working? New bug?
Also:> This bug was fixed in the package network-manager - 0.8.3+git.20101209t061929.638fb18-0ubuntu1I believe the current Maverick version is 0.8.1+git.

---

### Post by Gelupah on 2011-03-08
Wow, indeed, 0.8.1, it's worth updating I think... Let me see if I can find the package! Funny that update-manager doesn't suggest the update though?

---

### Post by Gelupah on 2011-03-08
OK I tried upgraded to version 0.8.4 (from natty)...

```
sudo dpkg -i network-manager_0.8.4~git.20110228t143901.5cdded6-0ubuntu1_i386.deb 
dpkg: regarding network-manager_0.8.4~git.20110228t143901.5cdded6-0ubuntu1_i386.deb containing network-manager:
 network-manager breaks dhcp3-client (<< 4.1.1-P1-11)
  dhcp3-client (version 3.1.3-2ubuntu6) is present and installed.
dpkg: error processing network-manager_0.8.4~git.20110228t143901.5cdded6-0ubuntu1_i386.deb (--install):
 installing network-manager would break dhcp3-client, and
 deconfiguration is not permitted (--auto-deconfigure might help)
Errors were encountered while processing:
 network-manager_0.8.4~git.20110228t143901.5cdded6-0ubuntu1_i386.deb
```

Do you think I'm wasting my time trying to upgrade the version or is it something worth pursuing to fix my problems?

---

### Post by chili555 on 2011-03-08
> Do you think I'm wasting my time trying to upgrade the version or is it something worth pursuing to fix my problems?It's hard to say if that's a significant problem or not. The bug report seems to indicate it's a problem with VPN. Your problem is getting connected and staying connected to an ordinary internet connection, if I understand your setup correctly.

Wasting time is a relative thing. I have plenty, but you may have an actual job and actual family; time may be more precious to you.

You could rule out NM easily. Remove --purge it and set your details in /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid eeenh
wpa-psk yoursecretkey

#auto eth0
etc., etc.

```Reboot and see if it helps.

Then we can look at the driver, ath5k or wpa_supplicant. wpa_supplicant can be ruled out easily, too.

I see your router is on channel 8. Can you try channel 1 or 12? Is it more stable?

I see nothing else in syslog to dislike and fix.

---

### Post by Gelupah on 2011-03-09
Well the VPN was also a problem, although not sure how much of that is due to the VPN and how is due to the inherent network problems.

So I tried removing the network manager and edited the interfaces file, but could not get any connection, no pinging of my router on 192.168.1.1. I tried switching wlan0 to a static address (in interfaces obviously), with gateway etc, but still couldn't ping the router. Seems that I couldn't get any internet without the network manager installed; am I being silly and misread your indications? So anyway I reinstalled the network manager...

I switched the router onto "auto-channel" mode, apparently it picks the channel with the least interference at each boot. I now have the following:

```
sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: D2:40:E4:XX:XX:XX
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"eeenh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000023cc12b8
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00056565656E68
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: D2:40:E4:XX:XX:XX
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000023c5bfd3
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 03 - Address: D2:40:E4:XX:XX:XX
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000023c5c4e2
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: D2:40:E4:XX:XX:XX
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000023c5c9a0
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
```

Not sure if channel 1 will be any more stable. It's in a very rural environment so it would be surprising, but it's worth a try.

Changing the drivers could be an interesting step to try out too though...

---

### Post by chili555 on 2011-03-09
> So I tried removing the network manager and edited the interfaces file, but could not get any connectionI assume you double-checked the encryption key. Also, I notice the signal strength is pretty low. > Cell 01 - Address: D2:40:E4:XX:XX:XX
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=[COLOR="Red"]36/70[/COLOR]  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"eeenh"
Does syslog have any interesting reasons why it wouldn't connect?

Could I proofread your static *interfaces* file?

---

### Post by chili555 on 2011-03-09
FYI, here is my relevant syslog. My wireless, on this laptop, uses *interfaces* and not NM:> Mar  9 07:03:06 LAPTOP60 wpa_supplicant[1116]: Authentication with 00:00:00:00:00:00 timed out.
Mar  9 07:03:06 LAPTOP60 wpa_supplicant[1116]: Failed to initiate AP scan.
Mar  9 07:03:06 LAPTOP60 kernel: [   34.177081] wlan0: no IPv6 routers present
Mar  9 07:03:07 LAPTOP60 wpa_supplicant[1116]: Trying to associate with 00:24:56:2a:xx:xx (SSID='GBR1' freq=2462 MHz)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.562762] wlan0: authenticate with 00:24:56:2a:xx:xx (try 1)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.564932] wlan0: authenticated
Mar  9 07:03:07 LAPTOP60 kernel: [   34.564986] wlan0: associate with 00:24:56:2a:xx:xx (try 1)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.567044] wlan0: RX AssocResp from 00:24:56:2a:xx:xx (capab=0x431 status=0 aid=1)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.567051] wlan0: associated
Mar  9 07:03:07 LAPTOP60 wpa_supplicant[1116]: Associated with 00:24:56:2a:xx:xx
Mar  9 07:03:07 LAPTOP60 kernel: [   34.568706] cfg80211: Calling CRDA for country: US
Mar  9 07:03:07 LAPTOP60 kernel: [   34.573828] cfg80211: Regulatory domain changed to country: US
Mar  9 07:03:07 LAPTOP60 kernel: [   34.573833]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.573837]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.573841]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.573845]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.573848]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.573852]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar  9 07:03:07 LAPTOP60 kernel: [   34.573856]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Mar  9 07:03:07 LAPTOP60 wpa_supplicant[1116]: WPA: Key negotiation completed with 00:24:56:2a:xx:xx [PTK=CCMP GTK=CCMP]
Mar  9 07:03:07 LAPTOP60 wpa_supplicant[1116]: CTRL-EVENT-CONNECTED - Connection to 00:24:56:2a:xx:xx completed (auth) [id=0 id_str=]
Mar  9 07:03:07 LAPTOP60 wpa_supplicant[1116]: WPA: Group rekeying completed with 00:24:56:2a:xx:xx [GTK=CCMP]


---

### Post by Gelupah on 2011-03-09
> **chili555 said:**
> I assume you double-checked the encryption key. Also, I notice the signal strength is pretty low. Does syslog have any interesting reasons why it wouldn't connect?

Could I proofread your static *interfaces* file?

This is my *interfaces* file:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.25
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid eeenh
wpa-psk xxx

#auto eth0
iface eth0 inet static
address 192.168.137.1
netmask 255.255.255.0
gateway 192.168.1.1
```

You are right in assuming I check the wpa-psk, no errors there. In DHCP the internet wouldn't work, so I tried with a static IP, but no luck without the network manager installed. Let me get a syslog of both cases: when the system starts up (and internet doesn't work), and one with the wifi manually reconnected...

---

### Post by Gelupah on 2011-03-09
So, this is interesting, here goes the syslog when I first boot:

```
Mar  9 18:12:01 BBF ovpn-ivacy-client[1153]: RESOLVE: Cannot resolve host address: openvpn.ivacy.com: [HOST_NOT_FOUND] The specified host is unknown.
Mar  9 18:12:01 BBF avahi-daemon[1026]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::219:5bff:xxxx:xxxx.
Mar  9 18:12:01 BBF avahi-daemon[1026]: New relevant interface wlan0.IPv6 for mDNS.
Mar  9 18:12:01 BBF avahi-daemon[1026]: Registering new address record for fe80::219:5bff:xxxx:xxxx on wlan0.*.
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> Policy set 'Auto eeenh' (wlan0) as default for IPv4 routing and DNS.
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> Activation (wlan0) successful, device activated.
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar  9 18:12:02 BBF nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Mar  9 18:12:04 BBF pulseaudio[1657]: ratelimit.c: 21 events suppressed
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: RESOLVE: NOTE: openvpn.ivacy.com resolves to 3 addresses, choosing one by random
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: Socket Buffers: R=[114688->131072] S=[114688->131072]
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: UDPv4 link local: [undef]
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: UDPv4 link remote: [AF_INET]213.232.200.171:1194
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: TLS: Initial packet from [AF_INET]213.232.200.171:1194, sid=568260ce d5e5a91a
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Mar  9 18:12:07 BBF ovpn-ivacy-client[1153]: VERIFY OK: depth=1, /C=RU/ST=MR/L=Moscow/O=ivacy.com/CN=ivacy.com_CA/emailAddress=admin@ivacy.com
Mar  9 18:12:07 BBF ovpn-ivacy-client[1153]: VERIFY OK: nsCertType=SERVER
Mar  9 18:12:07 BBF ovpn-ivacy-client[1153]: VERIFY OK: depth=0, /C=RU/ST=MR/L=Moscow/O=ivacy.com/CN=openvpn.ivacy.com/emailAddress=admin@ivacy.com
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: [openvpn.ivacy.com] Peer Connection Initiated with [AF_INET]213.232.200.171:1194
Mar  9 18:12:10 BBF kernel: [   67.232082] wlan0: no IPv6 routers present
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: SENT CONTROL [openvpn.ivacy.com]: 'PUSH_REQUEST' (status=1)
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: PUSH: Received control message: 'PUSH_REPLY,route 1.0.0.0 255.0.0.0,dhcp-option DNS 1.254.2.2,dhcp-option DNS 1.254.2.3,dhcp-option DOMAIN vpn,explicit-exit-notify 2,route-gateway 1.2.116.1,topology subnet,ping 10,ping-restart 60,ifconfig 1.2.116.114 255.255.252.0'
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: timers and/or timeouts modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: explicit notify parm(s) modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: --ifconfig/up options modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: route options modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: route-related options modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: ROUTE default_gateway=192.168.1.1
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: TUN/TAP device tun0 opened
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: TUN/TAP TX queue length set to 100
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: /sbin/ifconfig tun0 1.2.116.114 netmask 255.255.252.0 mtu 1500 broadcast 1.2.119.255
Mar  9 18:12:10 BBF NetworkManager[1027]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Mar  9 18:12:10 BBF NetworkManager[1027]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Mar  9 18:12:10 BBF modem-manager: (net/tun0): could not get port's parent device
Mar  9 18:12:10 BBF kernel: [   67.819555] tun0: Disabled Privacy Extensions
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: /sbin/route add -net 213.232.200.171 netmask 255.255.255.255 gw 192.168.1.1
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 1.2.116.1
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: WARNING: potential route subnet conflict between local LAN [1.2.116.0/255.255.255.0] and remote VPN [1.0.0.0/255.0.0.0]
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: /sbin/route add -net 1.0.0.0 netmask 255.0.0.0 gw 1.2.116.1
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: Initialization Sequence Completed
Mar  9 18:12:48 BBF NetworkManager[1027]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
su@BBF:~$ sudo tail -n50 /var/log/syslog
Mar  9 18:12:01 BBF ovpn-ivacy-client[1153]: RESOLVE: Cannot resolve host address: openvpn.ivacy.com: [HOST_NOT_FOUND] The specified host is unknown.
Mar  9 18:12:01 BBF avahi-daemon[1026]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::219:5bff:xxxx:xxxx.
Mar  9 18:12:01 BBF avahi-daemon[1026]: New relevant interface wlan0.IPv6 for mDNS.
Mar  9 18:12:01 BBF avahi-daemon[1026]: Registering new address record for fe80::219:5bff:xxxx:xxxx on wlan0.*.
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> Policy set 'Auto eeenh' (wlan0) as default for IPv4 routing and DNS.
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> Activation (wlan0) successful, device activated.
Mar  9 18:12:02 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar  9 18:12:02 BBF nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Mar  9 18:12:04 BBF pulseaudio[1657]: ratelimit.c: 21 events suppressed
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: RESOLVE: NOTE: openvpn.ivacy.com resolves to 3 addresses, choosing one by random
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: Socket Buffers: R=[114688->131072] S=[114688->131072]
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: UDPv4 link local: [undef]
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: UDPv4 link remote: [AF_INET]213.232.200.171:1194
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: TLS: Initial packet from [AF_INET]213.232.200.171:1194, sid=568260ce d5e5a91a
Mar  9 18:12:06 BBF ovpn-ivacy-client[1153]: WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Mar  9 18:12:07 BBF ovpn-ivacy-client[1153]: VERIFY OK: depth=1, /C=RU/ST=MR/L=Moscow/O=ivacy.com/CN=ivacy.com_CA/emailAddress=admin@ivacy.com
Mar  9 18:12:07 BBF ovpn-ivacy-client[1153]: VERIFY OK: nsCertType=SERVER
Mar  9 18:12:07 BBF ovpn-ivacy-client[1153]: VERIFY OK: depth=0, /C=RU/ST=MR/L=Moscow/O=ivacy.com/CN=openvpn.ivacy.com/emailAddress=admin@ivacy.com
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Mar  9 18:12:08 BBF ovpn-ivacy-client[1153]: [openvpn.ivacy.com] Peer Connection Initiated with [AF_INET]213.232.200.171:1194
Mar  9 18:12:10 BBF kernel: [   67.232082] wlan0: no IPv6 routers present
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: SENT CONTROL [openvpn.ivacy.com]: 'PUSH_REQUEST' (status=1)
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: PUSH: Received control message: 'PUSH_REPLY,route 1.0.0.0 255.0.0.0,dhcp-option DNS 1.254.2.2,dhcp-option DNS 1.254.2.3,dhcp-option DOMAIN vpn,explicit-exit-notify 2,route-gateway 1.2.116.1,topology subnet,ping 10,ping-restart 60,ifconfig 1.2.116.114 255.255.252.0'
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: timers and/or timeouts modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: explicit notify parm(s) modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: --ifconfig/up options modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: route options modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: route-related options modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: ROUTE default_gateway=192.168.1.1
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: TUN/TAP device tun0 opened
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: TUN/TAP TX queue length set to 100
Mar  9 18:12:10 BBF ovpn-ivacy-client[1153]: /sbin/ifconfig tun0 1.2.116.114 netmask 255.255.252.0 mtu 1500 broadcast 1.2.119.255
Mar  9 18:12:10 BBF NetworkManager[1027]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Mar  9 18:12:10 BBF NetworkManager[1027]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Mar  9 18:12:10 BBF modem-manager: (net/tun0): could not get port's parent device
Mar  9 18:12:10 BBF kernel: [   67.819555] tun0: Disabled Privacy Extensions
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: /sbin/route add -net 213.232.200.171 netmask 255.255.255.255 gw 192.168.1.1
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 1.2.116.1
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: WARNING: potential route subnet conflict between local LAN [1.2.116.0/255.255.255.0] and remote VPN [1.0.0.0/255.0.0.0]
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: /sbin/route add -net 1.0.0.0 netmask 255.0.0.0 gw 1.2.116.1
Mar  9 18:12:13 BBF ovpn-ivacy-client[1153]: Initialization Sequence Completed
Mar  9 18:12:48 BBF NetworkManager[1027]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
```

The '*Mar  9 18:12:02 BBF nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.*' section is probably simply due to the fact I had deleted the files and folders in /etc/network and /etc/NetworkManager/ before resinstalling the network manager...

Now, once I manually reconnect to the WiFi, this is what I get:

```
Mar  9 18:14:51 BBF kernel: [  228.539745] wlan0: associated
Mar  9 18:14:51 BBF wpa_supplicant[1076]: Associated with d2:40:e4:xx:xx:xx
Mar  9 18:14:51 BBF NetworkManager[1027]: <info> (wlan0): supplicant connection state:  associating -> associated
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar  9 18:14:52 BBF wpa_supplicant[1076]: WPA: Key negotiation completed with d2:40:e4:xx:xx:xx [PTK=CCMP GTK=TKIP]
Mar  9 18:14:52 BBF wpa_supplicant[1076]: CTRL-EVENT-CONNECTED - Connection to d2:40:e4:xx:xx:xx completed (reauth) [id=0 id_str=]
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'eeenh'.
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> dhclient started with pid 1917
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar  9 18:14:52 BBF dhclient: Internet Systems Consortium DHCP Client V3.1.3
Mar  9 18:14:52 BBF dhclient: Copyright 2004-2009 Internet Systems Consortium.
Mar  9 18:14:52 BBF dhclient: All rights reserved.
Mar  9 18:14:52 BBF dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar  9 18:14:52 BBF dhclient: 
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar  9 18:14:52 BBF dhclient: Listening on LPF/wlan0/00:19:5b:xx:xx:xx
Mar  9 18:14:52 BBF dhclient: Sending on   LPF/wlan0/00:19:5b:xx:xx:xx
Mar  9 18:14:52 BBF dhclient: Sending on   Socket/fallback
Mar  9 18:14:52 BBF dhclient: DHCPREQUEST of 192.168.1.11 on wlan0 to 255.255.255.255 port 67
Mar  9 18:14:52 BBF dhclient: DHCPACK of 192.168.1.11 from 192.168.1.1
Mar  9 18:14:52 BBF dhclient: bound to 192.168.1.11 -- renewal in 406745 seconds.
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Mar  9 18:14:52 BBF NetworkManager[1027]: <info>   address 192.168.1.11
Mar  9 18:14:52 BBF NetworkManager[1027]: <info>   prefix 24 (255.255.255.0)
Mar  9 18:14:52 BBF NetworkManager[1027]: <info>   gateway 192.168.1.1
Mar  9 18:14:52 BBF NetworkManager[1027]: <info>   nameserver '212.27.40.240'
Mar  9 18:14:52 BBF NetworkManager[1027]: <info>   nameserver '212.27.40.241'
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar  9 18:14:52 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar  9 18:14:52 BBF avahi-daemon[1026]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.11.
Mar  9 18:14:52 BBF avahi-daemon[1026]: New relevant interface wlan0.IPv4 for mDNS.
Mar  9 18:14:52 BBF avahi-daemon[1026]: Registering new address record for 192.168.1.11 on wlan0.IPv4.
Mar  9 18:14:53 BBF NetworkManager[1027]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Mar  9 18:14:53 BBF NetworkManager[1027]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar  9 18:14:53 BBF NetworkManager[1027]: <info> Policy set 'Auto eeenh' (wlan0) as default for IPv4 routing and DNS.
Mar  9 18:14:53 BBF NetworkManager[1027]: <info> Activation (wlan0) successful, device activated.
Mar  9 18:14:53 BBF NetworkManager[1027]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar  9 18:14:53 BBF nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Mar  9 18:15:52 BBF NetworkManager[1027]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar  9 18:17:01 BBF CRON[2001]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Ivacy is the VPN I use (when I get the thing to work); I can try uninstalling cisco VPN and OpenVPN protocols as I only use PPTP anyway, if that could help in anyway... I added those after reinstalling the network manager though, as I was trying to fix the VPN...

---

### Post by Gelupah on 2011-03-10
Well, for the first time in a long time, I booted my computer, and the internet worked right away, no need to manually reconnect. The only things I did since were to remove the openvpn and cisco vpn packages, which were not used anyway. No idea if that could have helped, but I'm really hoping the stability will remain. I'll report back soon, hoping we can classify this issue as "solved"!

---

### Post by chili555 on 2011-03-10
**Fingers crossed!**

---

### Post by Gelupah on 2011-03-11
So far so good! My eth0 is still disabled, I'm not sure I dare enable it, just in case! Might give it another couple of days before I try that...

I have no idea what could have fixed this though?!

---

### Post by chili555 on 2011-03-11
> My eth0 is still disabled, I'm not sure I dare enable it, just in case!You don't have to do anything in particular; just don't attach the cable. I'm glad it's working.

---

### Post by driftless on 2011-03-11
This has been great - and super informative, but I am curious if there is an answer to the original question:

>  Is there a way of resetting all of the network settings to standard, as if a fresh copy of ubuntu had just been installed?

Sometimes, you just have to hit the big fat reset button. I've searched for several hours now, and everyone who asks this simple question gets the answer: "lets try and figure out what's wrong first."

For me - it worked originally, I installed and quickly uninstalled a program, went down a rabbit-hole trying to fix things, now I just don't want to mess with it any more.

So - Is there?

---

### Post by chili555 on 2011-03-11
> Sometimes, you just have to hit the big fat reset button. 
.....
So - Is there?No, short of a fresh install. You can try the method above; remove and purge Network Manager and reinstall it. Search your home directory for any and every file remotely related to NM and delete it. Even then, the fault may actually be the driver or some configuration file you wrote or amended. So, let me say it again: "lets try and figure out what's wrong first."

Unless you are sure you have an Atheros ath5k device, please start a new thread and PM me the link.

---

### Post by Gelupah on 2011-03-12
Well, messing about with all of those different ideas somehow eventually fixed my issue.

chili555 - Thanks very much for the help, much appreciated. This will remain a good bookmark for any future network related issues.

driftless - good luck if you are facing similar issues, and please do share if you find anything interesting!

---

### Post by ROLOXT on 2011-07-20
Hello, I'm having problems with my wifi adapter and in the process of trying to enable it I lost wlan0. I can't see NM I'm connected with a mobile broadband modem, and really I'm at a loss. Should I reset to default settings all network changes I may have done?. Here is the current output. 

ubuntu@ubuntu:~$ rfkill unblock wifi
ubuntu@ubuntu:~$ rfkill unblock wifi
ubuntu@ubuntu:~$ sudo ifconfig wlan0 down
ubuntu@ubuntu:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:90:69:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:dc100000-dc100fff
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 15
       serial: 00:13:a9:3d:0f:86
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:d8000000-d8003fff ioport:3000(size=256)
ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 15)
09:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
09:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
09:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
ubuntu@ubuntu:~$ rfkill unblock wifi
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:90:69:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:dc100000-dc100fff
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 15
       serial: 00:13:a9:3d:0f:86
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:d8000000-d8003fff ioport:3000(size=256)

---

### Post by nm_geo on 2011-07-20
ROLOXT

You wireless switch appears to be off.. Is it not on the lower left front of your computer?

---

