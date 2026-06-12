---
title: "How I Got BTTV,Tv Card To Work"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by Kross on 2006-11-15
I Have A Phobe Master + FM card,,
it was cheap..and so was I.

so After looking on the web...I found out what I had to do in Debian,,
And it seems to work in most of them anyhow. Well any new distro..with the bttv built into the kernel...

What it was doing was booting unknown drivers for my card...
So how do I tell it the right drivers...

I had to make a file called bttv and place it in my /ect/modprobe.d/ folder
then I had to place these commands in that file.

options bttv card=[COLOR="DarkGreen"]2[/COLOR] tuner=[COLOR="DarkGreen"]2[/COLOR] radio=[COLOR="DarkGreen"]1[/COLOR]

Now in green,,tells the about my card.,,yours may be diffent.

card=2 = Phobe Master+Fm
tuner=2 = NTFS

to see a list of diffent cards & tuners.....find yours.
look here....
[http://www.mythtv.org/wiki/index.php/Bttv](http://www.mythtv.org/wiki/index.php/Bttv)

after that I reboot...
and it worked....

I am still A noob,,but I thought my findings may help.

I have also attached my file...
hope this helps.... 

[COLOR="DarkGreen"]-Kross[/COLOR]

---

### Post by NT4usB on 2006-11-15
I have an old AverMedia FM98 I put in a older PIII 550 I had laying around. After much struggle, got Edgy to run on it and dmesg finds 'a BTTV' card. Got MythTV frontend working. Still struggling making the slave backend work.
*Then* I'm going to see it the Aver works... Will keep this post handy for when that time comes.
Thanks!

---

### Post by Kross on 2006-11-16
I made a small type-o

...if anyone looks..

The Phobe Master+Fm is NOT card=2

The correct card ID is 22
So then it should read as so-

options bttv card=2[COLOR="Red"]2[/COLOR][COLOR="Black"][/COLOR] tuner=2 radio=1

It is also wrong in the uploaded file....

Sorry again.

-I am also aware that there are other Options for this (such as PLL)
But I don't know what they do,,,and I am have'n trouble with my audio,,including FM

-Any Information would Be Helpful

Thank You

-Kross

---

### Post by Kross on 2006-12-07
I have found A little more Info on My BTTV card,,I placed in file .

Here it is=

[COLOR="Red"]options bttv card=22 tuner=2 radio=1 triton1=0 pll=1

#insmod args:
[INDENT]#                  remap=adr       remap Bt848 memory to adr<<20
#                  vidmem=base     frame buffer address>>20 (of graphic card)
#                  triton1=0/1     for Triton1 compatibility
#                                  T[INDENT]riton1 is automatically recognized
#                                  but this might also help with other chipsets[/INDENT]
#                  pll=0/1/2       pll settings
#                                  [INDENT]0: don't use PLL
#                                  1: 28 MHz crystal installed
#                                  2: 35 MHz crystal installed[/INDENT]
#                  radio=0/1       card supports radio
#                  card=n          card type[/COLOR][/INDENT]

Because I have no speakers at this time I can not really test the btaudio. But from what I have try'd with headfones.My is not working..But The picture is great.everything but this work wonderful.

If Anyone eles had this work please let me know. also If your sound is not working or if you know how to fix mine, help would be thankfull.

Hope this helps some.
<=Kross=>8)

---

### Post by Kross on 2006-12-29
bump

---

### Post by Kross on 2007-01-08
> **Kross said:**
> bump

bump

---

### Post by Dhaun on 2008-06-18
Great job there Kross. My video quality is great but I can barely hear anything. I mean I can hear the sound a little but I have to max out my volume on the speakers. Have you found any solution for this problem?

Now when I got my TV working on ubu, I'm really thinking of fully switching to ubuntu from winxp :P

---

### Post by Dhaun on 2008-06-22
bump.
Any way to boost the sound comming from TV card?

---

