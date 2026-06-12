---
title: "Intel 2200BG WiFi Card Won't Connect"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by ultrageeky on 2010-07-25
I have an old Toshiba Satellite A30 Notepad. I've installed Ubuntu 10.04 onto it and everything but WiFi works. I've installed wicd and several other network tools but just can't get Ubuntu to let me use the WiFi connection (the option is greyed out).

I know the card works because the last OS (Windows XP) used it without any problems. The card is detected, the drivers are installed and the hardware (slider) switch is set to on.

I think the issue is related to the Radio Frequency Kill Switch being on but I don't know how to turn it off. Please help.

The output from various commands are:

sudo lshw -C network is:

```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:ce:e8:68
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:3000(size=256) memory:e0201800-e02018ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:cd:33:42
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:22 memory:e0200000-e0200fff

```

dmesg | grep ipw

```
[   23.372888] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   23.372895] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.613446] ipw2200 0000:02:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.624106] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.624193] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[   23.965666] ipw2200: Radio Frequency Kill Switch is On:
[   24.233276] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by ultrageeky on 2010-07-26
I take it no one has successfully got the Intel ipw2200BG wifi card to switch on in a Toshiba A30 Laptop?

---

### Post by chili555 on 2010-07-26
This may be of interest:  [http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI)

> Toshiba Satellite Pro A30 

The sellotape over pin 13 trick worked for my Intel Pro/Wireless 2100bg card but unfortunately the range is greatly reduced for some reason. This card works fine with full range capabibities in my newer laptop!

---

### Post by ultrageeky on 2010-07-26
Thank you Chili555, taking a look at it now.

---

### Post by ultrageeky on 2010-07-26
Chili555, taping off pin 13 worked. Unfortunately, it can't get an IP address.

---

### Post by ultrageeky on 2010-07-26
For others who might have a similar problem, I had to download the firmware from [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php), unpack it and move it to /lib/firmware then cover the 13th pin on the WiFi adapter. That got the card to detect.

I'll post back as soon as I've figured out how to get it to get an IP address.

---

### Post by chili555 on 2010-07-26
Does Network Manager show your access point? When you click to connect, are you asked for any encryption details? What does this tell us?```
sudo iwlist eth1 scan
iwconfig
```

---

### Post by ultrageeky on 2010-07-26
"sudo iwlist eth1 scan" outputs:

```
eth1      Scan completed :
          Cell 01 - Address: 00:24:17:C9:E8:E5
                    ESSID:"BTHomeHub2-K2WF"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1956ms ago
          Cell 02 - Address: 02:24:17:C9:E8:E7
                    ESSID:"BTFON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    Extra: Last beacon: 5380ms ago
          Cell 03 - Address: 00:13:64:37:9A:EF
                    ESSID:"Default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-37 dBm  
                    Extra: Last beacon: 156ms ago
```

The connection of "Cell 03", Default, is the main one that I need to connect to. I only tried the others in case it made any difference (they're not mine).

"iwconfig" outputs

```
eth1      unassociated  ESSID:"BTOpenzone"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 02:24:17:C9:E8:E6   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by chili555 on 2010-07-26
> eth1      unassociated  ESSID:"BTOpenzone"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 02:24:17:C9:E8:E6   
          [COLOR="Red"]Bit Rate:0 kb/s[/COLOR] You might try:```
sudo iwconfig eth1 rate auto
```Now see if Network Manager will connect to Default.

---

### Post by ultrageeky on 2010-07-26
Nope, still unable to get an IP address :(

---

### Post by chili555 on 2010-07-26
Let's have a look at:```
sudo cat /var/log/syslog | grep -i network
```Do you have an ethernet wired connection? You will probably have to disconnect the wire before Network Manager will use the wireless interface.

---

### Post by ultrageeky on 2010-07-26
Hello Chilli, sorry for my late reply - I kept refreshing the page without realizing we'd gone onto page 2.

The last command produced 1601 lines of data. I sent them directly to a text file which I've added as an attachment to this post (zipped).

However, here are the first 20 lines

```
Jul 24 20:00:42 BigBuz kernel: [    8.777381] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 24 20:00:42 BigBuz kernel: [    8.780206] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 24 20:00:42 BigBuz kernel: [    8.957950] type=1505 audit(1279998040.796:3):  operation="profile_load" pid=497 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 24 20:00:42 BigBuz kernel: [    9.357776] Kill switch must be turned off for wireless networking to work.
Jul 24 20:00:45 BigBuz avahi-daemon[720]: Network interface enumeration completed.
Jul 24 20:00:45 BigBuz kernel: [   13.930638] type=1505 audit(1279998045.768:7):  operation="profile_replace" pid=730 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 24 20:00:46 BigBuz NetworkManager: <info>  starting...
Jul 24 20:00:46 BigBuz NetworkManager: <info>  Trying to start the modem-manager...
Jul 24 20:00:47 BigBuz NetworkManager:    SCPlugin-Ifupdown: init!
Jul 24 20:00:47 BigBuz NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jul 24 20:00:47 BigBuz NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jul 24 20:00:47 BigBuz NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0)
Jul 24 20:00:47 BigBuz NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 24 20:00:47 BigBuz NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/eth1, iface: eth1)
Jul 24 20:00:47 BigBuz NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jul 24 20:00:47 BigBuz NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 24 20:00:47 BigBuz NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 24 20:00:47 BigBuz NetworkManager:    SCPlugin-Ifupdown: end _init.
Jul 24 20:00:47 BigBuz NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 24 20:00:47 BigBuz NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.

```

Here are the last 20 lines:

```
Jul 26 14:23:30 BigBuz NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 42)
Jul 26 14:31:56 BigBuz NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jul 26 14:31:56 BigBuz dhclient: receive_packet failed on eth0: Network is down
Jul 26 14:31:56 BigBuz NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Jul 26 14:33:13 BigBuz dhclient: send_packet: Network is unreachable
Jul 26 14:33:13 BigBuz NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jul 26 14:33:13 BigBuz dhclient: receive_packet failed on eth0: Network is down
Jul 26 14:33:13 BigBuz NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Jul 26 14:33:19 BigBuz dhclient: send_packet: Network is unreachable
Jul 26 14:33:19 BigBuz NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jul 26 14:33:19 BigBuz dhclient: receive_packet failed on eth0: Network is down
Jul 26 14:33:19 BigBuz NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Jul 26 14:34:46 BigBuz NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jul 26 14:34:51 BigBuz NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
Jul 26 14:34:51 BigBuz NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Jul 26 14:34:51 BigBuz NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 596
Jul 26 14:39:14 BigBuz dhclient: send_packet: Network is unreachable
Jul 26 14:40:31 BigBuz dhclient: send_packet: Network is unreachable
Jul 26 14:40:52 BigBuz dhclient: send_packet: Network is unreachable
Jul 26 14:42:34 BigBuz dhclient: send_packet: Network is unreachable
Jul 26 14:43:49 BigBuz dhclient: send_packet: Network is unreachable
```

---

### Post by chili555 on 2010-07-26
> NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 26 14:23:29 BigBuz NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 26 14:23:29 BigBuz NetworkManager: <info>    address 192.168.1.2
Jul 26 14:23:29 BigBuz NetworkManager: <info>    prefix 24 (255.255.255.0)
Jul 26 14:23:29 BigBuz NetworkManager: <info>    gateway 192.168.1.1
Jul 26 14:23:29 BigBuz NetworkManager: <info>    hostname 'BigBuz'
Jul 26 14:23:29 BigBuz NetworkManager: <info>    nameserver '192.168.1.1'
Jul 26 14:23:29 BigBuz NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 26 14:23:29 BigBuz NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 26 14:23:29 BigBuz NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...As I suspected, the wired ethernet appears connected and has an IP address. Please see: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themPlease unplug the ethernet cable and reboot. Then, if you do not connect, let us see:```
sudo cat /var/log/syslog | grep -i network
```Please post the last 25 lines.

---

### Post by ultrageeky on 2010-07-26
Chili, thank you, you gave me an idea: I'd installed wicd; when you mentioned Network Manager you made me realise that it might be interfering with wicd so I've removed Network Manger and sure enough it connected straight away.

So, the solution is:

[LIST=1]
[*]Download the firmware from [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php) and unpack it then move it to /lib/firmware
[*]Cover the 13th pin on the WiFi adapter (remove the card from its slot, turn it so that the pins point toward your body and the little notch is closer to your left than your right then cover the 6th pin in from the left with a small piece of non-metallic (non-conductive) tape/material ([http://www.minipci.biz/pin7.jpg]("http://www.minipci.biz/pin7.jpg") - the picture labels it as pin seven, it's isn't, it is pin 6)
[*]Put the wifi card back in its slot
[*]If Network Manger doesn't work, install wicd and remove Network Manger (use a wired connection to do it).
[/LIST]

Once again, thank you Chili.

---

### Post by chili555 on 2010-07-26
Great work! Glad it's working for you. Have fun and welcome to the Ubuntu family.

---

### Post by ultrageeky on 2010-07-26
I've used Ubuntu/Kubuntu/Mint for the last 4 years. I encourage as many people as I can to use it; hence the laptop problem (it's my nephews). I rarely have problems with it and those I do have can usually be quickly resolved but every so often a "little" problem occurs that should take five minutes to solve...

I'm not particularly a gnome fan (I prefer KDE) but it is lightweight enough to run on older hardware and to still look smart enough to compete with Windows (I hate Windows, pathologically - worked in IT support for too long).

---

