---
title: "How can i limit my download speed. Sharing a friends internet"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2011-09-12
hi, i am sharing internet with a friend, the wireless router is sittin in there house. they get about 1mb sec download speed and i am trying to limit my download speeds over at my house to about 100kb max. so its quick and not like dial up at least. i notice through frostwire my downloads get up to about 300kbs so i limited it through frostwire to about 50kb but i am wanting to limit the whole internet if i can. thanks to any help

---

### Post by stinkeye on 2011-11-07
Hi slixz85,
I only just installed it and gave it a try but wondershaper seems to work.
The difference between Kilobytes and Kilobits  always confuses me but this
should give you the limit you want.
```
sudo wondershaper [COLOR="Red"]eth0[/COLOR] 800 80
```
[COLOR="red"]Your network interface.[/COLOR]

To set back unlimited
```
sudo wondershaper clear [COLOR="red"]eth0[/COLOR]
```

---

### Post by slixz85 on 2011-11-07
> **stinkeye said:**
> Hi slixz85,
I only just installed it and gave it a try but wondershaper seems to work.
The difference between Kilobytes and Kilobits  always confuses me but this
should give you the limit you want.
```
sudo wondershaper [COLOR="Red"]eth0[/COLOR] 800 80
```
[COLOR="red"]Your network interface.[/COLOR]

To set back unlimited
```
sudo wondershaper clear [COLOR="red"]eth0[/COLOR]
```

thanks i am about to try this now. I am sure my friends laptop would have to have this installed on their computer for it too affect them right? just wouldn't want this program to somehow cap their router that they have sitting at their house also...

---

### Post by stinkeye on 2011-11-07
> **slixz85 said:**
> thanks i am about to try this now. I am sure my friends laptop would have to have this installed on their computer for it too affect them right? just wouldn't want this program to somehow cap their router that they have sitting at their house also...
You only need it on the computer you want to limit the speed on.
It wont affect the router. It will just limit the speed on the computer it's installed on.
eth0 is usually the wired interface on your computer.
wlan0 is usually the wireless interface on your computer.
Click on the **network icon > connection information** to check the interface your using.

KB = Kilobytes
Kb = Kilobits

 1 Kilobyte &#8776; 8 Kilobits 

Wondershaper uses Kb/sec.

---

### Post by slixz85 on 2011-11-07
> **stinkeye said:**
> You only need it on the computer you want to limit the speed on.
It wont affect the router. It will just limit the speed on the computer it's installed on.
eth0 is usually the wired interface on your computer.
wlan0 is usually the wireless interface on your computer.
Click on the **network icon > connection information** to check the interface your using.

KB = Kilobytes
Kb = Kilobits

 1 Byte = 8 bits 

 KB/sec would be about 8 times faster than Kb/sec.

Wondershaper uses Kb/sec.

Thanks Alot man. it is pretty much doin what i want kinda. I ran a wifi speed test from [http://www.myspeedtestonline.com/wifi-networks.html](http://www.myspeedtestonline.com/wifi-networks.html) and it was much faster than i thought. it downloaded at about 3500 kb and 700 upload so i know it was affecting their speed probably. they have said it got a bit slow before. so i set it to what the default setup says of 500kb and 100kb upload and my download speeds after retrying the test only hit 310 kb tops for some reason, so all i gotta do is fiddle with it. thanks again

---

