---
title: "WPA2 Issues (Dell Insprion 5100, Broadcom BCM4309)"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by jubu8 on 2009-07-31
Hello, I recently installed Ubuntu 9.04 on a Dell Inspiron 5100. All of the hardware is installed properly and works as it should, except for the wireless card. I am able to connect to my WPA2 protected network, but it is a challenge. I may have to restart the laptop five or so times before it will successfully connect. When it fails to connect, it will stall for a short while and then prompt me for the password to my network. Upon entering my password, it will stall and the process will repeat. I have included the output of a few commands incase they are needed.

--

lspci

```
02:02.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)
```

iwconfig

```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod | grep 'b43legacy'

```
b43legacy             127004  0 
mac80211              217464  1 b43legacy
led_class              12036  1 b43legacy
input_polldev          11912  1 b43legacy
ssb                    41220  2 b43legacy,b44
```

dmesg

```
[   26.164053] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[   26.295098] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   26.369869] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   26.740053] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   26.804566] b43legacy-phy0 debug: Chip initialized
[   26.804878] b43legacy-phy0 debug: 30-bit DMA initialized
[   26.807073] Registered led device: b43legacy-phy0:tx
[   26.807097] Registered led device: b43legacy-phy0:rx
[   26.807124] Registered led device: b43legacy-phy0:radio
[   26.807157] b43legacy-phy0 debug: Wireless interface started
[   26.814142] b43legacy-phy0 debug: Adding Interface type 2
[   26.826096] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.348083] wlan0: authenticate with AP 00:14:bf:df:05:48
[   28.352603] wlan0: authenticated
[   28.352608] wlan0: associate with AP 00:14:bf:df:05:48
[   28.355160] wlan0: RX AssocResp from 00:14:bf:df:05:48 (capab=0x1 status=0 aid=2)
[   28.355163] wlan0: associated
[   28.355595] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.397379] wlan0: disassociating by local choice (reason=3)
[   39.344027] wlan0: no IPv6 routers present
[   56.436096] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[   56.636036] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[   56.836072] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[   57.036087] wlan0: authentication with AP 00:1a:70:d4:2a:89 timed out
[   66.420933] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 1
[   66.420987] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 1
[   66.620042] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 2
[   66.820050] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 3
[   67.020050] wlan0: direct probe to AP 00:1a:70:d4:2a:89 timed out
[   77.932928] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 1
[   77.932980] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 1
[   78.132116] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 2
[   78.332056] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 3
[   78.532039] wlan0: direct probe to AP 00:1a:70:d4:2a:89 timed out
[   89.508477] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 1
[   89.508527] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 1
[   89.708216] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 2
[   89.908286] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 3
[   90.108052] wlan0: direct probe to AP 00:1a:70:d4:2a:89 timed out
[   99.094280] wlan0 direct probe responded
[   99.094288] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[   99.292061] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[   99.492048] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[   99.692041] wlan0: authentication with AP 00:1a:70:d4:2a:89 timed out
[  101.296432] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[  101.296476] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[  101.496049] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[  101.696051] wlan0: authenticate with AP 00:1a:70:d4:2a:89
[  101.896055] wlan0: authentication with AP 00:1a:70:d4:2a:89 timed out
[  112.856086] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 1
[  112.856144] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 1
[  113.056035] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 2
[  113.264604] wlan0: direct probe to AP 00:1a:70:d4:2a:89 try 3
[  113.464040] wlan0: direct probe to AP 00:1a:70:d4:2a:89 timed out
[  387.828172] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  387.852566] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  387.854103] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  387.909149] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  387.930938] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  387.932484] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  387.987788] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  387.989341] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
```

---

### Post by skinnejay on 2009-10-08
Hi I have a similar setup as well except my dell inspiron 5100 is using a broadcom bcm4306 rev 02 chipset and have karmic installed. I am able to connect eventually after a really long WPA2 handshake but the connection only works for a few minutes before it conks out. NM still shows it connected but the internet times out. Don't think its a hardware issue cause it works fine in windows vista. So far, haven't had any luck finding a fix on the forums or launchpad. Any help keeping the connection up and running would be great. Would hate to go back to ndiswrapper and WEP security.

---

### Post by buntumaddy on 2010-05-03
Any updates on this issue? I'm trying to debug the same issue on a friend's hp pavilion ze4430US with Broadcom 4306 v02 chipset. I see a whole bunch of "Unexpected value for chanstat (0x7C00)" warnings in /var/log/messages. If I can't get this resolved, he  would go back to Windows XP :(. Need help to keep him from moving to the dark side again.

O, and this is on 10.04 LTS with all latest updates installed as of today. Using restricted drivers available through Hardware Drivers admin app.

---

### Post by adssse on 2010-05-09
I am having a similar issue in 10.04 (in fact it hasnt worked for me since 8.10 which I am currently still using) with the Broadcom 4306 v02. I am currently using the B43Legacy driver. I am sometimes able to connect to unencrypted networks, but have been unable to connect to my wep encrypted G network. It tries to connect but just repeatedly asks for the key and fails authentication. Like I mentioned, I have no problem with this under 8.10 using the same legacy driver and settings so I am not sure what changed between that and 9.04.

Any help would be great.

---

### Post by filibertov on 2011-01-13
I would really like to see someone help with this thread. I have not been able to connect with my Broadcom 4306 rev02 using 9.04, 9.10 or 10.04.  The network manager, after installing drivers with the HARDWARE DRIVERS tool - specifically b43-fwcutter, finally sees all the wireless networks around, but when I try to connect and enter the password, it always comes back asking for the password.  As in the above post, dmesg is flooded with:

b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)

I've tried setting up through command line, interfaces, network-manager and wicd.  Wicd says BAD PASSWORD in the gtk gui and the log shows

Sending connection attempt result bad_pass

 I know I have the password right because I have tested with at least 10 different computer (work). And I am using the Hex form, not the ASCII, of the password.

So, can anyone give a suggestion? I believe it is a bug since I've read on the internet people having it work the last time as of 8.04 but there is no information that I can find.  Thanks.

---

