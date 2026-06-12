---
title: "Wireless card"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by peterson43 on 2011-09-22
I have a new HP laptop running Ubuntu 11.04. I've been having issues with my internet speed, and I'm starting to suspect that it might be caused by my wireless card. 

I'm supposed to be getting download speeds of 1.5 Mps, but oftentimes when my internet seems to be running slow I'll check my download speed at speedtest.net and I'm only getting 0.2 Mps. Then, a while later the internet speed will improve and I'll be getting close to 1.5 Mps again. 

I'm suspecting that it's a wireless issue because I haven't noticed it yet happening if I have the computer plugged directly into the router. When I installed 11.04 I enabled the proprietary driver for the wireless card. 

When I run sudo lspci, the wireless card info I get is 
```
24:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
```

The information that I have on the proprietary driver is that it is a Broadcom STA wireless driver. 

My questions are the following:
1) Are there any known issues with this driver
2) If I remove this driver is there an open source driver that comes with Ubuntu that I could use instead? (do they have fewer issues?)
3) Is there anything else that could be causing this problem?

---

### Post by MG&amp;TL on 2011-09-22
Question 2: Open-source drivers tend to have less issues because people can fix stuff-BUT they're not as good as the people's with the hardware to tinker with.

---

### Post by Lisiano on 2011-09-22
1) Them being closed source is a issue for some. Don't know any other issues since all my WiFi adapters are Atheros (They rock btw).
2) AFAIC, there are no open-source drivers for broadcoms.
3) Maybe someone on your network is downloading something or someone broke into it? Try changing your WPA2 password on the router to something new. Also if you don't have WPA2 on, TURN IT ON. WEP can be cracked in less than 5 minutes and the cracker can just watch the progress, almost nothing needed to be done (I know from experience, network security is my hobby). WPA1 has some sort of hole in it that you can exploit to get the password but I don't remember, maybe I am confusing it or the place I read it actually meant WEP. Anyway. Use WPA2 and a new password.

---

### Post by peterson43 on 2011-09-22
> **Lisiano said:**
> 1) Them being closed source is a issue for some. Don't know any other issues since all my WiFi adapters are Atheros (They rock btw).
2) AFAIC, there are no open-source drivers for broadcoms.
3) Maybe someone on your network is downloading something or someone broke into it? Try changing your WPA2 password on the router to something new. Also if you don't have WPA2 on, TURN IT ON. WEP can be cracked in less than 5 minutes and the cracker can just watch the progress, almost nothing needed to be done (I know from experience, network security is my hobby). WPA1 has some sort of hole in it that you can exploit to get the password but I don't remember, maybe I am confusing it or the place I read it actually meant WEP. Anyway. Use WPA2 and a new password.

I don't think it's from someone else downloading things on my network. If it were, this would also slow down my internet when I'm plugged directly into the router, wouldn't it? Also, I live out in the country and there really isn't anyone living close enough to hack my wireless. I did set up the router with a password, but I don't remember what the security was. How do I check that?

---

### Post by Lisiano on 2011-09-22
Click on the network manager icon -> Edit Connections -> Wireless -> Pick your home WiFi network -> Edit -> Security -> Look at the type.

Also I don't know if this is true but, some people say that weather can affect the connection and the way the house is built (Metal under the floor, etc).

---

### Post by philipballew on 2011-09-23
I would if I were you make a trip to a different wifi hotspot like starbucks or something and see if you get the same errors there? Do you live to far to check that out. if so I can help with other methods

---

### Post by peterson43 on 2011-09-23
I think that I may have solved the problem, and it appears to have nothing to do with Ubuntu. I have another laptop that I can run Windows on, and when I tried using that one the wireless speed was also slow at times. Thus, it seems that the issue is actually with the wireless router. 

I think I fixed the problem by just changing the channel that the wireless router was broadcasting on. At least it seems to be working good so far. In any case, it appears the Ubuntu part of my problem is "solved."

---

### Post by philipballew on 2011-09-23
If you look at your neighbors router channels you'll see that they are probably using a channel that is the same as the one you were on or a similar one.

---

### Post by peterson43 on 2011-09-30
> **philipballew said:**
> If you look at your neighbors router channels you'll see that they are probably using a channel that is the same as the one you were on or a similar one.

I'm not sure that's it. I've tried about 6 different channels now, and none of them work consistently well (and I only have one neighbor within wireless range). I think there may be something wrong with the wireless router.

---

### Post by philipballew on 2011-09-30
Alright then, I want you to reset your router, also, what model of router do you have?

---

