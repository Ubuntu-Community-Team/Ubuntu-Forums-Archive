---
title: "Alfa AWUS036H Slow Internet"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by akashi on 2012-10-14
I am using a computer with an Alfa AWUS036H device connected to my Wireless G router. My internet speed is 25mbps although I get a maximum speed of around 18mbps.

The device works with Ubuntu 12.04 out of the box as I am able to connect to the router with an excellent signal. However, the internet speed is **_very, very slow!_**

I also got the exact problem with Windows XP and 7 and tried the latest drivers found on Realtek's website (RTL8187L)

I connected to my brother's router which is 2 houses away and he also has a 24mbps internet connection. I am again able to connect with an excellent signal (full bars)but the websites load **_extremely slowly_** and even fail at times. When I run a speed test, the maximum speed I got was around 2-3mbps. If I use my old USB device (RT2070) I can get around 15mbps from my router.

**My question to other owners of the Alfa AWUS036H:**

What speeds can you achieve on your network? Can you max out your internet speed?

Please help as I really need a long rang adapter that can connect to routers (like the AWUS036H) but more importantly provide reasonable speed. If it connects with full bars, surely it should be able to max the connection?

I was also considering the newer Alfa AWUS036NHR, any advise on this one?

Thanks in advance.

---

### Post by Kirk Schnable on 2012-10-14
I have this card, and I have not noticed this.  When I've used it on my university campus, I could pull 40-50Mbit easily from the Internet.

Are you sure your card isn't defective?  It sort of sounds like it might be, since you're having difficulties on multiple operating systems.

It almost sounds like you're running at USB 1.1 speed (12Mbps).  Do other USB devices perform well on the same USB port (try a flash drive or something, and generate some bandwidth).

Just my thoughts...

Kirk

---

### Post by akashi on 2012-10-14
Thank you for your input.

The USB port that I tried the device on I also tried my older WiFi adapter without any problems. I have tried different ports on my computer and also tested it on 2 other laptops. All ports were USB 2.0

I am thinking it is faulty but I read this problem on many forums and thought it was the "norm" for this card. Most people seem to use this card for WiFi security testing which I had no problems with.

Since you were receiving 40-50Mbit, you were almost maxing the limit of 54Mbit! This is good news for me. I am thinking should I get it again from a reliable place such as Amazon and try it again or just get the newer AWUS036NHR?

Thanks.

---

### Post by Kirk Schnable on 2012-10-14
> **akashi said:**
> Thank you for your input.

The USB port that I tried the device on I also tried my older WiFi adapter without any problems. I have tried different ports on my computer and also tested it on 2 other laptops. All ports were USB 2.0

I am thinking it is faulty but I read this problem on many forums and thought it was the "norm" for this card. Most people seem to use this card for WiFi security testing which I had no problems with.

Since you were receiving 40-50Mbit, you were almost maxing the limit of 54Mbit! This is good news for me. I am thinking should I get it again from a reliable place such as Amazon and try it again or just get the newer AWUS036NHR?

Thanks.

I have an NHR as well. The only issue I have had with it was compatibility with my Raspberry Pi kernel (the NH was compatible out of the box). The NHR card works great under Ubuntu for me as well. 

Kirk

---

### Post by akashi on 2012-10-15
Can you confirm if the AWUS036NHR can utilise the full bandwidth of your internet?

Thanks.

---

### Post by Kirk Schnable on 2012-10-17
> **akashi said:**
> Can you confirm if the AWUS036NHR can utilise the full bandwidth of your internet?

Thanks.

The Internet can be unpredictable... speeds are not always guaranteed.  I have not noticed any lack of performance when using the card.

---

### Post by akashi on 2012-10-17
I returned the one I brought from ebay and ordered a new one from Amazon (Fulfilled by Amazon)

*signs* This one is even worse than the last one! It has trouble connecting to **my network** whereas the other connected quickly. I could not browse a single website! The other loaded pages **very slowly**.

Before anyone asks, I understand the signal might of been too strong which is why I removed the antenna when trying to connect to my router. I even took it to a room about 10 meters away. Exact problem when connecting to my brother's router, 2 houses away.

Maybe it is time to give up on the AWUS036H and get a **AWUS036NHR** or a **AWUS036NHA**?

Your input is valued.

Thanks.

---

### Post by akashi on 2012-10-23
Just wanted to update and say I bought an Alfa **AWUS036NHA** which as the Atheros AR9271 chipset.

It is not as powerful as the AWUS036H as it is 650mW compared to 1000mW. However, I can max out my internet connection!

I am happy with this device.

Thank you very much  Kirk Schnable for your help.

---

### Post by TobiMensch on 2013-02-14
For a possible workaround for the speed-issues with the AWUS036H, you'll mind want check out the following post.
Had the same problems, and now they are most-likely gone :)

[http://ubuntuforums.org/showthread.php?p=12509249#post12509249](http://ubuntuforums.org/showthread.php?p=12509249#post12509249)

---

