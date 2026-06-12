---
title: "Rolling S-Video"
date: 2009-11-18
forum: Mythbuntu
---

### Post by ColBuendia71 on 2009-11-18
I've done a bit of research for this, but haven't found the solution for my particular issue. I've seen a lot about how to get s-video working once you get into mythbuntu, but haven't seen anyone with solutions for what to do if all your video is screwed up. I'm going from an nvidia 8400GS into an analog TV. The video is fine via a regular monitor cable, but goes black and white and runs all over the screen once I plug via s-video into the TV. I was wondering if the issue was that the receptor on the video card is 7 pin and the cable I'm using is 4 pin. The TV receptor is also 4 pin. Thanks.

---

### Post by blackoper on 2009-11-18
I'm using a 7300 and svideo out and it's working fine. Do you have a second svideo cord to test and make sure it's not a bad svideo cable?

If it's not the cable sounds like you have a weird connector that isn't outputting standard svideo signals. The black and white and moving indicates a loss of sync in the signal. Maybe try a mythbuntu live cd to see if it's a problem with the drivers

---

### Post by ColBuendia71 on 2009-11-18
The cable I'm using works fine when I use it with my Macbook to hook it to the TV. It also can't be the solely the fault of drivers since the BIOS screen is also doing the same thing. It should at least hold steady until the splash screen if it's a driver problem.

It seems more likely that it's a nonstandard signal like you said. Anyone know why this would have happened and if there's any way to solve it?

---

### Post by nickrout on 2009-11-18
> **ColBuendia71 said:**
> I've done a bit of research for this, but haven't found the solution for my particular issue. I've seen a lot about how to get s-video working once you get into mythbuntu, but haven't seen anyone with solutions for what to do if all your video is screwed up. I'm going from an nvidia 8400GS into an analog TV. The video is fine via a regular monitor cable, but goes black and white and runs all over the screen once I plug via s-video into the TV. I was wondering if the issue was that the receptor on the video card is 7 pin and the cable I'm using is 4 pin. The TV receptor is also 4 pin. Thanks.

LOL Colonel Buendia, I am reading '100 Years of Solitude' at the moment!

The video card plug is not strictly just for s-video. It probably also has tha ability to output compnent and you can get an adaptor - 7 pin din to three compnoent RCA's.

Having said that I think it is backwardly pin compatible with s-video too. If so what you are seeing is probably the result of a bad cable. s-video has two signals, Y or luminance, which is 'brightness' and C which is chrominance or 'colour'. If only Y is working you get black and white. Try another cable.

see also here [http://en.wikipedia.org/wiki/S-Video#7-pin_mini-DIN](http://en.wikipedia.org/wiki/S-Video#7-pin_mini-DIN)

---

### Post by ColBuendia71 on 2009-11-19
> **nickrout said:**
> LOL Colonel Buendia, I am reading '100 Years of Solitude' at the moment!

The video card plug is not strictly just for s-video. It probably also has tha ability to output compnent and you can get an adaptor - 7 pin din to three compnoent RCA's.

Having said that I think it is backwardly pin compatible with s-video too. If so what you are seeing is probably the result of a bad cable. s-video has two signals, Y or luminance, which is 'brightness' and C which is chrominance or 'colour'. If only Y is working you get black and white. Try another cable.

see also here [http://en.wikipedia.org/wiki/S-Video#7-pin_mini-DIN](http://en.wikipedia.org/wiki/S-Video#7-pin_mini-DIN)

Ok, since I've been told to do it twice now, I'll call a friend and see if I can borrow a cable even though the cable works for my macbook.

I don't know if this tips anyone off, but I tried it again after my first post and when ubuntu came up, it had a screen saying that it was running in low graphics mode. This doesn't come up when I plug in a VGA cable. The nvidia proprietary drivers are installed and working fine.

And, obviously I think so from my handle, Garcia Marquez is incredible. Probably the greatest currently living writer on earth. If you like 100 Years, then check out Strange Pilgrims.

---

### Post by SiHa on 2009-11-19
I'd be looking at this bit again:> The video card plug is not strictly just for s-video. It probably also has tha ability to output compnent and you can get an adaptor - 7 pin din to three compnoent RCA's.Some may be backwards compatible, but many aren't I have a 9-pin mini-din on my FX5200. You can plug an S-video cable into it, but all you get is the B&W. You need to try and get an adaptor cable, I think.

---

### Post by ColBuendia71 on 2009-11-19
> **SiHa said:**
> I'd be looking at this bit again:Some may be backwards compatible, but many aren't I have a 9-pin mini-din on my FX5200. You can plug an S-video cable into it, but all you get is the B&W. You need to try and get an adaptor cable, I think.

Any idea on the cost/best place to purchase an adapter cable? Every time I buy something for the HTPC I tell my wife it's the last thing and her tolerance for that is getting pretty low...

---

