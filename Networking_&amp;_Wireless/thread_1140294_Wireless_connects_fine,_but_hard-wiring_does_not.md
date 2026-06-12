---
title: "Wireless connects fine, but hard-wiring does not?"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by MikeBrown on 2009-04-27
I recently upgraded to Ubuntu 9.04 (which is AWESOME so far) from 8.10 and was over at my girlfriend's house trying to get online in the new boot to check email, etc. 

She has a hard-wired Internet connection which is not connected to any sort of wireless transmitter, and that is what I was trying to connect with. 

I could not for the life of me get it to connect, but when I am at work both the wireless and wired connections work fine. 

Is there something I'm overlooking?

Any help would be much appreciated! Thanks!

---

### Post by rrojas on 2009-04-27
> **MikeBrown said:**
> I recently upgraded to Ubuntu 9.04 (which is AWESOME so far) from 8.10 and was over at my girlfriend's house trying to get online in the new boot to check email, etc. 

She has a hard-wired Internet connection which is not connected to any sort of wireless transmitter, and that is what I was trying to connect with. 

I could not for the life of me get it to connect, but when I am at work both the wireless and wired connections work fine. 

Is there something I'm overlooking?

Any help would be much appreciated! Thanks!

What do you mean by "hard-wired Internet connection?" And are you connecting to a router or directly to the cable modem?

---

### Post by MikeBrown on 2009-04-27
It's a connection provided by the internet company my girlfriend uses. 

Cable comes out of the wall, goes into modem. Ethernet cable comes out of the modem, goes into computer.

---

### Post by coffeecat on 2009-04-27
Is this a cable connection rather than adsl over a telephone line? It sounds like it. I have no personal experience of cable internet, but I believe you have to "register" the nic MAC. So, if you change the computer connected to the modem, the MAC changes and you can't connect. You get round this, I believe, by using a router between the modem and your computers. You have to "register" (or whatever) the MAC of the outward facing port of the router, but once you've done this you can connect any computer (and any OS) to an inward port on the router and you should be fine.

Or something like that. Why not post the name of your girlfriend's internet company and, with luck, someone on the forum might know the details?

One last thought. I have a dim memory (not unusual at my age :wink: ) of someone needing to reboot a cable modem between switching computers. Perhaps that gets round the MAC issue - I don't know.

---

### Post by MikeBrown on 2009-04-27
I have had to reboot the modem when unplugging her laptop and plugging mine in. It connects automatically when I use my Windows boot, but for some reason it won't with my Ubuntu. 

I will have to look up her cable provider, but I don't have much more info about this problem at the moment. 

Clever joke by the way, i made an audible "rim shot" when I read that

//I'm a dork

---

### Post by rrojas on 2009-04-27
With the Windows boot and your laptop connected to the cable modem with internet access, what do you get when you run

```
netstat -nr
```

What do you get when you run the same command with your Ubuntu boot and connected to the cable modem?

---

### Post by evermooingcow on 2009-04-27
When changing the device connected to the modem your ISP has to register your new MAC address so you have to wait or power cycle the modem to get them to register.

Another option is to clone your MAC address. Look up the MAC address of the PC that is normally connected to the modem. Set the MAC address of your laptop's wired interface using

sudo ifconfig eth0 hw ether xxxxxxxxxxxx
Where eth0 is your wired NIC

---

### Post by bwilhiteforex on 2009-04-27
VERY STRANGE!!....I'm having a very similar problem.  If I use a wireless USB adapter, I can connect.  But anything that connects directly into my router via Cat-5 does not, and for me this is not contained to just ubuntu 9.04 but also 8.04 and 8.01.  I'm not sure what is going on, but any insight would be welcome.  (I'll grab the link for my own thread, but this is disturbingly similar)


EDIT: Here's the link to other thread

[http://ubuntuforums.org/showthread.php?t=1140606](http://ubuntuforums.org/showthread.php?t=1140606)

---

