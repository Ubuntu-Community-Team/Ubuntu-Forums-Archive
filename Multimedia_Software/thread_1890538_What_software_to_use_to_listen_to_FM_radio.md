---
title: "What software to use to listen to FM radio?"
date: 2011-12-03
forum: Multimedia Software
---

### Post by calande on 2011-12-03
Hello,

I have an FM radio board that is supported by Linux and I'm having a hard time using it. I haven't been able to use it with VLC. I found gnomeradio and XMMS-FMRadio but the former is only available as source files and the latter isn't in the package tree anymore. My radio isn't available for streeming. What software do you suggest to use?
Thanks,

---

### Post by dabl on 2011-12-03
I use radiotray to stream from the internet -- I dunno if you can set it to stream from a local device.

---

### Post by calande on 2011-12-03
Thanks. As you can see from the sound mixer, there is sound coming out of the FM radio board, but I can't hear it. And "fm" command is not listed in the sound applications tab. Weird. What do you think?

---

### Post by radiobuzzer on 2012-01-31
Many PCI radio/tv cards require a separate cable to be connected from the sound out of the radio card to the line in of your sound card. So check this connection. Alternative, some PCI cards offer the possibility to connect them with the sound card, using a grey sound cable with a square edge in the PC box, similar to one the CDrom uses to send sound from CD-Audio

---

### Post by calande on 2012-02-22
Thanks. I'm still struggling to make my radio board work. My device is /dev/radio0 and my station is 95.7. What command do you suggest to receive FM radio?
Thanks,

---

### Post by nrundy on 2012-02-22
Exaile

---

### Post by calande on 2012-02-22
Thanks, from my research, it doesn't seem to support FM radio boards, does it really?

---

### Post by calande on 2012-02-23
Any other suggestion?

---

### Post by andrew.46 on 2012-02-24
> **calande said:**
> Any other suggestion?

Unfortunately I do not have one of these devices to test but it certainly looks as if MPlayer should be able to access such a device. Looks like SMPlayer has a nice gui menu for this as well so might be worth a look?

---

### Post by calande on 2012-02-24
Thanks.

---

