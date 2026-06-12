---
title: "Cannot connect to some wireless networks ...."
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by benhur99ph on 2009-11-16
Hi guys,

Should there be a post the same as this, then please just kindly point me to the right direction...

Well, here goes...

I am using Ubuntu 9.10 and my wifi is working fine. The only problem I have is that a few days ago, upon booting my laptop, I suddenly cannot connect to my work's wireless network. My laptop cannot even detect the networks ID. The wifi router is on and it broadcasts its SSID (I tried connecting with my phone and it works just fine).

I went home and tried connecting to my home wireless network and it automatically connected like it should. So how come I cannot even detect the SSID of the wireless network at the office?

There were some of my colleagues who had the same problem. Someone managed to get his working by deleting his connections and creating and refreshing the available network list (they are all using Vista). I tried deleting the connection by right-clicking on the wifi icon on the gnome panel> then edit connections> then click on the wireless tab and delete the connection for my office.

But still after countless log-offs and restarts, I still cannot detect my offices wireless network? 

Any help is appreciated. Thanks!

---

### Post by jward3010 on 2009-11-16
Your wireless card is possibly incompatible with some types of wireless secutiry. Is it an oldish model or very new? Post the output of:
```
sudo lshw -C network
```

---

### Post by Bucky Ball on 2009-11-16
[quote=jward3010]Your wireless card is possibly incompatible with some types of wireless secutiry.[/quote]

OP gives the impression this was working then one day not. Is this correct benhur99ph? If others struck a problem on the same day, same place, same time, I'd ask your techies if something has been changed recently.

---

### Post by jward3010 on 2009-11-16
Sorry, you're damn right. I ran through that post fast and straight away thoughts went back to another post about wireless connectivity and and an old card that didn't support WPA.

---

### Post by benhur99ph on 2009-11-18
Hey! Thanks for the quick replies.

Here's the thing. It was working fine before then suddenly when I booted my machine the other day, I cannot connect anymore. What bugs me is that there was no change done on the wifi router. 

Another thing to consider is that I use the same router at home. It's a Linksys WRT54g. At home it connects without any problems. As soon as I start my laptop I'm already connected. 

At the office, I could detect the wifi of the PSP's nearby so I am really confused as to what is the reason why I cannot even detect the office's wifi signal even if I'm just in the same room as the router... :(

---

### Post by jward3010 on 2009-11-18
Go to the terminal and do a:
```
sudo iwlist scan
```
Read through the result and see if it appears there. If it does is there anything unusual about it's SSID - unusually long, strange characters.

I'll give it to you, it's certainly weird.

---

