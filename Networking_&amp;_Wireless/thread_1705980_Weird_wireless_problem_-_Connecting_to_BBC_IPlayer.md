---
title: "Weird wireless problem - Connecting to BBC IPlayer kills Internet."
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by jock mackay on 2011-03-13
I am a newbie and have been fighting with this problem since I got my netbook with Ubuntu on it. Very simply, if I connect to BBC IPlayer wirelessly through my BT Home Hub, playback stops after about 15 seconds and contact with server is lost. I can play downloaded video files.
What is strange is that the internet functions normally using 1. Ethernet, 2. wireless through a friend's BT Home Hub, 3. BTFON, and 4. Windows 7.

The computer is a Dell Mini 10 with the Realtek 8188ce card, and I have downloaded the latest version of the drivers through the PPA. I have used 10.04 and am currently using 10.10 all with the same results.

I wonder if anyone out there can suggest a remedy for me.

---

### Post by ~Hinterland on 2011-03-13
That is strange, is it only IPlayer or any streaming (eg YouTube)?

---

### Post by jock mackay on 2011-03-13
> **~Hinterland said:**
> That is strange, is it only IPlayer or any streaming (eg YouTube)?
The same thing applies with the ITV equivalent of IPlayer, and also trying to play radio over the internet.

---

### Post by ~Hinterland on 2011-03-13
I was going to suggest trying the driver from Realtek instead, but as it works with your friend's BT hub, I'm not sure that would help (assuming they are the same hardware).
Sorry I can't be more help.

---

### Post by jock mackay on 2011-03-13
> **~Hinterland said:**
> I was going to suggest trying the driver from Realtek instead, but as it works with your friend's BT hub, I'm not sure that would help (assuming they are the same hardware).
Sorry I can't be more help.
Thanks for taking an interest. Like you, I do not think the driver is the issue. It might be the DNS server, but I do not know enough about that to make changes.

---

### Post by ~Hinterland on 2011-03-13
Edit: I was wrong about DNS (thinking it was set in router) you can change DNS servers by editing resolv.conf:
```
gksu gedit /etc/resolv.conf
```
To set DNS to Google's DNS add the lines:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Edit2: It can't be the DNS or you wouldn't be able to connect in the first place, or by ethernet..

You could check if the powersaving option is on: (in terminal)
```
iwconfig
```

if power management is on:
```
sudo iwconfig XXXX power off
```

**NB change XXXX to your wireless interface.**

---

### Post by jock mackay on 2011-03-14
> **~Hinterland said:**
> Edit: I was wrong about DNS (thinking it was set in router) you can change DNS servers by editing resolv.conf:
```
gksu gedit /etc/resolv.conf
```
To set DNS to Google's DNS add the lines:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Edit2: It can't be the DNS or you wouldn't be able to connect in the first place, or by ethernet..

You could check if the powersaving option is on: (in terminal)
```
iwconfig
```

if power management is on:
```
sudo iwconfig XXXX power off
```

**NB change XXXX to your wireless interface.**
I am game to give anything a try, but 1. I wonder whether powersave would be expected to activate close to the beginning of the wireless card's use 2. I used the IPlayer successfully through my friend's wireless BT Home Hub, and 3. Wireless works perfectly well on nearly all other sites.
My Wireless card is (Realtek) RTL8188CE. It that what you would like me to insert where your XXXXs are?

---

### Post by ~Hinterland on 2011-03-14
No, if you type iwconfig into the terminal you'll get something like:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"xxxxxxxx"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:xx:xx:xx:DD   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-14 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

for me wireless is on "wlan0" yours might be different.

---

### Post by jock mackay on 2011-03-15
I did as you suggested, but power setting did not change. Terminal output attached. Have I done something silly?
Version:1.0 StartHTML:0000000167 EndHTML:0000004318 StartFragment:0000000454 EndFragment:0000004302    	 	 	 	p { margin-bottom: 0.21cm; }  

 

 

 eleanor@eleanor-Inspiron-1018:~$ iwconfig
 

 lo        no wireless extensions.
 

 

 

 eth0      no wireless extensions.
 

 

 

 wlan0     802.11bgn  ESSID:"BTHomeHub2-KT6R"  Nickname:"rtl8192CE"
 

           Mode:Managed  Frequency=2.442 GHz  Access Point: 00:24:17:A5:96:B7    
 

           Bit Rate=65 Mb/s    
 

           Retry:on   RTS thr:off   Fragment thr:off
 

           Power Management period:0us  mode:All packets received
 

           Link Quality=86/100  Signal level=-55 dBm  Noise level=-113 dBm
 

           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
 

           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

 

 

 eleanor@eleanor-Inspiron-1018:~$ sudo iwconfig wlan0 power off
 

 [sudo] password for eleanor:  
 

 eleanor@eleanor-Inspiron-1018:~$ iwconfig
 

 lo        no wireless extensions.
 

 

 

 eth0      no wireless extensions.
 

 

 

 wlan0     802.11bgn  ESSID:"BTHomeHub2-KT6R"  Nickname:"rtl8192CE"
 

           Mode:Managed  Frequency=2.442 GHz  Access Point: 00:24:17:A5:96:B7    
 

           Bit Rate=65 Mb/s    
 

           Retry:on   RTS thr:off   Fragment thr:off
 

           Power Management period:0us  mode:All packets received
 

           Link Quality=81/100  Signal level=-59 dBm  Noise level=-110 dBm
 

           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
 

           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

 

 

 eleanor@eleanor-Inspiron-1018:~$

---

### Post by jock mackay on 2011-03-15
I am really coming round to the conclusion that this is an issue relating to my BT HOME HUB Version 2.
The reason I say that is that over the past few days I have successfully used the IPlayer wireless through BTFON, a BT Voyager Hub, and a BT HOME HUB version 1.5. I have started to look for a friend with a Version 2 hub like mine so that I can try using it to see how I get on.
I will let you know what happens.

---

