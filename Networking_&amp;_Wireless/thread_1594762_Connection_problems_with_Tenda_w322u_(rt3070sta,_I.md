---
title: "Connection problems with Tenda w322u (rt3070sta, I think) on 10.04"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by foolfodder on 2010-10-12
Firstly, I'm a noob, I've tried to follow some of the advice that I've seen on these boards, but it's not worked out so far.

My Tenda USB dongle keeps asking for a password but never actually connects. The inbuilt Intel PRO wireless card connects fine.

I've tried blacklisting drivers in /etc/modprobe.d/blacklist.conf.

Adding:
[FONT=monospace]
[/FONT]blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

Results in no change.

Adding: blacklist rt2870sta results in the dongle not trying to connect at all.

> iwconfig wlan1
wlan1     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:24:17:EE:B1:A9   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-79 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Bit of time passes...

Okay I just tried to install the rt3070sta driver off the Ralink site. Now the network manager shows the device as not ready and iwconfig has the following:

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So it's not wlan1 any more, it's now at ra0, not sure if that should make a difference though. Not really sure what I'm doing or what to try next. Any advice appreciated.

---

### Post by foolfodder on 2010-10-14
I looked in my /etc/Wireless/RT3070STA/RT3070STA.dat file* and found this:

Wapiifname=ra0

and changed it for

Wapiifname=wlan1

But there's no change, iwconfig still shows it as ra0.

* - this file didn't actually exist in the file that I downloaded to install the driver, but there was one called RT2870STA.dat, I just copied that one and renamed it.

---

### Post by Vaevictus on 2010-10-21
Hi,

I have a Tenda W322u, running on XBMC (ubuntu 10 2.6.32-25-generic
kernel)

Followed every post on the forum already and just cannot get the thing to connect either, blacklisting, using the dat file etc. 

Convinced I will have to wait to the next major release of ubuntu for this to be fixed.

Every time I give linux a new try some device always gives me big headaches :(

---

### Post by Vaevictus on 2010-10-22
Finally got my Tenda Wireless W322U stick working on ubuntu 10.

I think the problem was that the 2870 drivers were being loaded for it instead of the 3370sta drivers.

Here is how I did it:
add:
blacklist rt2870sta
to the end of your /etc/modprobe.d/blacklist.conf

This stops the rt2870 driver from loading.

Download and extract the DPO_RT3370_LinuxSTA_V2.4.0.1_20100831.tgz
file from the ralinktech website

Extract, configure /os/linux/config.mk file and enable the WPA SUPPLICANT stuff (mentioned in the readme for the driver)

make
make install

reboot

now the wireless card should no longer be named wlan0 it should be ra0.

"lsmod | grep rt" should yield the following:
rt3370sta             584549  1

this is good as it shows the new driver we have compiled has been used.

now you need to get this card to connect to your wireless.
assuming the network is open:
ifconfig ra0 up
iwconfig ra0 essid myessidname
dhclient ra0

in a few seconds you should have an IP address

now dont bother with the dat file nonsense that this ralink driver apparently needs in /etc/Wireless, just use iwconfig and the /etc/network/interfaces file. 

Hope it helps someone out there

---

### Post by DitchingMS on 2010-10-25
> **Vaevictus said:**
> Finally got my Tenda Wireless W322U stick working on ubuntu 10.

I think the problem was that the 2870 drivers were being loaded for it instead of the 3370sta drivers.

Here is how I did it:
add:
blacklist rt2870sta
to the end of your /etc/modprobe.d/blacklist.conf

This stops the rt2870 driver from loading.

Download and extract the DPO_RT3370_LinuxSTA_V2.4.0.1_20100831.tgz
file from the ralinktech website

Extract, configure /os/linux/config.mk file and enable the WPA SUPPLICANT stuff (mentioned in the readme for the driver)

make
make install

reboot

now the wireless card should no longer be named wlan0 it should be ra0.

"lsmod | grep rt" should yield the following:
rt3370sta             584549  1

this is good as it shows the new driver we have compiled has been used.

now you need to get this card to connect to your wireless.
assuming the network is open:
ifconfig ra0 up
iwconfig ra0 essid myessidname
dhclient ra0

in a few seconds you should have an IP address

now dont bother with the dat file nonsense that this ralink driver apparently needs in /etc/Wireless, just use iwconfig and the /etc/network/interfaces file. 

Hope it helps someone out there

Thanks but I'm a complete noob and new to the terminal etc. I have downloaded what I believe is the file you mention from ralink and have unzipped it to a private folder. I have also found >  /etc/modprobe.d/blacklist.conf  and added >  blacklist rt2870sta
to the end . However I am now stuck and having opened the download it doesn't make any sense to me at all. I'd be so grateful if you could spell it out from scratch as it seems like you know your way around.

Thanks!

---

