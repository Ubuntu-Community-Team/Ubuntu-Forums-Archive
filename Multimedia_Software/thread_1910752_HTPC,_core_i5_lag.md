---
title: "HTPC, core i5 lag"
date: 2012-01-17
forum: Multimedia Software
---

### Post by KingDalle on 2012-01-17
Hi, just bought a new pc. Relevant specs as follows:
Motherboard: Asrock H61m-ge
CPU: Intel core i5 2400 3.1GHz 6MB box s1155
Ram: 2x Corsair ddr3 pc1333 4GB CL9

It was meant to be a HTPC. It is connected to my 40" samsung LED TV. The salesman said that the integrated Intel graphics would be enough for streaming or watching a dvd. That I only needed a graphics card if I were to play any games on it. At first I tried XBMC Live, which i believe is build on Ubuntu 10.04 32 bit and then I tried Ubuntu 11.10 64 bit. Same result. When just trying to move the courser over the desktop it is very laggy. When trying to watch a dvd the picture will be refreshed about once every second or so. When setting the resolution to the lowest (about 600 x 400 cant remember exactly) the courser could move over the desktop almost without any lag and when watching a dvd the picture would be refreshed about twice a second or so.

As a side note I even tried installing OpenELEC but wasnt able to make it boot, most likely something i did wrong...

My question is as follows:
1. Is there any known issues with ubuntu and core i5 integrated graphics? (or something software related?
2. Was the salesman wrong? (as in I need to buy a graphicscard)
3. Is there something wrong with the PC? (some hardware faults)

Any advice or opinions will be appreciated as I am new to the linux world (but loving it so far)

Thanks, Daniel

---

### Post by rubylaser on 2012-01-18
An i5 should be able to easily playback 1080p without the need for a discrete graphics card.  I would give Openelec a shot again. I have the Generic image running on one of my 3 HTPCs at home and install was easy and the result is perfect 1080p playback with an Nvidia 210 graphics card and an AMD 4600+ X2 CPU (much weaker processor than yours).  Have you tried connecting the PC to a computer monitor to rule out your TV's smooth motion causing the appearance of choppiness?

---

### Post by KingDalle on 2012-01-18
Hi, I just did as you suggested, connected to a computer monitor. And realized another problem, ubuntu won't play any of my dvds but an old lucky luke cartoon. I did not have that problem with xbmc. It says "An error occured, could not read the dvd. This may be because the dvd is encrypted an a dvd decryption library is not installed." Where to get that library? hm, back on track.

Lucky Luke plays just fine on the computer monitor. Don't know about TV's smooth motion, is it something I should disable in the TV's settings or in ubuntu?

As a side note Ubuntu 11.10 64 bit is presently installed. Once things get working I plan on making a dual boot installation with ubuntu (for web browser and old amiga games) and either openelec or xbmc for htpc purposes.

I called my salesman today, he was prepared to pay for expenses for freight and testing no matter the conclusion. But I think it will be a little embarrassing if they are to detect no faults.

Again, all inputs are most welcome!

Thanks, Daniel

---

### Post by papibe on 2012-01-18
Hi KingDalle. Welcome to the forums!

A few thoughts:
[LIST]
[*]The video acceleration library for Intel cores is called VAAPI.
[*]I believe latest OpenELEC is based on XBMC v10, that does not support VAAPI (by default, although I think can be patched).
[*]I pretty sure the latest beta XBMC v11 supports it by default.
[*]In order to play DVDs you need to install the package: ubuntu-restricted-extras.
[/LIST]
Hope it helps.
Regards.

---

### Post by KingDalle on 2012-01-19
Hi, thanks.
 
As i stated earlier I am new to the ubuntu and linux in generel. So I dont understand what you are writing :-)
 
I suppose that when I have more time I can find an online guide on how to install VAAPI?
 
I will try out xbmc v.11
 
How do I install the package: ubuntu-restricted-extras ?
 
Thanks.

---

### Post by KingDalle on 2012-01-19
Hi again,

I installed the ubuntu restricted extras and the repository from medibuntu. Now the no dvd will even start, not even getting an error message anymore. I decided to skip  movie player and installed vlc instead, same result. But all the codec stuff and about getting to watch encrypted dvds is not my main concern right now. I need a way to test if my hardware is okay or if I should get it checked.

I found the following:
[http://www.pcmediacenter.com.au/forum/topic/45335-problems-setting-up-htpc-with-new-samsung-led-tv/](http://www.pcmediacenter.com.au/forum/topic/45335-problems-setting-up-htpc-with-new-samsung-led-tv/)

To me it sounds like it is related. How can I perform a similar test using ubuntu?

Thanks again!

---

### Post by papibe on 2012-01-19
To install the extras write this on the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
There are several guides on the [xbmc forums]("http://forum.xbmc.org/index.php"). This one for example:

[INDENT][HOW-TO use VAAPI HW Acceleration in Intel Core i3]("http://forum.xbmc.org/showthread.php?t=86581&highlight=vaapi") [/INDENT]

Hope it helps.

---

