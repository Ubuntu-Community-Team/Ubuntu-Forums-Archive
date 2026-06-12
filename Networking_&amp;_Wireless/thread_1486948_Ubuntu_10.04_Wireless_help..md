---
title: "Ubuntu 10.04 Wireless help."
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Ivan 992 on 2010-05-18
Hello I am totaly new on this forum,My english is not realy good.......
I have a problem with my ubuntu 10.04 I running it on my laptop in duall boot with windows xp professional witch is Intel Fujitsu Siemens with Atheros ar5007eg wireless card,
I have tried to conect to wlan with my card but it is disebled, I have tried so many things and dont know what to do any more, so I came here to ask experts becasuse I realy dont know what to do any more.........

This is what I got when write this in terminal

ivan@ivan-laptop:~$ lspci | grep Network
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

ivan@ivan-laptop:~$ iwconfig
lo no wireless extensions.

wlan0 IEEE 802.11bg ESSID: off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=off 
Retry long limit:7 RTS thr: off Fragment thr: off
Power Management: off

eth0 no wireless extensions.

And this.........

ivan@ivan-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

I found on internet theat this error 132 is actualy a bug theat wont let my car to go up........

This whas like solution for theat bug but theat didnt help either.......

rmmod ath9k
rfkill block all
rfkill unblock all
modprobe ath9k
rfkill unblock all

So please can someone help me.........

---

### Post by Megaptera on 2010-05-18
Hi,
Is this solution any help?

How To: Wireless on a Fujitsu Siemens Li 2727 notebook

[http://ubuntuforums.org/showthread.php?t=986288](http://ubuntuforums.org/showthread.php?t=986288)

---

### Post by chili555 on 2010-05-18
I noticed this:> wlan0 IEEE 802.11bg ESSID: off/any
Mode:Managed Access Point: Not-Associated [COLOR="Red"]Tx-Power=off[/COLOR]
Retry long limit:7 RTS thr: off Fragment thr: off
Power Management: offDoes it improve if you do:```
sudo iwconfig wlan0 txpower 15
```If this produdes an error, try txpower 12 and 10, etc. until it sticks without error. Then can you do:```
sudo iwlist wlan0 scan
```If you get scan results, can you click the Network Manager icon and connect?

Your English is fine; we understand you well.

---

### Post by Ivan 992 on 2010-05-18
Thanks to all I l go to try it out........
To se will it work.......

---

### Post by Ivan 992 on 2010-05-18
Ok I have tried to go with theat but I got this message......

ivan@ivan-laptop:~$ sudo iwconfig wlan0 txpower 15

ivan@ivan-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

ivan@ivan-laptop:~$ 

Is to get online with the cable only solution to get this thing fixed?

---

### Post by chili555 on 2010-05-18
What does this tell us?```
rfkill list all
dmesg | grep -e wlan -e ath
```Thanks.

---

### Post by Ivan 992 on 2010-05-19
It gives me this message.......

ivan@ivan-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
ivan@ivan-laptop:~$ dmesg | grep -e wlan -e ath
[    0.453569] device-mapper: [COLOR="Red"]multipath[/COLOR]: version 1.1.0 loaded
[    0.453573] device-mapper: [COLOR="Red"]multipath[/COLOR] round-robin: version 1.0.0 loaded
[   10.848251] [COLOR="Red"]ath[/COLOR]5k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.848266] [COLOR="Red"]ath[/COLOR]5k 0000:02:00.0: setting latency timer to 64
[   10.848305] [COLOR="Red"]ath[/COLOR]5k 0000:02:00.0: registered as 'phy0'
[   11.344261] [COLOR="Red"]ath[/COLOR]: EEPROM regdomain: 0x30
[   11.344264] [COLOR="Red"]ath[/COLOR]: EEPROM indicates we should expect a direct regpair map
[   11.344267] [COLOR="Red"]ath[/COLOR]: Country alpha2 being used: AM
[   11.344269] [COLOR="Red"]ath[/COLOR]: Regpair used: 0x30
[   11.350610] [COLOR="Red"]ath[/COLOR]5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   12.370103] ADDRCONF(NETDEV_UP): wlan0<: link is not ready

This was realy red........

---

### Post by chili555 on 2010-05-19
> Hard blocked: yesThat usually means there is a wireless switch on your laptop that is moved to 'Off.' Can you find it and push it on?

---

### Post by Ivan 992 on 2010-05-19
At my laptop it is combination of FN+F1.......
Did you meen theat.......
I will give it a try....

---

### Post by Ivan 992 on 2010-05-19
I tried theat, and all I got was the same message.......

---

### Post by chili555 on 2010-05-19
I saw this: [http://www.vleeuwen.net/2009/06/wireless-fix-on-amilo-running-ubuntu](http://www.vleeuwen.net/2009/06/wireless-fix-on-amilo-running-ubuntu)

Will you try the same fix? ```
sudo modprobe acer-wmi
rfkill list all
```What model of Fujitsu is it?

---

### Post by Ivan 992 on 2010-05-19
The model is fujitsu siemens v5535......

I didnt try your last solution I will try it now.....

Tnx for helping me......

---

### Post by Ivan 992 on 2010-05-19
I got this message now....

ivan@ivan-laptop:~$ sudo modprobe acer-wmi
[sudo] password for ivan: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-21-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
ivan@ivan-laptop:~$ sudo modprobe acer-wmi

I dont know are my drivers are installed atleast for the wireless because I was not beeing online with ubuntu.......
Theas this mean anything......

---

### Post by Ivan 992 on 2010-05-20
Anyone??????

---

