---
title: "[SOLVED] TV turner card, how configure?"
date: 2008-07-06
forum: Multimedia Software
---

### Post by g_rus on 2008-07-06
I have a TV + FM Turner installed at Kubuntu (but is the same at Ubuntu). Is a Acorp 9Y878F.
I can't get it work. In this list [http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv](http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv) in 137 - 136 position is listed my tv card. But to configure i need do something at kernel with a some number card a some number turner. Exactly, How do this?

Anyone have this card work correctly?

This card have a remote control, and i know, i must configure de IRKick (Lirc for KDE) to this, but first, the TV.

Thanks:)

---

### Post by g_rus on 2008-07-20
Well, i have a little success.

Now i can see all channels, but not sound.

I did this configuration:

sudo modprobe bttv card=136 tuner=64 radio=1 remote=1 pll=1

But in tunner, i can use others numbers: 43, 47, 57, 59, 64

Now, my only problem is not sound. I check in kmix, and line 1 is up. I tried conect the pc speakers direct to sound out on tv card, and not sound.

The card have a cable from sound out on tv card to line in on sound card at mother board.

---

### Post by cariboo on 2008-07-20
Have you got line in enabled? If not go to the volume control in the panel and double click on the speaker icon. When the volume control panel pops up and click preferences in the window that pops open add a check mark to line in and try it again.

Jim

---

### Post by g_rus on 2008-07-20
Yes, i check kmix, -line in- is working, in fact all is enable.

I think is about sound configuration for  this tv card. But still i not find how do it. :(

---

### Post by g_rus on 2008-07-25
If someone know about his; i have more information in other forum, a kubuntu forum. Here: [http://kubuntuforums.net/forums/index.php?topic=3095958](http://kubuntuforums.net/forums/index.php?topic=3095958)

---

### Post by benrod on 2008-07-28
> **g_rus said:**
> If someone know about his; i have more information in other forum, a kubuntu forum. Here: [http://kubuntuforums.net/forums/index.php?topic=3095958](http://kubuntuforums.net/forums/index.php?topic=3095958)

According to my experience configuring tv card. You're wrong on configure the tuner. If you have picture, it means your card number is right. But if no sound, it means wrong tuner number.
I hope this comment helpfull.

---

### Post by g_rus on 2008-08-08
Well, thanks, i follow your experience. I check with all tuners numbers, compatible and not compatible with my card. I found more tuners number that work with my tv card, seeing all channles, but sound not. :(

---

### Post by g_rus on 2008-08-10
Today i found something. This channles, have a very poor quality sound, i must put the volume to high, of course a sound like "sssssss", is noising, and sometimes is possible undertand teh sound of the channel. Is not possible follow a movie or tv serie, or the music, but that menas that tv card work, well, what i must do to have a good quality.

I must say, i connet the speaker directly to tv card, and the sound is the same.

Of course, when i put the master volume to high, and i try to understand something, the systems sounds, like pidgin have a very high volume, is terrorific.

---

### Post by g_rus on 2009-01-09
Well, at first days of 2009 year i found how solve the problem, is so easy, but difficult to find in internet, because the information is in russian and bulgarian.

First, my card is Acorp 9Y878F, i found in this blog:

[http://sergej5.blogspot.com/2008/02/acorp-9y878f.html](http://sergej5.blogspot.com/2008/02/acorp-9y878f.html)

The instructions that i need; only add the line i2c_udelay=128 on /etc/modprobe.d/options , the result in that file is:

options bttv card=136 tuner=51 radio=1 remote=1 pll=1 video_nr=-1 i2c_udelay=128

I dont know if that number ( 128 ) is only for my model card or is a generic number, i dont know something about i2c_udelay. The command video_nr=-1 i saw in a bulgarian blog, I probed and nothing, still i don't know if i remove it change something in my configuration, but say "video" and do nothing that i see.

Of course, most to reboot. The sound work fine, normal. I probe on Tvtime and kdetv. I can see the TV normal, good quality of video and good quality of sound :D

---

