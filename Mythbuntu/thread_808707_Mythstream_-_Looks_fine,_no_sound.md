---
title: "Mythstream - Looks fine, no sound"
date: 2008-05-26
forum: Mythbuntu
---

### Post by scottd34 on 2008-05-26
I am having issues with mythstream.  Muthbuntu with ubuntu 8.04, and most current 0.21 mythtv. Sound Blaster live usb soundcard, using coax out.

I go into mythstream and pull up any feed.  I see the equalizer, it says its playing but I get no sound at all. 

Audio works fine in every other part of mythtv.  Any ideas as to what I can look at to fix this?

---

### Post by scottd34 on 2008-05-27
nobody else is having this problem?

---

### Post by pennstatebadboy on 2008-07-10
I'm having this same problem. I have sound in everything except MythStream. Does MythStream use a player that's different? If so, It could be a matter of configuring that player. Anyone have an idea?

---

### Post by erconway1943@yahoo.com on 2008-07-10
For what is worth, I have a new iMac, running Leopard, gobs of memory.  When Ubuntu boots I get the jungle sound.  If I go to system and to sound; initiate the test, I get sound.

However, if I go to games, there is no sound.  If I go to anything on the web where there is sound; I get no sound.

I am at a loss as to where to go (please, be nice):lolflag:

Any suggestions appreciated.

Oh yes, running 8.0.4.1  64bit.


Ed

---

### Post by pennstatebadboy on 2008-07-12
bump...

Anybody know why I have no sound in everything except MythStream?

---

### Post by nickrout on 2008-07-13
what do your logs tell you?

---

### Post by dcwdrum on 2008-07-18
Are you using Analog audio or Digital?  For Mythstream, Mythmusic, and Mythvideo, the only way I am able to get audio is to use a SPDIF connection.  However, MythTv uses Analog audio, so its a pain to switch back and forth.

If you open up the terminal and type in "alsamixer"  you will pull up the sound mixer for your computer.  Use the arrow keys to scroll over to the option labeled "IEC958".  If the box has "mm" in it, that means that it is muted and disabled.  Press m on your keyboard to enable it.  If you have a digital/optical connection such as SPDIF connected to whatever you are using for sound, this should hopefully do the trick is this is the problem.  Hope this helps

---

### Post by scottd34 on 2008-08-03
> **dcwdrum said:**
> Are you using Analog audio or Digital?  For Mythstream, Mythmusic, and Mythvideo, the only way I am able to get audio is to use a SPDIF connection.  However, MythTv uses Analog audio, so its a pain to switch back and forth.

If you open up the terminal and type in "alsamixer"  you will pull up the sound mixer for your computer.  Use the arrow keys to scroll over to the option labeled "IEC958".  If the box has "mm" in it, that means that it is muted and disabled.  Press m on your keyboard to enable it.  If you have a digital/optical connection such as SPDIF connected to whatever you are using for sound, this should hopefully do the trick is this is the problem.  Hope this helps

Thats the wierd thing about it, mythvideo and mythmusic work fine. I will give alsamixer a go and see how it goes.

*EDIT*  It didnt work.  It was disabled but did nothing when I enabled iec958.

---

### Post by nickrout on 2008-08-03
What do your logs say?

---

### Post by tgm4883 on 2008-08-03
> **nickrout said:**
> What do your logs say?

It might help if you gave a little more info, like

What do you frontend logs say?  Can you post them?  The log we want to know about is at /var/log/mythtv/mythfrontend.log

---

