---
title: "What is the status of HDMI out in Linux?"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by Cadmus on 2008-03-31
I'm thinking of upgrading my current home media centre and tv from an inherited CRT connected to an AGP card in a beat up old Dell desktop (quiet though) to something with a wee bit more to it.

What I would like to know is if I bought an HDTV with the usual HDMI socket, how easy/hard is it to make it a second display if I were to buy a card with an HDMI connector? Would I get sound? Does HDCP's proprietary nature cause problems?

---

### Post by aeiah on 2008-03-31
you may get sound if the graphics card supports it but i think people are having problems. you could always connect an audio cable for the time being until the issue is resolved. you should probably stick with nvidia unless you find someone with an ATI card they've got working with an hdtv as a second monitor. nvidia is usually a lot easier. bear in mind that hdmi is just dvi+audio, so, if you're ok with running an audio cable into your tv as well as the video cable, you may save some money.

the important thing you should think about though is 1:1 pixel mapping. most tvs dont support it, especially in linux, but there are some that do and if you get the chance, you should get one of these. it will mean that your tv wont upscale the image. a lot of say, 720p hdtvs will say they use a resolution of 1366x768, but most will only allow you to input either 1280x720 or 1024x768, and then they will upscale to the 1366x768. this is the same for full hd televisions. it goes without saying that there's a degredation in quality when you upscale.

 have a look here:
[http://pixelmapping.wikispaces.com/](http://pixelmapping.wikispaces.com/)

---

### Post by Cadmus on 2008-03-31
Thanks for the response, I think you've helped me out before, I may forget names but I never forget a turkey(?) in a cardigan.

Looking at that link you've slung me it does appear that there's quite a few models coming online with 1:1, by the time I wish to purchase an HDTV (6 months away realistically) there should be better understanding of who's offering what and the connection to Linux should be better supported.

---

### Post by aeiah on 2008-03-31
no worries, i just went around things the wrong way when i bought a tv, and was really pissed off when i realised i couldnt actually get it to display at 1366x768. that'll teach me to get the cheapest tv i could possibly find...

but yea, if it can do 1:1 pixel mapping in windows, it can do it in linux, but it may take some time to figure it out if no one else has done it before. if i was choosing a tv again i know id pay an extra 50 for pixel mapping, maybe more if i knew it would be easy to get it working under linux

---

