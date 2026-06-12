---
title: "Atheros 5001 temperamental, works on my network but not on my Sisters!"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by thebiguglyone on 2010-07-08
Hi all,
I have been reading up on the problems people have had with the Atheros card but mine is a little different.

I have the latest version of Ubuntu installed on my nephews Compaq Presario CQ60 laptop and it just won't wirelessly connect to his home network. The "Enable wireless" button is faded and doesn't allow me to click it to turn wireless on.

However... when I have the Laptop at my house to try to fix it I don't have any trouble, I can surf the internet quite contently. 

We both use a sky router for our wireless and the security settings are the same, it just don't make no sense!!!

When I have it on at mine, the button to turn wireless on/off is changing blue to orange and back again quite regularly.

The driver installed on the system is the Ath5K.

I look forward to any advice/ info regarding this.

Thanks
TBUO

---

### Post by bkratz on 2010-07-08
> **thebiguglyone said:**
> Hi all,
I have been reading up on the problems people have had with the Atheros card but mine is a little different.

I have the latest version of Ubuntu installed on my nephews Compaq Presario CQ60 laptop and it just won't wirelessly connect to his home network. The "Enable wireless" button is faded and doesn't allow me to click it to turn wireless on.

However... when I have the Laptop at my house to try to fix it I don't have any trouble, I can surf the internet quite contently. 

We both use a sky router for our wireless and the security settings are the same, it just don't make no sense!!!

When I have it on at mine, the button to turn wireless on/off is changing blue to orange and back again quite regularly.

The driver installed on the system is the Ath5K.

I look forward to any advice/ info regarding this.

Thanks
TBUO

Perhaps your nephew has a local wireless A/P on the same channel as a neighbor or poor signal quality.
You might do a 

sudo iwlist scan

in the terminal and see if there is any competition.

---

