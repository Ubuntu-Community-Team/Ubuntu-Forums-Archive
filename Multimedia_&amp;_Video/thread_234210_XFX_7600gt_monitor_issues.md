---
title: "XFX 7600gt monitor issues"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by offramp13 on 2006-08-11
I just built a new machine, it has an AM2 Asus M2V motherboard, with an athlon 64 x2 4200~2.2ghz, and two gb's of pc6400 OCZ gold series ram. I have an XFX 7600gt installed also. I had windows on it orignally and it worked fine. I decided to install the 64-bit version of the new 6.06. The installation, though a bit shaky did just fine, but in the end when i booted into the completely installed Ubuntu my monitor displayed "Please check pc display settings" and nothing showed up on the screen. I have a couple-year-old HP Pavilion mx70 monitor that worked fine with the card on windows. It is plugged in to one of the two DVI ports on the card using a DVI-to-RGB converter that came with the card. In the past i recieved the same message on my monitor when i set the refresh rate too high, so i attatched my buddies samsung LCD monitor using a DVI cable and it worked just fine. Then i looked at the display settings and they weren't even unusually high, i set them to 1024 x 768 with 60 hz refresh rate. And switched back to my HP monitor thinking that it would fix the problem, it didn't. I dont know what is wrong with it. Can anyone help?

---

### Post by tseliot on 2006-08-11
Moved to a more appropriate section

---

### Post by tseliot on 2006-08-11
boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Select the Advanced customisation when it asks you about the refresh rate and resolution of your monitor.

Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine

---

### Post by offramp13 on 2006-08-11
Thank you, that worked perfectly.

---

### Post by offramp13 on 2006-08-11
Thank you, that worked perfectly.

---

