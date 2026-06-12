---
title: "Sound is not working on my laptop"
date: 2012-04-21
forum: Multimedia Software
---

### Post by Zyxer22 on 2012-04-21
I'm using a Ubuntu 11.10 HP Pavillion dv7-3063cl

Today I plugged in headphones for the first time since installing Ubuntu 11.10 about a month ago. Eventually I noticed that the sound was playing from both the speakers and the headphones, so I tried to fix it.

I found this in a thread somewhere and  used 
```
 echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf 
```[B]Reboot

This got rid of all my sound output.
[/B]I realized that my laptop was in fact not an asus<.< and switched the code to 

```
 echo "options snd-hda-intel model=hp" | sudo tee -a /etc/modprobe.d/alsa-base.conf 
```[B]Reboot
[/B]
However, this didn't work either, so I tried uninstalling and reinstalling alsa-base. This also didn't work.
Anyone know how to go about fixing this?

---

### Post by Yellow Pasque on 2012-04-21
You can edit the file to remove the line you added and that should have your sound back to normal (although still without working headphone jack sensing).
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Before removing the line, I would try changing 'hp' (which is an invalid keyword) to 'hp-dv5' since that's the closest match for your model (and then rebooting).

In case you're wondering, the full list for that codec is here:
```
STAC92HD71B*/75B*
============
  ref		Reference board
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  hp-dv4-1222nr	HP dv4-1222nr (with LED support)
  auto		BIOS setup (default)

```

---

### Post by Zyxer22 on 2012-04-21
I tried both getting rid of the line and changing it. I used both hp-dv5 and auto. Neither worked. If the only thing that line of code does is add a line to the document (which is what seems to be the case) then, I'm not sure I understand why that doesn't fix it.

---

### Post by Zyxer22 on 2012-04-22
bump?

---

### Post by Zyxer22 on 2012-04-22
So, some new information.

I'm not sure why, but I'm not able to open alsamixer in my terminal  anymore. I'm not sure if that means that it's not on my laptop at all?

This should reinstall alsa, right? It says that it's up to date and no new packages need to be installed. If so, why can't I use alsamixer?
```
apt-get install --reinstall alsa
```

---

### Post by Zyxer22 on 2012-04-23
Fixed it. Just downloaded alsa from it's site and changed the line to use hp-dv5.

---

