---
title: "Rhythmbox does not play my internetradio"
date: 2010-09-09
forum: Multimedia Software
---

### Post by Alver on 2010-09-09
I run Ubuntu 10.04.1 64 bits dual boot with W7 64 b on a Toshiba L505-10M  6GB ram. All I want to do succeeds without problems, except listening to Klara Continuo (Belgian internetradio). I will have to bring in [http://mp3.streampower.be/klaracontinuo-high.mp3](http://mp3.streampower.be/klaracontinuo-high.mp3) when  I create a new radio in Rhythmbox. When I press the green arrow "Play" then the system starts to buffer (bottom orange bar moves) and the radio plays, but ... only a few seconds. Then  buffering starts again and again, I hear sound for a few seconds until everything fails. This goes on for 6 or 7 times and then Rhythmbox stops completely. Under Windows 7, I can easily listen to radio. Can anyone give me some advice on how to tackle this ? Thx for a possible clue. 

Alver

---

### Post by rivenathos on 2010-09-09
I have Ubuntu 10.04.1 64-bits installed as well.  However, when I added that radio stream to my Rhythmbox, it played flawlessly with absolutely no buffering.  The buffering may be the result of a slow Internet connection at your particular location at this time.  Rebooting your Internet connection (DSL or cable modem) might help if you have a dynamic IP.  I hope this helps.

---

### Post by Alver on 2010-09-09
> **rivenathos said:**
> I have Ubuntu 10.04.1 64-bits installed as well.  However, when I added that radio stream to my Rhythmbox, it played flawlessly with absolutely no buffering.  The buffering may be the result of a slow Internet connection at your particular location at this time.  Rebooting your Internet connection (DSL or cable modem) might help if you have a dynamic IP.  I hope this helps.
Since I run a dual boot with W7, I tried the same internetradio in W7 of course. There the radio plays without hick-up in Firefox, using Windows MediaPlayer.

Alver

---

### Post by rivenathos on 2010-09-09
Are you connecting to the Internet via Ethernet (wired) or wi-fi (wireless).  Also, is the buffering only on this one station or all stations?

---

### Post by Alver on 2010-09-09
> **rivenathos said:**
> Are you connecting to the Internet via Ethernet (wired) or wi-fi (wireless).  Also, is the buffering only on this one station or all stations?
I have a functioning wireless connection (the applet tells me I have a 54 Mb/s connection). I have not tried other radiostations yet, but I will try some right away and come back on it.

Alver

---

### Post by Alver on 2010-09-09
> **Alver said:**
> I have a functioning wireless connection (the applet tells me I have a 54 Mb/s connection). I have not tried other radiostations yet, but I will try some right away and come back on it.

Alver
I tried several staions randomly chosen. These are the results:
1) NRK Alltid Klassik (Norway): same phenomenon, no improvement
2) Absolute Classic Rock (Modem): Flawless reception
3) Absolute Classic Rock (Broadband):  same phenomenon, no improvement
4) Absolute Radio (Modem): Flawless reception
5) Absolute Radio (Broadband): same phenomenon, no improvement
6) WKNC 88.1 FM (NC State) Low Quality: Flawless reception
7) WKNC 88.1 FM (NC State) High Quality: Buffering starts, stutters and finally, no reception.

Alver

---

### Post by rivenathos on 2010-09-09
I already see a pattern here.  All of the broadband stations have problems while all the modem stations work flawlessly.  This appears to now be a bandwith issue.

There is a distinct possibility that your wi-fi may not be working at its full speed.  Have you tried doing this same experiment while connected to Ethernet?  If you are connected to Ethernet and everything works great, then that suggests your wi-fi is not at full speed.

You may need to post your lspci focusing on your wireless adapter card.  There may be a setting in some file that is limiting your wi-fi to either 1 or 11 versus 54.  I am not a wi-fi guy, but I have seen this issue crop up previously.

Hopefully, this points you in the right direction.

Edit:  This might work, but please research before you try it...

sudo iwconfig eth1 rate 54M

---

### Post by ron999 on 2010-09-09
@ Alver
Have you tried those radio stations using a different player, such as vlc or mplayer?

Like this:-
```
vlc http://mp3.streampower.be/klaracontinuo-high.mp3
```
And this:-
```
mplayer http://mp3.streampower.be/klaracontinuo-high.mp3
```

---

### Post by Alver on 2010-09-09
> **rivenathos said:**
> I already see a pattern here.  All of the broadband stations have problems while all the modem stations work flawlessly.  This appears to now be a bandwith issue.

There is a distinct possibility that your wi-fi may not be working at its full speed.  Have you tried doing this same experiment while connected to Ethernet?  If you are connected to Ethernet and everything works great, then that suggests your wi-fi is not at full speed.

You may need to post your lspci focusing on your wireless adapter card.  There may be a setting in some file that is limiting your wi-fi to either 1 or 11 versus 54.  I am not a wi-fi guy, but I have seen this issue crop up previously.

Hopefully, this points you in the right direction.

Edit:  This might work, but please research before you try it...

sudo iwconfig eth1 rate 54M

Thank you for your elaborate reply. I too noticed the pattern but ... if I switch to W7 (remember I can dual boot) and use Windows Media Player all randomly picked radio stations play well (I have not tried the ones from my Ubuntu test). I'm inclined to believe that indeed my nic does not work to its full potential in U 10.04.1. I will do some more digging into this, follow the suggestions of the other learned members and come back asap.


Alver

---

### Post by Alver on 2010-09-09
> **ron999 said:**
> @ Alver
Have you tried those radio stations using a different player, such as vlc or mplayer?

Like this:-
```
vlc http://mp3.streampower.be/klaracontinuo-high.mp3
```And this:-
```
mplayer http://mp3.streampower.be/klaracontinuo-high.mp3
```
I have tried vlc player but to no avail. I keep getting stuttering music. Please see also my terminal output file.

Thx 

Alver

---

### Post by ron999 on 2010-09-09
Yes, I can see that vlc finds it difficult.
It seems that the problem is your internet connection, not Rhythmbox.

---

### Post by Alver on 2010-09-10
> **ron999 said:**
> Yes, I can see that vlc finds it difficult.
It seems that the problem is your internet connection, not Rhythmbox.
I'm more & more convinced that my internet connection is working but in a "throthled" kind of mode. This is not very noticeable when perusing the internet or for e-mails but music is different matter. FYI in W7 my connection speed is also 54 Mb/s so it is probably another parameter, but which one?? Any thoughts??

Alver

---

### Post by Alver on 2010-09-10
> **ron999 said:**
> Yes, I can see that vlc finds it difficult.
It seems that the problem is your internet connection, not Rhythmbox.
 I ran the lshw command in a terminal and this is what I get for my nic:
 *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:14:00.0
                logical name: wlan0
                version: 10
                serial: 70:1a:04:37:37:56
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=192.168.1.6 latency=0 multicast=yes wireless=802.11bg
                resources: irq:19 ioport:5000(size=256) memory:f2200000-f2203fff

It says width: 32 bits, has this to do with the architecture? I'm running U 10.04 64 bits. is this a possible conflict zone?

Alver

---

