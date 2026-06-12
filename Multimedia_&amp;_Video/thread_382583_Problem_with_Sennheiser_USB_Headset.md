---
title: "Problem with Sennheiser USB Headset"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by Helmi on 2007-03-12
Hi,

i've got two soundcards:

```

$ cat /proc/asound/cards 
 0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [2001]
                      Audigy 2 ZS [2001] (rev.4, serial:0x20011102) at 0xdf00, irq 217
 1 [Headset        ]: USB-Audio - Sennheiser USB Headset
                      Sennheiser Communications Sennheiser USB Headset at usb-0000:00:1d.7-2.2, full 

```

Both worked fine until yesterday. When calling someone using skype, skype announces "problems with sound device" as the call starts. I first blamed skype for that but the problem seems to be that the USB recording signal doesn't get into the right way. Skype works fine after switching to the Audigy2. I installed gnome-alsamixer and played around a bit. If i unmute the microphone for listening mode i can hear myself speaking but i couldn't get anything recorded using the usb mike.

ideas anyone?

Best,
Frank

---

### Post by Helmi on 2007-03-16
a shameless bump as i couldn't find any help yet.

probably ANY idea?

---

