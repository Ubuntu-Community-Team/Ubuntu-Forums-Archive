---
title: "Wireless connection problem for Unix-based laptops"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by jonarnett90@gmail.com on 2011-12-30
I'm having a really odd problem- Wireless is slow only for unix-based operating systems in my house.

So a few days ago, some house guests, one running Mac OSX Snow Leopard, the other running Win7, commented that my wireless was slow. Running Win 7 at the time, I had no problem.

Last night, however, I was up late working in Ubuntu 11.10 and my wireless speeds hit a wall. Speedtest.net wouldn't even load. My sister, running, OSX had the same problem. I would go and change the wireless password, which would only improve speeds for 10 minutes or so. Then nothing.

After about the 5th time, having tried changing the wireless channel, updating the router firmware, and changing the password to rather strong passwords, Ubuntu was still running slow. I rebooted into Windows 7, and voila, full wireless speed.

My wireless security is WPA2-AES
Router is Netgear WNDA 3400

---

### Post by dodo3773 on 2011-12-30
I recently had a similar problem. Setting static ip addresses helped in my case. Try giving your Ubuntu machine one on your router.

---

### Post by jonarnett90@gmail.com on 2011-12-31
Thanks so much for your help! As of now, it is working much better. Although it may be deceiving me, my hopes are high. Since I posted, I'd discovered that it was my Ubuntu laptop slowing down the wireless for the rest of the house, and even I wasn't getting a reasonable connection...

I'm always curious to know why, so do you know why setting a static ip stops my laptop from devouring bandwidth or why it was devouring bandwidth in the first place?

---

### Post by dodo3773 on 2011-12-31
> **jonarnett90@gmail.com said:**
> Thanks so much for your help! As of now, it is working much better. Although it may be deceiving me, my hopes are high. Since I posted, I'd discovered that it was my Ubuntu laptop slowing down the wireless for the rest of the house, and even I wasn't getting a reasonable connection...

I'm always curious to know why, so do you know why setting a static ip stops my laptop from devouring bandwidth or why it was devouring bandwidth in the first place?

Not really sure. What happened was I had someone who had an android phone that was taking three ip addresses somehow and totally messing up my network. I read that giving the android device a static ip address would help. So, then I thought to myself: Why wouldn't this help with my laptop problem? So I gave it a shot and sure enough it helped. The reason behind it? I am not sure. I can only assume that it is somehow related to dhcp on the router end when talking to a GNU / Linux device. One thing we do have in common though is that I also have a netgear router. So maybe it is a problem with netgear. Not sure. Glad it helped though.

---

### Post by jonarnett90@gmail.com on 2011-12-31
> Not really sure. What happened was I had someone who had an android phone that was taking three ip addresses somehow and totally messing up my network. I read that giving the android device a static ip address would help. So, then I thought to myself: Why wouldn't this help with my laptop problem? So I gave it a shot and sure enough it helped. The reason behind it? I am not sure. I can only assume that it is somehow related to dhcp on the router end when talking to a GNU / Linux device. One thing we do have in common though is that I also have a netgear router. So maybe it is a problem with netgear. Not sure. Glad it helped though.

Well, that makes enough sense for me! While this hasn't been an issue before, I have had some negative experiences with Ubuntu and a Netgear wireless adapter, so my overall impression is that they aren't so good with eachother... Well, anyhow, thank you again for all your help! My wireless connection is staying stable and sane and I can check my email again!

---

