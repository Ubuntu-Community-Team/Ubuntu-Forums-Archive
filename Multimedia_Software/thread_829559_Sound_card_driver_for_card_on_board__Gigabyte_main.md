---
title: "Sound card driver for card on board : Gigabyte mainboard."
date: 2008-06-14
forum: Multimedia Software
---

### Post by mozartvn on 2008-06-14
I've just installed ubuntu 8.04, but I cant play music, anybody help me.:(
Thank u so much.:lolflag:

---

### Post by Trollslayer on 2008-06-15
what is the result when you enter 'aplay -l' in the console?
Also what output connections are you using?

---

### Post by prshah on 2008-06-15
> **mozartvn said:**
> I've just installed ubuntu 8.04, but I cant play music, anybody help me.:(

Open a terminal (Applications-Accessories-Terminal), then give the following command ```

sudo apt-get install ubuntu-restricted-extras

```

Will load support for most popular (mp3, etc) and video (mpg, avi, etc) formats.

---

### Post by Trollslayer on 2008-06-15
> **prshah said:**
> Open a terminal (Applications-Accessories-Terminal), then give the following command ```

sudo apt-get install ubuntu-restricted-extras

```

Will load support for most popular (mp3, etc) and video (mpg, avi, etc) formats.

Won't the restricted extras show up in synaptic as well?

---

### Post by Pjotr123 on 2008-06-15
This is the easiest way to install full multimedia support:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

---

### Post by Trollslayer on 2008-06-15
I have one problem - I've installed Mythbuntu 8.04 which is great for MythTV but the desktop menus aren't the same so it means working things out separately at time, just a warning for Mythbuntu users.
Ubuntutip is very good and well laid out BTW.

---

### Post by prshah on 2008-06-15
> **Trollslayer said:**
> Won't the restricted extras show up in synaptic as well?

Yes it will; but I'm probably a command-line junkie.

---

### Post by mozartvn on 2008-06-15
> **Trollslayer said:**
> what is the result when you enter 'aplay -l' in the console?
Also what output connections are you using?

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
what should i do? :confused:

> sudo apt-get install ubuntu-restricted-extras
i think the problem is only my sound card driver. :(

---

### Post by Pjotr123 on 2008-06-15
Sound: check this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

---

### Post by mozartvn on 2008-06-18
:(:(:(
nothing work. Any idea. I want to know exactly that ubuntu supports sound driver for Gigabyte.
thanks u very much.:popcorn:

---

