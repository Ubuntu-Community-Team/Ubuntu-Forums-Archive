---
title: "sniff the local accesspoints and connecting using only a given key"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by jzoom on 2008-12-16
I have the following scenario, yet haven't seen anything in my searches to give me a resolution.

The basic concept: I have the encryption key, but don't know which wireless ssid it goes to.


I want to be able to install a new system at, for example, "grandma's house". She only knows the wireless "key" that was written down for her. She doesn't know if it is wep, psk, she doesn't know if its 64 bit 128 bit, Finally, she doesn't know what the ssid is.

Is there anything that I can sniff all the available wireless networks, try every key type and find and store the network that the "key" matches?

I have tried a number of different configs with wpa_supplicant, 
parsing through iwconfig output then generating an interfaces file and looping through each type etc etc...but none seem to work.

any ideas?
Thanks
JH

---

### Post by nixscripter on 2008-12-16
This Terminal command will show all networks which broadcast an SSID:

```
sudo iwlist **interface** scan
```

iwconfig was the right idea; iwlist is another utility for controlling parameters.

Hope this helps.

---

### Post by jzoom on 2008-12-18
So the only real way to do this is use iwlist, parse the buffered response, then take all the WEP and WPA accesspoints, generate a new interfaces file, then run /etc/init.d/networking start then ping ~ [www.zzz.com](www.zzz.com) and see if the key works.

If not, then do the same for the next wep or wap?
I thought there moight be something a bit more elegant. ;-)

bear in mind, I'm trying to automate this within a C setup routine.

---

### Post by razy60 on 2008-12-18
What router (make/model) are you trying to get the ssid for?
Or is it a shared/communal network,

Raz

---

### Post by jzoom on 2008-12-18
Raz,
I'm tasked with a module ... setup.c let's say, and this will be embedded in a system delivered to an end users home. The end user only knows the Key which is written on a scrap piece of paper. no knowledge of IP, router whatever. Just imagine "grandma" I need to find which router the key matches, and don't know the make model... nothing.

---

### Post by razy60 on 2008-12-18
now thats a task that ain't gonna be easy.
from what I've read on here there are problems when trying to connect to hidden networks and thats with people having the ssid, so only having the access code is going to be a (cant think of a good word but complicated don't cover it).
Although there are a couple of useful looking tools in add remove programs that may stand up to some adaption.

Raz

---

