---
title: "Sooo close to accessing my wireless network"
date: 2006-04-02
forum: Networking &amp; Wireless
---

### Post by Jonhoo on 2006-04-02
Allright, pretty big Linux-newbie speaking :P

First of all, I just figured out I actually like tinkering around in Linux :)

Now, to my problem..

I have a Compaq Armada E500 laptop with a Belkin F5D7010 (rev 03 with Broadcom BCM4306 chip) wireless PCMCIA card..

I have followed all of the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?p=885268"), and have got no errors at all.. The network light on my F5D7010 is green (Not the power light strangely, only the traffic light which is on continously..) , and I can configure the device in the networking manager, the only problem is that the card doesn't find any networks.. :( I have SSID broadcasting enabled on my router which is placed a bit under 10 feet from laptop with the card...

Even if I try to set the SSID through iwconfig, the SSID simply says 'off/any' when I run iwconfig.. 

```
iwlist wlan0 scan
```

produces:

```
wlan0          No scan results
```

Does anyone know what may cause this to happen?

Appreciate the help :)
Jon

---

### Post by spd106 on 2006-04-02
The instructions you followed in the link above are for Hoary (5.04), rather than Breezy (5.10). So changing the radiostate to 0 should not be needed.

However as the cards lights have come on I suppose this is not where the problem lies. Could you perhaps try a different (driver) bcmwl5.inf?

Maybe ndiswrapper doesn't work so well on your machine. You could try building a newer version. Have a look in the wiki for useful guides.

---

### Post by Jonhoo on 2006-04-02
Hmm, yeah.. I think the files were set to RadioState 0 by default...

To use another driver, all I need to do is:
```

ndiswrapper -e bcmwl5
ndiswrapper -i bcmwl5.inf <-- Where this is the new driver

```
right?

The ndiswrapper is the newest version through apt-get at least... 
ndiswrapper-utils is version 1.1-4ubuntu2


Dunno which version the ndiswrapper itself is.. How do I update it?

Thanks for helping :)
Jon

---

### Post by Jonhoo on 2006-04-03
Anyone?

I feel the solution is very close, but I'm not there yet :(

---

