---
title: "using 64bit WEP on ubuntu 10.4"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by fpache on 2010-05-28
My wireless router isn`t the youngest anymore, and the best it offers is 64bit WEP. I know it`s not the safest thing but I accept that.
However ubuntu 10.04 does not allow using 64bit WEP keys via the Network Manager popup dialogs. Choices are 128bit Key or 128bit pass phrase.
While I appreciate the sentiment of higher security standards, I still would like to keep using my key which worked perfectly fine on the same machine while using 8.04 (so its not a hardware issue)

What I am looking for is either

[LIST]
[*]a way to enable 64bit key entry in the Network Manager or
[*]the iwconfig command to sneak the key past the nice GUI
[/LIST]
much appreciated

---

### Post by purelinuxuser on 2010-05-28
Just use the "40/128-bit key" option.  It works for 64-bit keys too.

As for an iwconfig option, you could use
```
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid YOUR_ESSID key YOUR_WEPKEY channel YOUR_CHANNEL
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```
...but I think Network Manager is a lot easier :)

---

### Post by fpache on 2010-05-28
thanks a lot purelinuxuser

Meanwhile I took door 3: installed wicd and removed network manager :-)

between the two of us, I think we got all options covered

---

### Post by prscott1 on 2010-09-09
Hi - how did you remove the network manager?

---

### Post by I SHOULD COCO on 2010-09-16
I am struggling with WICD too 
Damn the ISP

COCO

---

### Post by Cris.P on 2010-12-15
I'm in 10.10 and I can't seem to get any WEP keys to work. I know its not really security but we have a few people who use the wireless connection. My RaLink 2600 MIMO chipset seems to work just fine with an open network though. Could  be the drivers are lacking WEP support.
I might just use MAC filtering over an open network. Won't stop a hacker but it would stop my neighbors from using my network.

---

