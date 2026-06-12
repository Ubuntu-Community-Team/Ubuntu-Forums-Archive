---
title: "Wi-Fi connection intermittency (DNS lookup failed):"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by spitfirejunky on 2012-07-08
[B]SOLUTION:

[http://ubuntuforums.org/showpost.php?p=12102147&postcount=7](http://ubuntuforums.org/showpost.php?p=12102147&postcount=7)

To elaborate on this solution:

If you're running 12.04, you can navigate to:

/etc/default/crda

And add/modify the following line:

# The country code that corresponds to 
# your wireless router. I'm in the US so:
REGDOMAIN=US

Save, then restart.[/B]

---------------------

Periodically my internet connection will drop (although the notifier will indicate I'm still connected) and I'll get "DNS lookup failed" errors inside any web browser. I called all of these immediately after my connection dropped.


lsusb:
```

rude@Rude-Linux:~$ lsusb
Bus 002 Device 004: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 802.11n [Atheros AR9170]

```

iwconfig:
```

rude@Rude-Linux:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"DOODEE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:AA:4B:2C:F4:F0   
          Bit Rate=130 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1440  Invalid misc:116   Missed beacon:0

```

dmesg:
```

rude@Rude-Linux:~$ dmesg
[   14.969707] wlan0: authenticate with 20:aa:4b:2c:f4:f0 (try 1)
[   14.971319] wlan0: authenticated
[   15.079513] wlan0: associate with 20:aa:4b:2c:f4:f0 (try 1)
[   15.083525] wlan0: RX AssocResp from 20:aa:4b:2c:f4:f0 (capab=0x411 status=0 aid=3)
[   15.083528] wlan0: associated
[   15.184087] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   35.652830] ieee80211 phy0: channel change: 2447 -> 2452 failed (3).
[   45.537091] audit_printk_skb: 45 callbacks suppressed
[   45.537093] type=1701 audit(1341763463.537:27): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2480 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7ffe80627eb0 code=0x50002
[   45.537102] type=1701 audit(1341763463.537:28): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2480 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7ffe80627eb0 code=0x50002
[   45.556989] type=1701 audit(1341763463.557:29): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2486 comm="chrome" reason="seccomp" sig=0 syscall=59 compat=0 ip=0x7ffe80601427 code=0x50002
[   45.779478] type=1701 audit(1341763463.777:30): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2401 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7fa49c670e47 code=0x50002
[   45.779484] type=1701 audit(1341763463.777:31): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2401 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7fa49c670e47 code=0x50002
[   45.783427] type=1701 audit(1341763463.781:32): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2401 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa49c670eb0 code=0x50002
[   45.783435] type=1701 audit(1341763463.781:33): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2401 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa49c670eb0 code=0x50002
[  174.294195] type=1701 audit(1341763592.414:34): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2401 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7fa49c670e47 code=0x50002
[  174.294207] type=1701 audit(1341763592.414:35): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2401 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7fa49c670e47 code=0x50002

```

iwlist scan:
```

rude@Rude-Linux:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 20:AA:4B:2C:F4:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"DOODEE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000011da451183
                    Extra: Last beacon: 77632ms ago
                    IE: Unknown: 0006444F4F444545
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD760050F204104A0001101044000102103B00010310470010EFF5877EC1289585ACE332361A52CC74102100074C696E6B7379731023000545313230301024000776322E302E30321042000234321054000800060050F2040001101100054531323030100800022688103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

```

lshw:
```

rude@Rude-Linux:~$ sudo lshw -C network
[sudo] password for rude: 
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 12
       serial: bc:ae:c5:0e:fe:1a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:75 memory:fbdfc000-fbdfffff ioport:d800(size=256) memory:fbdc0000-fbddffff
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 12
       serial: bc:ae:c5:0e:fa:fb
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:76 memory:fbcfc000-fbcfffff ioport:c800(size=256) memory:fbcc0000-fbcdffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:6
       logical name: wlan0
       serial: 00:22:2d:28:7e:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=carl9170 driverversion=3.2.0-26-generic firmware=1.9.5 ip=192.168.1.137 link=yes multicast=yes wireless=IEEE 802.11bgn

```

lsb_release and uname:
```

rude@Rude-Linux:~$ lsb_release -d
Description:	Ubuntu 12.04 LTS

rude@Rude-Linux:~$ uname -mr
3.2.0-26-generic x86_64

```

**The pattern I notice is under "iwconfig". Whenever "Tx excessive retries" exceeds 1400, the connection fails.**

---

### Post by Marcelo Ruiz on 2012-07-08
I have the same problem with a realtek 8192se, even using the new 3.4.0-030400-generic x64 kernel.

---

### Post by spitfirejunky on 2012-07-09
Are you also experiencing that same "Tx excessive retries" pattern?

---

### Post by Marcelo Ruiz on 2012-07-09
Hi,
I reinstalled 12.04, so I cannot take a look at the old logs.
After reinstalling, I still had the same problems, until I figured how to solve it. I hope this can help you too:

[http://ubuntuforums.org/showpost.php?p=12088241&postcount=31]("http://ubuntuforums.org/showpost.php?p=12088241&postcount=31")

I am still using the 3.4 Kernel because that solved a drop connection problem for my wireless card (rtl8192se).
Cheers!

---

### Post by spitfirejunky on 2012-07-09
Awesome. =)

This unfortunately didn't work for me. My issue seems to be driver related.

---

### Post by Marcelo Ruiz on 2012-07-10
I forgot to mention that you need to restart the computer after making the changes...
If your connection is alive (meaning you can ping and receive the answer from the router and from the Internet) I guess the dig command with OpenDNS should work.
If your ip is 192.168.0.55 (for example) and the getaway is 192.168.0.1, then try:
```

ping 192.168.0.1

```
Do you get any answers?
If you do, what about Google's IP:
```

ping 208.117.253.155

```
Do you get any answers there?
It is very weird that your connection is alive and your just the dns lookup is the only thing failing. Did you try the dig commands? This one might not work,
```

dig omgubuntu.co.uk

```
but this one should if pinging Google's IP gave you an answer.
```

dig omgubuntu.co.uk @208.67.220.220

```
I am just a regular Ubuntu user (way far from being an expert), but the DNS lookup was driving me insane until I applied the solution in the thread I mentioned.
Still, just from common sense, I don't think the driver is the problem if you can communicate with the Internet...
Let us know.
Good luck!

---

### Post by spitfirejunky on 2012-07-14
Looks like everythings working properly now.

I did a dmesg and noticed that cfg80211 kept manipulating Wi-Fi frequencies.

One quick google got me to this solution:

[http://tech.chandrahasa.com/2012/05/31/fixing-wifi-regulatory-rule-in-unix/](http://tech.chandrahasa.com/2012/05/31/fixing-wifi-regulatory-rule-in-unix/)

Thanks all for the help.

---

