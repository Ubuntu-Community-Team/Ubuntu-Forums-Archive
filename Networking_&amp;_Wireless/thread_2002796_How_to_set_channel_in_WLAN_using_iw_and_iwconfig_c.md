---
title: "How to set channel in WLAN using iw and iwconfig command"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by omega341991 on 2012-06-13
how will i GET the correct channel has been set using command
```
iw phy phy0 set channel 11 HT20 ?

```

and what is the use of the command 

```
iw dev wlan0 set channel 11 HT20
``` when there is another command
```
iwconfig wlan0 channel 11
```

---

### Post by poolet on 2012-06-13
Depending on your card and drivers, you may have the option to set the essid to the special value “any”. In this case, your card will pick the first available access point. This is called promiscuous mode.
You also may need to set the mode to be used by your wireless card. This depends on your network topology. You may have a central access point to which all of the other devices connect, or you may have an ad hoc wireless network, where all of the devices communicate as peers. You may want to have your computer act as an access point. If so, you can set the mode to master using iwconfig. Or, you simply may want to sniff what's happening around you. You can set other parameters, but you should consider doing so only if you have a really good reason. You can also do so by set the mode to monitor and passively monitor all packets on frequency to which your card is set. You can set the frequency, or channel, by running:

```
sudo iwconfig wlan0 freq 2.422G
```Or by running:

```
sudo iwconfig wlan0 channel 3 (or what ever play with the numbers)
```If you want to get specific statistics against a peer you station is communicating with you can use the following: 

```
sudo iw dev wlan1 station get <peer-MAC-address>
```There are several modes supported. The modes supported are:

    monitor
    managed [also station]
    wds
    mesh [also mp]
    ibss [also adhoc] 

For example to add a monitor interface:

```
iw phy phy0 interface add moni0 type monitor
```where you can replace monitor by anything else and moni0 by the interface name, and need to replace phy0 by the PHY name for your hardware (usually phy0 will be correct unless you hotplugged or reloaded any modules.) If your udev is configured incorrectly, the newly created virtual interface may be renamed by it right away, use ip link to list all interfaces.

Note that in case you want to monitor 802.11n you will need to specify channel width (20 or 20/40MHz) and in case of 20/40MHz if the upper or lower channel is being used. To do so you would use:

```
iw dev <devname> set freq <freq> [HT20|HT40+|HT40-]
```or

```
iw phy <phyname> set freq <freq> [HT20|HT40+|HT40-]
```You can also specify channel instead of frequency:

```
iw phy <phyname> set channel <channel> [HT20|HT40+|HT40-]
iw dev <devname> set channel <channel> [HT20|HT40+|HT40-]
```To create a new managed mode interface you would use:

```
iw phy phy0 interface add wlan10 type managed
```Note that the interface is automatically put into AP mode when using hostapd. 

::**NOTE**::It took me 5 seconds to find all these information's!!! Just search a little bit google has everything!!! 

::**Source**::[http://linuxwireless.org/en/users/Documentation/iw](http://linuxwireless.org/en/users/Documentation/iw)

---

### Post by omega341991 on 2012-06-13
i also found all these thank you.
What i wanted to know is still not answered (please read my post again ) and try to answer the questions posted and not some copied document from a site containing a lot of irrelevant data
Hope you can give me a more precise answer the next time

---

### Post by poolet on 2012-06-14
There is no precise answer!! The link is covered all that you refer(according to your questions)!! As for copy - paste information.."Yes" I often do that,  but guess what why?? Because there are some kind of people who are so bored to right click on a link and read bunch of information.!!!  At the end, if you want a specific detail please give a specific details of what you are trying to do, if you try any malicious ways you are in the wrong place!!

---

### Post by omega341991 on 2012-06-14
malicious?hmm...
anyways leave it
do u know how to set the source address using **iw **command?

---

