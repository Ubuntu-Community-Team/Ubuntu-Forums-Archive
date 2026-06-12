---
title: "Acer Aspire Revo R3700 wireless - DHCPDISCOVER no working leases."
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by graabein on 2011-03-14
Hi, so I got myself the Revo R3700 and installed XBMC Live which is basically Ubuntu 10.04 that boots straight into XBMC. And as always I can't get wireless to work on Linux. I'm no expert here. 

I followed [this thread]("http://forum.xbmc.org/showthread.php?t=85765") including post #6 and I can now see my network with iwlist scan but I can't connect to it. I've tried mucking about with wpa_supplicant.conf also. 

iwconfig shows the following for wlan0:
```
RT2860 Wireless  ESSID: "" Nickname: "RT2860STA"
Mode: Auto  Frequency=2.412 GHz  Access Point: Not-Associated
Bit Rate:1 Mb/s
RTS thr:off  Fragment thr:off
Link Quality=10/100  Signal level:0 dBm Noise level:-115 dBm
```

I can see my network with iwlist scan as:
```
ESSID:"SuperNetwork"
Mode:Managed
Channel:11
Quality:37/100  Signal level:-75 dBm  Noise level:-115 dBm
Encryption key:on
Bit Rates:54 Mb/s
IE: WPA Version 1
    Group Cipher: TKIP
    Pairwise Ciphers (2): CCMP TKIP
    Authentication Suites (1): PSK
```

My /etc/network/interfaces is at the moment:
```
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
wpa-ssid SuperNetwork
wpa-ap-scan 0
wpa-proto WPA
wpa-pairwise CCMP TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk X
```

Where X is the secret password doing this: 
```
wpa_passphrase <yourAPssid> <yourpassphrase> 
```

Trying to connect I get rows of:
```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval ...
...
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

So what should I do? Any help would be greatly appreciated!

---

### Post by chili555 on 2011-03-14
That's a very busy *interfaces* file! Try this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid SuperNetwork
#wpa-ap-scan 0
#wpa-proto WPA
#wpa-pairwise CCMP TKIP
#wpa-group TKIP
#wpa-key-mgmt WPA-PSK
wpa-psk <yourpassphrase>
```<yourpassphrase> in clear text; *not* put through the encryption device wpa_passphrase.

I notice the signal strength is low; are you close to the router?

Next, do:```
sudo ifdown wlan0 && sudo ifup wlan0
```Does it get a DHCP lease or time out?

---

### Post by graabein on 2011-03-15
Hi, thanks for answering. Didn't get home until now.

The signal strength is weak, yes, but I'm in the room next to the router. I did the changes to /etc/network/interfaces and restarted the network. Still getting the same result. No working leases.

---

### Post by chili555 on 2011-03-15
Let's sneak things in one at a time and see if we get any improvement. Before we start, take a look at:```
sudo ifdown wlan0 && sudo ifup wlan0
sudo tail -n25 /var/log/syslog
```See if you can see any messages about failure to connect. You can copy from the terminal to a text document and transfer the text on a USB key and post it here. For reference, here is a successful connection:> Mar 15 17:27:55 LAPTOP60 avahi-daemon[1396]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.108.
Mar 15 17:27:55 LAPTOP60 avahi-daemon[1396]: New relevant interface wlan0.IPv4 for mDNS.
Mar 15 17:27:55 LAPTOP60 avahi-daemon[1396]: Registering new address record for 192.168.1.108 on wlan0.IPv4.
Mar 15 17:27:55 LAPTOP60 kernel: [118263.121799] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 15 17:27:58 LAPTOP60 wpa_supplicant[1646]: Trying to associate with 00:24:56:2a:xx:xx (SSID='GBR1' freq=2462 MHz)
Mar 15 17:27:58 LAPTOP60 kernel: [118265.797126] wlan0: authenticate with 00:24:56:2a:xx:xx (try 1)
Mar 15 17:27:58 LAPTOP60 kernel: [118265.798945] wlan0: authenticated
Mar 15 17:27:58 LAPTOP60 kernel: [118265.798997] wlan0: associate with 00:24:56:2a:xx:xx (try 1)
Mar 15 17:27:58 LAPTOP60 kernel: [118265.800885] wlan0: RX AssocResp from 00:24:56:2a:xx:xx (capab=0x431 status=0 aid=2)
Mar 15 17:27:58 LAPTOP60 kernel: [118265.800892] wlan0: associatedMy interfaces file, aside from being set to static IP addresses, is identical to what I suggested.

Next, take away the # in front of wpa-ap-scan 0 and try again:```
sudo ifdown wlan0 && sudo ifup wlan0
sudo tail -n25 /var/log/syslog
```Any improvement?

---

### Post by graabein on 2011-03-16
Hi, I took snapshots of the screen. 

[Before]("http://dl.dropbox.com/u/11838265/IMAG0203.jpg"). [After]("http://dl.dropbox.com/u/11838265/IMAG0204.jpg").

---

### Post by chili555 on 2011-03-17
It looks improved. Now remove the # in front of wpa-pairwise CCMP TKIP. Can you connect now?

I'm still very concerned about signal strength.

---

### Post by graabein on 2011-03-17
Hi, I will try this when I get home in about 4-5 hours.

Do you have any suggestions to what I can do about signal strength? My main box also has a weak signal. It dual boots Vista and Ubuntu 10.10 and connects with a wireless dongle. Can I get a better router or some equipment to my router?

Another thing is I want to use a static IP for the Revo. I figure I will connect to it from other computers on the LAN running both Windows and GNU/Linux so static IP is probably the best, no?

Then maybe I can bypass the DHPC problem all together? 

Thanks for your help btw, it's much appreciated :)

---

### Post by chili555 on 2011-03-17
Here is a post reflecting thoughts about low strength: [http://ubuntuforums.org/showpost.php?p=10562752&postcount=7](http://ubuntuforums.org/showpost.php?p=10562752&postcount=7)> Another thing is I want to use a static IP for the Revo. I figure I will connect to it from other computers on the LAN running both Windows and GNU/Linux so static IP is probably the best, no?Actually, some of the Windows-compatibility tools, winbind, samba and others, don't depend on static IP addresses. I don't have much experience with all this; I have no Windows or Mac machines on my network. There are many threads on this forum about file and printer sharing from Linux to Windows.> Then maybe I can bypass the DHPC problem all together? Probably not true. If your router and your Ubuntu machine agree about all of the encryption details, it will connect either way, static or DHCP; if not, it won't connect either way.

---

### Post by graabein on 2011-03-17
I've moved my router a bit and signal strength is now at about 75% on my main box and 60% on the Revo. Hope that's good enough? :)

I wanna try NFS on the Revo and mount its external USB drive directly on my main box. I will use FTP for the windows machines (maybe do some backup and get some music for portable music players) and SSH for maintenance from the main box. 

But first I have to get it online. I added wpa-pairwise CCMP TKIP to /etc/network/interfaces, down/up and tail syslog. Image proof [here]("http://dl.dropbox.com/u/11838265/IMAG0205.jpg").

Maybe disable avahi daemon? The Revo boots directly into xbmc. I don't know on which user. But any daemons and configuration in /etc/network/interfaces is used anyhow, right?

---

### Post by chili555 on 2011-03-17
I'm trying to understand XMBC better. I'm downloading the live CD now. In the meantime, are you sure that Network Manager is not installed, not running and not even in the same city with you? NM will resist manual methods and make connection with /etc/network/interfaces almost impossible.

What does this tell us?```
ps aux | grep -i network
```

---

### Post by graabein on 2011-03-17
It says <username> 1968 0.0 0.0 3324 860 tty1 S+ 20:52 0:00 grep --color=auto -i network

---

### Post by graabein on 2011-03-29
I haven't solved this yet. I noticed though that wpa_supplicant is running. Is it supposed to? Found nothing doing ps -A | grep nm or grep network.

Edit: It also reads from [Kernel] No IPv6 routers present in the sys.log. Does that matter anything?

---

