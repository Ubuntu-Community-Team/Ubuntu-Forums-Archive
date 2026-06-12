---
title: "Adobe Flash Runs Slow in flash video"
date: 2009-08-15
forum: Multimedia Software
---

### Post by eladh7 on 2009-08-15
Hello
I installed ubuntu 9.04 now and I have a problem with viewing Flash content.
After installing the ubuntu finished, I installed all the updates and installed the latest driver for my graphics card - Hardware drivers.
The problem is that when I see a flash video on youtube, they work me slow, and can not be watch like this.
The problem is not only on youtube, are all sites that allow video viewing.

It should be noted that when I go to youtube for the first time, opened in firefox top bar that said should install Flash to view the Videos.
In the top bar I had three possible installation of a flash, one of them was - adobe flash, and that I installed.

How do I fix the problem? Do I have to install something more? or i need to installed another flash?
Essential to add that the system itself runs on my computer as well, is quick.
My specifications: Processor Pentium 4 - 2000 MHz, card - nvidia geforce 6800 gt 256 MB, Memory - 2 GB. 

Thanks

---

### Post by eladh7 on 2009-08-15
please help :(

---

### Post by eladh7 on 2009-08-16
why any body dont help me?
its very important.

---

### Post by hojgaard on 2009-08-17
I have the same problem...

Many flash-banners on a website makes my firefox deadly slow...

---

### Post by eladh7 on 2009-08-18
Must be a solution to it!
	
What else can I do to resolve this problem?

---

### Post by Saganite on 2009-08-18
Same issue here.   Choppy video, sound if fine but video is jerky to the point of unwatchablity.   In Hulu and some other flash sites I can get around this by right clicking in the video and lowering the Quality setting to low.     Other than that there seems to be little urge for devs to care or look into this.  Been having this problem for months.

---

### Post by eladh7 on 2009-08-21
Help guys :(

---

### Post by Kayos02 on 2009-09-04
Same thing here.

Dell Inspiron 1300 - Xubuntu 9.0.4

---

### Post by Bill.the.noob on 2009-09-04
Hey Guys and Girls. I'm having a problem with the new Adobe flash version 10.0.3..... as well. It doesn't install properly and the quality of the picture is garbage. Many sites like Facebook require the new flash to view their content. Don't worry , I'm sure some one can figure a solution to this problem. I think it's just Adobe ( being perpriatary ) screwing with us.

---

### Post by Vazel on 2009-11-11
I too have problems with flash video. Flash video does not play well there's tearing all over the place and I get artifacts in the picture. Here's a pic with a red artifact in it. [http://i34.tinypic.com/xp4zcx.png](http://i34.tinypic.com/xp4zcx.png)  Then when I fullscreen hulu it becomes very choppy and this is at a desktop resolution of 1024x768.

CPU: Athlon 2800+ Barton 
GPU: Nvidia 6200 (driver is installed)
RAM: 512MB

---

### Post by shpansk on 2009-11-27
Hey guys, 

All I really use flash for is videos, so this trick is only really useful if you want to watch fullscreen videos.

I just now discovered a little trick that will enable you to play the videos as if they were directly on your hardisk without having to use the flash plugin directly.

The trick isn't a trick so to speak, its just merely taking advantage of the buffered content that streaming technology utilises to appear to play files without load times.

Everytime you stream a video, ubuntu creates a new file with a corresponding title like 'FlashOCNZcD' in your '/tmp' folder. If you watch the folder, the filesize of the FlashOCNZcD file grows as the buffering bar on the website nears completion. This FlashOCNZcD is your video stream.

The trick is to pause the stream (which still lets the video buffer) and instead of playing the stream in firefox, open the FlashOCNZcD file in vlc!

BINGO !!!

I cant believe I never thought of this before...

Tested on Ubuntu 9.04 Jaunty, flash10, firefox 3.0 and VLC .9.9a

---

