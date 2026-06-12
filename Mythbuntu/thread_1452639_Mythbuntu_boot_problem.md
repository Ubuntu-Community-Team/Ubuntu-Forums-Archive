---
title: "Mythbuntu boot problem"
date: 2010-04-12
forum: Mythbuntu
---

### Post by sqeelurgle on 2010-04-12
I get a problem with mythbuntu booting, where every so often it won't boot properly.  When this happens, it will take a very long time, and will eventually boot to the mythwelcome screen.  On that screen, the usual countdown is missing, and there is no record of any future recording.  The system won't record anything, and you can't watch live TV.  Usually a reboot or two will clear up the problem, but obviously this makes automatic boots to record a problem - I miss shows sometimes.  The only message in the error logs is this:

rt_ioctl_giwscan. 1(1) BSS returned, data->length = 131

Any ideas?

Thanks

---

### Post by ktmom on 2010-04-12
I don't think I can help you, but I am curious what capture card(s) are you using?  I have this problem when the 2250 card doesn't load before the backend.  I then have to restart the backend to make things work.

---

### Post by sqeelurgle on 2010-04-12
I have two cards in it - An older Twinhan one and a Leadtek DTV1000S.

---

### Post by sqeelurgle on 2010-04-16
Bumpety bump because it's still an issue

---

### Post by ian dobson on 2010-04-17
Hi,

Do you have a wireless network card in your box?

Regards
Ian Dobson

---

### Post by sqeelurgle on 2010-04-18
Yes, there is a wireless card in there.  By default it is set up not to connect at boot, it is there in case I want to update or load new packages, but it is there.  Where this computer is located there isn't really any practical way of hard wiring the network.

---

### Post by sqeelurgle on 2010-04-18
There have been a few extra messages in the messages log recently, that talk about errors in bttv and bt878.  From what I can work out that is related to the Twinhan card.  I would like to try and post comparative extracts from dmesg for good boots and bad.  DOes anyone know the best way to get an appropriate extract?

Thanks

---

