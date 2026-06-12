---
title: "Intel Ultimat n 6300 Connection Issues - denied authentication (status 17)"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by rschlaikjer on 2011-11-30
I recently got  new thinkpad, and opted for the big wifi card: Intel Ultimate-N 6300. The only problem is, it has some real trouble connecting to the wireless at my college campus. Looking at syslog, it seems that network-manager roams around the different APs, looking to authenticate and usually getting rejected with status 17. Eventually, it does manage to connect. 
The computer could connect to a small wireless created by another computer no problem, but I haven't had a chance to check on more wireless networks.
Has anyone had similar problems with this card? I tried the ubuntu default iwlagn module, and am now running the iwlwifi module after downloading the latest version of compat-wireless and compiling it.

Relevant system information and logfiles:
```

lspci:
Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 3e)
ifconfig wlan0:
wlan0     Link encap:Ethernet  HWaddr 24:77:03:26:e8:50  
          inet addr:130.64.153.137  Bcast:130.64.153.255  Mask:255.255.255.0
          inet6 addr: fe80::2677:3ff:fe26:e850/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1288307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1016044127 (1.0 GB)  TX bytes:27674773 (27.6 MB)

 iwconfig wlan0:
wlan0     IEEE 802.11abgn  ESSID:"tuftswireless"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: 00:24:6C:60:D0:10   
          Bit Rate=300 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2749  Invalid misc:7   Missed beacon:0

lsmod | grep iw:
iwlwifi               320164  0 
mac80211              506154  1 iwlwifi
cfg80211              209294  2 iwlwifi,mac80211


dmesg | grep wlan:

[   12.059405] wlan0: direct probe to 00:24:6c:60:d0:00 (try 1/3)
[   12.258109] wlan0: direct probe to 00:24:6c:60:d0:00 (try 2/3)
[   12.457695] wlan0: direct probe to 00:24:6c:60:d0:00 (try 3/3)
[   12.657205] wlan0: direct probe to 00:24:6c:60:d0:00 timed out
[   20.624778] wlan0: direct probe to 00:24:6c:60:d0:00 (try 1/3)
[   20.822683] wlan0: direct probe to 00:24:6c:60:d0:00 (try 2/3)
[   21.022217] wlan0: direct probe to 00:24:6c:60:d0:00 (try 3/3)
[   21.221788] wlan0: direct probe to 00:24:6c:60:d0:00 timed out
[   29.105117] wlan0: direct probe to 00:24:6c:60:d0:00 (try 1/3)
[   29.303463] wlan0: direct probe to 00:24:6c:60:d0:00 (try 2/3)
[   29.503007] wlan0: direct probe to 00:24:6c:60:d0:00 (try 3/3)
[   29.702581] wlan0: direct probe to 00:24:6c:60:d0:00 timed out
[   37.888734] wlan0: direct probe to 00:24:6c:60:d0:00 (try 1/3)
[   38.087513] wlan0: direct probe to 00:24:6c:60:d0:00 (try 2/3)
[   38.287083] wlan0: direct probe to 00:24:6c:60:d0:00 (try 3/3)
[   38.486602] wlan0: direct probe to 00:24:6c:60:d0:00 timed out
[   46.376942] wlan0: authenticate with 00:24:6c:60:d0:00 (try 1)
[   46.411091] wlan0: 00:24:6c:60:d0:00 denied authentication (status 17)


syslog:

Nov 30 19:01:27 Beast kernel: [ 1924.850725] wlan0: authenticate with 00:24:6c:60:d0:00 (try 1)
Nov 30 19:01:27 Beast kernel: [ 1924.852183] wlan0: 00:24:6c:60:d0:00 denied authentication (status 17)
Nov 30 19:02:24 Beast NetworkManager[1332]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 30 19:02:24 Beast NetworkManager[1332]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 30 19:02:24 Beast NetworkManager[1332]: <warn> Activation (wlan0) failed for access point (tuftswireless)
Nov 30 19:02:24 Beast NetworkManager[1332]: <warn> Activation (wlan0) failed.
Nov 30 19:02:24 Beast NetworkManager[1332]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 30 19:02:24 Beast NetworkManager[1332]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 30 19:02:24 Beast NetworkManager[1332]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 30 19:02:24 Beast NetworkManager[1332]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Auto-activating connection 'Auto hpsetup'.
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Activation (wlan0) starting connection 'Auto hpsetup'
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Activation (wlan0/wireless): connection 'Auto hpsetup' requires no security.  No secrets needed.
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Config: added 'ssid' value 'tuftswireless'
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Config: added 'scan_ssid' value '1'
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> Config: set interface ap_scan to 1
Nov 30 19:02:27 Beast NetworkManager[1332]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 30 19:02:30 Beast wpa_supplicant[6090]: Trying to authenticate with 00:24:6c:60:d0:00 (SSID='tuftswireless' freq=2437 MHz)
Nov 30 19:02:30 Beast NetworkManager[1332]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 30 19:02:30 Beast kernel: [ 1987.684183] wlan0: authenticate with 00:24:6c:60:d0:00 (try 1)
Nov 30 19:02:30 Beast kernel: [ 1987.687421] wlan0: 00:24:6c:60:d0:00 denied authentication (status 17)


sudo iwlist scan:

wlan0     Scan completed :
          Cell 01 - Address: 00:24:6C:60:D0:10
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"tuftswireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005a132e5c6a
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000D7475667473776972656C657373
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 03019D
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D169D051B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C349D051B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:0B:86:58:19:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"tuftswireless"
                    Bit Rates:2 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000202533181
                    Extra: Last beacon: 9104ms ago
                    IE: Unknown: 000D7475667473776972656C657373
                    IE: Unknown: 0108840C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:24:6C:60:CF:A0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"tuftswireless"
                    Bit Rates:2 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c808e35af
                    Extra: Last beacon: 8704ms ago
                    IE: Unknown: 000D7475667473776972656C657373
                    IE: Unknown: 010884160C1218243048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:0B:86:58:1F:A0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"tuftswireless"
                    Bit Rates:2 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006687da181
                    Extra: Last beacon: 7328ms ago
                    IE: Unknown: 000D7475667473776972656C657373
                    IE: Unknown: 010884160C1218243048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010180
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:24:6C:60:CF:B0
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"tuftswireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002e94c969ed
                    Extra: Last beacon: 7072ms ago
                    IE: Unknown: 000D7475667473776972656C657373
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 030124
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3424050A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 06 - Address: 00:0B:86:59:FD:C8
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"tuftswireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005a137c235f
                    Extra: Last beacon: 6560ms ago
                    IE: Unknown: 000D7475667473776972656C657373
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 030128
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: 00:24:6C:60:D5:50
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"tuftswireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005a1328778d
                    Extra: Last beacon: 6336ms ago
                    IE: Unknown: 000D7475667473776972656C657373
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 03012C
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D162C0508000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C342C0508000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: 00:0B:86:58:1F:A8
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"tuftswireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005a13a8e1c3
                    Extra: Last beacon: 6124ms ago
                    IE: Unknown: 000D7475667473776972656C657373
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 030130
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 09 - Address: 00:24:6C:60:CF:F0
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"tuftswireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005a131955bb
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 000D7475667473776972656C657373
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 030195
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16950508000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34950508000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000


lsb_release -d:
Description:    Ubuntu 11.10

uname -a:
Linux Beast 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


```

---

### Post by jo9100 on 2012-01-26
I'm having a very very similar case:

[LIST]
[*]Campus Network (McGill University; Aruba APs)
[*]Thinkpad W520
[*]Intel Centrino Advanced-N 6205
[*]Ubuntu 11.10
[*]Denied authentications
[*]Kernel 3.0.0
[/LIST]

Do you still get the issue?
(Edit) I looked up the AP you were trying to connect to and it appears it was an Aruba too. Interesting.

Here's a piece of **kern.log**:

```
Jan 26 13:53:49 panhandle kernel: [247275.774327] wlan0: authenticate with d8:c7:c8:9b:c7:1a (try 1)
Jan 26 13:53:49 panhandle kernel: [247275.774909] wlan0: d8:c7:c8:9b:c7:1a denied authentication (status 17)
Jan 26 13:54:04 panhandle kernel: [247291.136443] wlan0: authenticate with d8:c7:c8:9b:c7:1a (try 1)
Jan 26 13:54:04 panhandle kernel: [247291.137069] wlan0: d8:c7:c8:9b:c7:1a denied authentication (status 17)
Jan 26 13:54:45 panhandle kernel: [247332.310923] wlan0: authenticate with d8:c7:c8:9b:c7:1a (try 1)
Jan 26 13:54:45 panhandle kernel: [247332.311801] wlan0: d8:c7:c8:9b:c7:1a denied authentication (status 17)
Jan 26 13:55:48 panhandle kernel: [247395.312898] wlan0: authenticate with d8:c7:c8:9b:c7:1a (try 1)
Jan 26 13:55:48 panhandle kernel: [247395.314273] wlan0: d8:c7:c8:9b:c7:1a denied authentication (status 17)
Jan 26 13:56:35 panhandle kernel: [247442.010012] wlan0: authenticate with d8:c7:c8:9b:c7:1a (try 1)
Jan 26 13:56:35 panhandle kernel: [247442.010648] wlan0: d8:c7:c8:9b:c7:1a denied authentication (status 17)
Jan 26 13:56:43 panhandle kernel: [247449.999230] wlan0: authenticate with d8:c7:c8:9b:c7:1a (try 1)
Jan 26 13:56:43 panhandle kernel: [247450.000100] wlan0: d8:c7:c8:9b:c7:1a denied authentication (status 17)
Jan 26 13:57:45 panhandle kernel: [247512.365361] wlan0: authenticate with d8:c7:c8:9b:c7:1a (try 1)
Jan 26 13:57:45 panhandle kernel: [247512.366002] wlan0: authenticated
Jan 26 13:57:45 panhandle kernel: [247512.366310] wlan0: associate with d8:c7:c8:9b:c7:1a (try 1)
Jan 26 13:57:45 panhandle kernel: [247512.368669] wlan0: RX ReassocResp from d8:c7:c8:9b:c7:1a (capab=0x411 status=0 aid=5)
Jan 26 13:57:45 panhandle kernel: [247512.368672] wlan0: associated
Jan 26 13:57:56 panhandle kernel: [247522.984584] wlan0: no IPv6 routers present

```

---

### Post by jo9100 on 2012-01-28
I have filed a bug with IWL: 
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2346](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2346)

---

### Post by Gelupah on 2012-01-29
Have you tried to configure wifi manually, without going through network manager ? The following link helped me :

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

On another note, how did you get your card to work in "N" mode? I have the same card, but mine just seems to want to run in g mode, although the router is N ! Is it supposed to be automatic?

---

### Post by parshimers on 2012-02-02
i also have this issue. it really does seem to be a driver bug. 
the status 17 is certainly bogus, because i can connect to the same wifi with the same credentials in the same room successfuly, first try with an android phone while iwlagn will refuse to do so.

---

### Post by hangelwen on 2012-03-16
> **parshimers said:**
> i also have this issue. it really does seem to be a driver bug. 
the status 17 is certainly bogus, because i can connect to the same wifi with the same credentials in the same room successfuly, first try with an android phone while iwlagn will refuse to do so.

I have the same issue. 
Campus network,Centrino Advanced-N 6230 card. 3.3.0-030300rc6-generic kernel. Thinkpad T420.

I had wifi problem with the old RTL8188ce card, and did not find a solution to solve it for the last servral months so I replaced the card with a intel one several days ago.
In the first two days it seemed all ok. But today it happend several times so I found this thread.

---

