---
title: "Sound card not detected"
date: 2009-04-11
forum: Multimedia Software
---

### Post by bunny_basher on 2009-04-11
Hello, 
      I have a problem with my C-Media Electronics Inc CM8738 (rev 10).

Every time I start my computer I have to run the same terminal command before the card is detected :S - gksudo modprobe snd-cmipci

Can anyone tell me how to make it work properly, without having to do this every time my computer starts? :)

Marcus

---

### Post by markbuntu on 2009-04-11
You can remove and reinstall alsa, that usually fixes problems like that.

(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

---

### Post by bunny_basher on 2009-04-11
Thankyou very much :D

---

