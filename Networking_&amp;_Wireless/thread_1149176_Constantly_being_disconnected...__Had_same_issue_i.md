---
title: "Constantly being disconnected...  Had same issue in Intrepid but not Hardy."
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by tegnoto89 on 2009-05-05
I'm running a thinkpad T61, and here's what my university gives me for setup, which I've used:

There is no official support for configuring linux ...
The latest Ubuntu and other distributions appear to work well out of the box with the exception of specifying the auth servers.
... if you get the supplicant compiled on other versions, here are the fundamental settings.

    * WPA-1 protocol (WPA).
    * TKIP session encryption.
    * PEAP authentication type.
    * MSCHAPv2 password encryption.
    * AuthServers secure1.syr.edu;secure2.syr.edu; 

These settings are NOT required for AirOrangeX and can be ignored:

    * Anonymous Identity
    * Client Certificate File
    * CA Certificate File
    * Private Key File
    * Private Key Password 


I'm constantly being disconnected.  Sometimes it reconnects, sometimes it asks me for my password and username again.  In Intrepid, I was having this problem, except it didn't ever reconnect on its own, I always had to type in my username again.  I had to downgrade to hardy, and I figured it would have been fixed for Jaunty, and now I'm really angry!  Any suggestions?  :-P

---

### Post by netwarriorwy on 2009-05-05
I don't know if it helps but my wireless security is wep 128 and the nm was disconnecting a lot in intrepid and also after doing  a fresh jaunty instalation...the problem with intrepid was not always, at some point it began...

I did this to get my connection stable:

[http://ubuntuforums.org/showthread.php?t=1147582]("http://ubuntuforums.org/showthread.php?t=1147582")

I hope it helps...

:)

---

### Post by tegnoto89 on 2009-05-05
Installed NTP...  got disconnected literally thirty seconds after it had finished.  Anyone else have ideas?

---

### Post by tegnoto89 on 2009-05-05
Here's my output of the following:

dmesg | tail
lshw -C Network
iwconfig
iwlist scan

```
dmesg | tail
[ 7556.821036] wlan0: associate with AP 00:17:df:2f:c0:c1
[ 7556.824617] wlan0: RX AssocResp from 00:17:df:2f:c0:c1 (capab=0x431 status=0 aid=4)
[ 7556.824623] wlan0: associated
[ 7603.555085] wlan0: authenticate with AP 00:17:df:2f:c0:c1
[ 7603.567610] wlan0: authenticate with AP 00:17:df:2f:c0:c1
[ 7603.567631] wlan0: authenticated
[ 7603.567637] wlan0: associate with AP 00:17:df:2f:c0:c1
[ 7603.575575] wlan0: RX ReassocResp from 00:17:df:2f:c0:c1 (capab=0x431 status=0 aid=4)
[ 7603.575580] wlan0: associated
[ 7621.457469] CE: hpet increasing min_delta_ns to 22500 nsec
tom@tom-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:6b:38:aa:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.3-0 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:76:8f:7f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=128.230.111.137 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:4f:7f:0f:2d:90
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
tom@tom-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"AirOrangeX"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:DF:2F:C0:C1   
          Bit Rate=48 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=62/100  Signal level:-70 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

tom@tom-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:DF:2F:C0:C1
                    ESSID:"AirOrangeX"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=65/100  Signal level:-70 dBm  Noise level=-96 dBm
                    Encryption key:on
                    IE: Unknown: 000A4169724F72616E676558
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1A
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 9606004096000500
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000020eeaa00ee
                    Extra: Last beacon: 84ms ago

pan0      Interface doesn't support scanning.

```

---

### Post by netwarriorwy on 2009-05-05
Well my friend, I'm not an expert but I'll tel you one thing...when I was trying to use WPA in my home network I had so much trouble that I went back to WEP 128, I had to constantly edit things in the interfaces file and so in the wpa_supplicant,however WPA worked just fine in Windows XP. So i decided to go back to WEP.

About your output are pretty much the same as me except for two things.
1. You are using WPA.
2. You are using the iwlagn driver for your 4965 card and I'm using iwl3945 for my 3945 card. Both cards are PRO/Wireless from Intel family.
[COLOR="Red"]
Check out this site.[/COLOR] [http://www.intellinuxwireless.org/]("http://www.intellinuxwireless.org/") They say that in case of using a card like yours, you should be using the new iwlwifi driver instead of the iwlagn that is for the latest laptops.

I hope it helps.:P

---

