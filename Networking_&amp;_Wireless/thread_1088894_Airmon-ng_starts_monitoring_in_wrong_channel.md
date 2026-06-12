---
title: "Airmon-ng starts monitoring in wrong channel"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by Sam__ on 2009-03-06
Hello,

I am having problems when running airmon-ng with my Linksys Wireless-G, running Broadcom 43.
I have checked up whether it works with aircrack, and it does.
Here is what I get:
```
sam@sam-desk:~$ sudo airmon-ng stop wlan0
[sudo] password for sam: 


Interface	Chipset		Driver

wlan0		Broadcom 43xx	b43 - [phy0]
				(monitor mode disabled)
mon0		Broadcom 43xx	b43 - [phy0]

sam@sam-desk:~$ sudo airmon-ng stop mon0


Interface	Chipset		Driver

wlan0		Broadcom 43xx	b43 - [phy0]
mon0		Broadcom 43xx	b43 - [phy0] (removed)

sam@sam-desk:~$ sudo airmon-ng start wlan0 6


Interface	Chipset		Driver

wlan0		Broadcom 43xx	b43 - [phy0]
				(monitor mode enabled on mon0)


sam@sam-desk:~$ iwlist wlan0 channel
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.412 GHz (Channel 1)

sam@sam-desk:~$ iwlist mon0 channel
mon0      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.412 GHz (Channel 1)

sam@sam-desk:~$ 

```

Could also be worth mentioning that I do [use this driver](http://bildr.no/view/360705) for the wireless network card.

Thanks :)

---

### Post by terazen on 2009-03-06
I run this and it works for me.
```
sudo airodump-ng wlan0 --channel 6
```

---

### Post by manou on 2009-07-01
Hola,

A mi me pasa algo parecido que al amigo que inicio el post, 

manou@nomada:~$ sudo aireplay-ng -1 0 -e WLAN_57 -a 00:1A:2B:06:29:05 -h 00:18:de:11:cd:4a mon0
14:05:51  Waiting for beacon frame (BSSID: 00:1A:2B:06:29:05) on channel 11
14:05:51  mon0 is on channel 11, but the AP uses channel 3

y la opción --channel me da el siguiente error.

wlan0		Intel 3945ABG	iwl3945 - [phy0]/usr/sbin/airmon-ng: line 447: [: --channel: se esperaba expresión de tipo entero

				(monitor mode enabled on mon0)


Alguien sabe algo al respecto ?

Gracias por la atención,
·_- manou

Que todos los seres sean felices
Que todos los seres Amen

---

### Post by Aitaix on 2011-03-10
**Translated from ****manou**



Hello,

 Happens to me something like that friend who started the post,

 manou @ nomad: ~ $ sudo aireplay-ng -1 0-e WLAN_57-a 00:1 A: 2B: 6:29:05-h 00:18:: 11: cd: 4a mon0
 14:05:51 Waiting for beacon frame (BSSID: 00:1 A: 2B: 6:29:05) on channel 11
 14:05:51 mon0 is on channel 11, But The AP uses channel 3

 and the - channel I get this error.

 Intel 3945ABG wlan0 iwl3945 - [phy0] / usr / sbin / airmon-ng: line 447: [: - channel: expected integer expression

 (monitor mode enabled on mon0)


 Anyone know anything about it?

 Thanks for caring,
 · _-manou

 May all beings be happy
 Amen May all beings

---

### Post by Aitaix on 2011-03-10
The interface MAC (00:27:10:6A:15:EC) doesn't match the specified MAC (-h).
    ifconfig mon0 hw ether 00:11:22:33:44:55
11:35:44  Waiting for beacon frame (BSSID: 18:B1:0D:E6:97:61) on channel -1
11:35:44  mon0 is on channel -1, but the AP uses channel 11
dan@Terra:~$ sudo airodump-ng wlan0 --channel 11


I get this....how can I get it to monitor channel 11?

---

### Post by bbaaxx on 2011-06-22
Got the exact same problem with a Broadcom BCM4313[14e4:4727] NIC w/ brcm80211 driver on a laptop running 10.10. airodump-ng captures just fine but all aireplay-ng commands just tells me that the *monX* interface is on the non-existing channel **-1**

I've already tried several different things including the following:

[LIST]
[*]Tried all forms of the *airmon-ng* command to force a channel to the *monX* interface.
[*]Tried with iwconfig to force the channel change.
[*]Tried running with only essential services/drivers.
[*]Enabling secondary *monX* interfaces.
[/LIST]

It looks to me as some sort of bug that sets the channel in -1 but it may not be too hard to track where is it happening since it seems to affect several different NIC's, so if this thread remains alive please include your NIC model/driver.


:( :( :(

---

### Post by blackløtus on 2011-06-23
first off all, have all you tried:

> sudo airmon-ng start <interface> (type iwconfig for see the name)
sudo airodump-ng <options> **-c <chanel>** mon* (name of the monitor that you enabled whit airmon-ng, type iwconfig for see the exact name)

whit this you can enable the airodump in the chanel that you will attack

---

### Post by RoflHaxBbq on 2011-06-24
bbaaxx, you need to patch your drivers.

As for OP, you may be able to get away without specifying a channel.
It will channel jump, but that may just be better than being in the wrong channel totally, amiright?

Put the card into monitor mode.
sudo airmon-ng start wlan0

Find the info of the AP you want to attack.
sudo aireplay-ng -9 mon0

This set airodump-ng to capture packets. Make sure you specify the channel of the AP with -c.

;)

---

