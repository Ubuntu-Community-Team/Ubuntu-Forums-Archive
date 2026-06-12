---
title: "ath0 at bootup"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by kmacc on 2006-01-13
Hi, I've got a DWL-G510 in Kubuntu and although I can get it to work, it won't work at boot. I've got the following lines in my /etc/network/interfaces file (I've blanked out the key):

auto ath0
iface ath0 inet dhcp
name Wireless LAN card
wireless_essid Falcon
wireless_key XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX 
wireless_channel 6
wireless_mode managed

Whenever I boot, it takes ages and then once the desktop is up I have to type the following in a terminal.

sudo ifdown ath0
sudo ifup ath0

Just doing the last line is not enough. I can also hit the activate button in the System Settings --> Network --> Wifi page to get the card started. Incidentally if I sudo iwconfig before the ifup and ifdown I get the follwoing (edited a little):

ath0      IEEE 802.11  ESSID:"Falcon"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:restricted
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any suggestions what I should do? I've been trolling the forum and plenty of people seem to have similar problems but none of their solutions seem to fit or work.

Cheers,

kmacc

---

### Post by Lambert on 2006-01-13
Not knowing what you've tried, some pcmcia cards start at hotplug and not networking during bootup. This doesn't always work but you can try this.

remove the auto ath0 line and under the map eth0 line add map ath0

---

### Post by jasmuz on 2006-01-13
Does your card (same as mine) load via Ndiswrapper at boot?

---

### Post by kmacc on 2006-01-13
Hi Lambert,

Unfortunately your tip did not do much. My card is PCI and I'm using the madwifi drivers which came with kubuntu.

After the last boot up I did the following:

lsmod | grep ath

Here's the result:

ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
wlan                  120988  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample

I've really just been flailing around tweaking all sorts of things. I'm sorry if some of my experimenting might seem a little disconnected.

Cheers,

tandk.

---

### Post by kmacc on 2006-01-13
I've changed my interfaces file back to how I originally posted it.

This time after boot up I did the following:

tandk@familyRoom:~$ sudo ifup ath0
Password:
There is already a pid file /var/run/dhclient.ath0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:13:46:74:51:85
Sending on   LPF/ath0/00:13:46:74:51:85
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.100 -- renewal in 290285 seconds.
tandk@familyRoom:~$

Does this mean anything to anyone? Notice that the network came up correctly at the end.

kmacc

---

### Post by kmacc on 2006-01-14
I just booted up again and tried:

sudo ifdown ath0

It replied:

ifdown: interface ath0 not configured

I'm pretty sure this isn't what it said before but never mind.

My interfaces file still looks like it did in my first post of this thread.

Cheers,

tandk

---

### Post by kmacc on 2006-01-14
This morning when I booted ifup just blanked on me so I had to do an ifdown and then an ifup. This brought the network up.

I'm pretty much stumped. Web searching only finds stuff I've tried.

Can anyone tell me which log file I should look at to get a better idea of what goes on at boot?

Cheers,

kmacc

---

### Post by NTolerance on 2006-01-14
I'm getting this exact same issue.  Here's my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto ath0

iface ath0 inet dhcp
wireless-essid text
wireless-channel 1
wireless-key hex
wireless-ap macaddress
```

---

