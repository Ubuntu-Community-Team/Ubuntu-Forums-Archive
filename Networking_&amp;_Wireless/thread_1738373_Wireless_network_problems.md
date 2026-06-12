---
title: "Wireless network problems"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by getafix28 on 2011-04-24
Hello everyone
On Monday I decided to try ubuntu for the first time I installed it on my computer. Two years ago I was running back track and I remembered that my friend taught me how to penetrate the network wep encryption. I decided to do an exercise to see if I can still remember how.
Before we begin I want to mention that the pc connected directly to the router i want to hack through a network cable. Network above is my own network. (May be problems because I connected directly as well?)

I shall start from the beginning and first of all the commands I use.

airmon-ng
    . Airmon-ng start (interface)
airodump-ng (interface)
airodump-ng-c (channel)-w1 - bssid (bssid) (interface)
aireplay-ng -1 0-a (bssid)-h (MAC of network card)-e "(essid)" (interface)
This command hangs most of the time all

aireplay-ng -3-b (bssid)-h (MAC of network card) (interface)
aircrack-ng-b (bssid) (file name-01.cap)
The last two commands I did not even get Mchiio I'm not enough to pass the fifth command at all ever

When I run airmon-ng i get only wlan0 and i get the following comment:

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

Name PID
992 avahi-daemon
993 avahi-daemon
1137 NetworkManager
1410 wpa_supplicant
1757 dhclient

I try to kill  the following processes but I can not ever because they always re-open ...

When I do

airmon-ng start wlan0
I  get the previous error of the processes that operate in addition he  informs me that wlan0 is there to standardize and added more mon0 where  it came from?
Interface Chipset Driver

wlan0 RTL8187 rtl8187 - [phy0]
                (Monitor mode enabled on mon1)
mon0 RTL8187 rtl8187 - [phy0]

When I try to do airodump-ng wlan0
He always impressed me

ioctl (SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead. Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.

But if I try to do the same command with mon0 it will start the scan.

When I try to capture data from the network through the command airodump-ng-c (channel)-w1 - bssid (bssid) (interface)
Finally I'm doing wlan 0 is write me back this error

ioctl (SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead. Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.
And if I try the same command in mon0 then it will start capturing data also ..
I'm  not so stupid and realized I need to work with the mon0 but I would be  more stupid if I do not try to understand why is that?
After all, in airmon-ng He recognized the wlan0! So how I got to mon0?
So in short I went with the mon0.
But now when I try to run the command
aireplay-ng -1 0-a (bssid)-h (MAC of network card)-e "(essid)" (interface)

I  always got the following error.
18:11:33 Waiting for beacon frame (BSSID: 00:21:63:9 C: 61: E3) on channel -1
18:11:33 mon0 is on channel -1, but the AP uses channel 6

Google  search it said that there may be interfering with the process and  should be done to kill but I tried it already and it does not work.
I  tried to change the channel via iwconfig but I guess I'm missing  something because I seem iwconfig channel 6 for example is going through  to the next line and not bring me any error. If it succeeded in something. But the channel continues to be -1

Please someone help me on my part to post here a guide to these problems that I do not know what to do.
Overall this first exercise I'm trying to

Thanks in advance for any help :-)

---

