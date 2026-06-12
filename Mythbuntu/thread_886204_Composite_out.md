---
title: "Composite out"
date: 2008-08-10
forum: Mythbuntu
---

### Post by nightwar on 2008-08-10
Hello.

Backround: not new to unix/linux, not new to mythtv.. I have a working setup, 1 backend, 1 frontend, 1 fileserver for media(running freebsd).

Obective: put mythbuntu box in kid's rooms

Problem: Composite video inputs!(RCA)

This is what i have tried so far, rage ati 128 pro card, built in composite out, got a display, but does not render quick enough, more like 2 frames a second.. 

matrox g450(older card), dual head.. comes with a vga to svideo/composite RCA "adapter"

system boots ,no display, oncef x starts, the screen comes on but it looks like its out of sync or something? not sure, tried every driver on the planet i think.


My obvious answer, get a Svideo to RCA converter, or a better tv.

TV's are simple 13 inch or 14 inch TV.  What is the best route? Try to find some older cheap video cards with builtin RCA outputs, or grab  a converter? 

I had thought that the rage 128 pro with builtin RCA out would have been a simple 10.00 card i could pick up a few on ebay or something, but im having such a driver issue, id like to refrain from buying all new tv's for now..

---

### Post by nickrout on 2008-08-10
avoid ati cards. go for nvidia with tv out, composite if you can, alternatively s-video with a convertor. The convertors are very simple and cheap, eg

[http://www.dse.co.nz/cgi-bin/dse.storefront/en/product/P1471](http://www.dse.co.nz/cgi-bin/dse.storefront/en/product/P1471)

---

### Post by SiHa on 2008-08-11
> "avoid ati cards. go for nvidia"
I'll second that - two weeks to (fail to) get something out of on-board ATI rubbish. ATI Linux drivers just aren't up to scratch.

Also - some Nvidia (eg 7200)cards have a multifunctional VIVO (Video In Video Out) port (9 or 10-pin) in place of standard S-Video. If you're buying second hand, ensure that you get the video adaptor cable that comes with it. A standard S-Video cable is supposed to work (according to Tech Support), but didn't for me, just got B&W - 'Y', but no 'C'. 
I had to randomly experiment, and now have a bit of 75ohm coax soldered onto pin 5 for my composite out. 
There are several '9-Pin Mini-Din' pinouts on the web, none was correct for the above PNY FX7200 card.

---

### Post by Nate B. on 2008-08-11
Beware that an older TV (like my Zenith from 1993) may not work well with an S-Video to composite adapter cable.  I'm using an Averkey Micro for feeding my TV, but I don't think it is well suited for scenes with a lot of motion, such as an auto race.  Also it seems to gradiate the color to such an extent that shading is quite noticable.  I presume the Averkey is more suitable for presentations of slides than full motion video.

The good thing about Myth is that it works beautifully.  The bad thing about Myth is that it has me thinking seriously about upgrading my venerable TV set.  :)

---

