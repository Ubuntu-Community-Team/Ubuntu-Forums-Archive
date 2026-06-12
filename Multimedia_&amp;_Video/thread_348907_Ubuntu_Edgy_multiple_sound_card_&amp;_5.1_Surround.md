---
title: "Ubuntu Edgy multiple sound card &amp; 5.1 Surround Sound Problem"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by spakowski on 2007-01-29
Hi,
 
I have recently shifted from Gentoo 2006.1 to Ubuntu Edgy

I have 2 sound cards in my machine 

Creative 24Bit Live (CA0106)
Nvidia nforce3 Onboard (CK8S)

I am having a major problem with sound cards interchanging after every bootup 
both the cards swaps itself after every bootup and i am unable to fix this problem at all.

"asoundconf list" output
Names of available sound cards:
CA0106
UART
CK8S

after a restart "asoundconf list" output
Names of available sound cards:
CK8S
UART
CA0106

The second part of my problem is every time i edit my .asoundrc file with
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

all the 6 speakers work properly but Xine shows no audio driver available after a restart of the machine no audio is available until i delete the lines from the .asoundrc and restart alsa

I never had Sound problems in Gentoo at all before.

Can someone please help me solve this problem pleaseeeeeeeeee

---

### Post by spakowski on 2007-01-30
Finally i got everything fixed and i am getting 5.1 surround in both the sound cards

Thank you

---

### Post by zeifertstc on 2007-01-30
Do you think you could tell me the full procedure for getting Surround Sound to work on Ubuntu Edgy? I have a Sound Blaster Audigy 24-bit CA0106 similar to your own. I only have a 5.1 setup, I'm guessing that 6 channels must be used in order to make the powered subwoofer function? 

I am still somewhat new to linux despite my various uninstall/re-install attempts. The procedure you followed would be of great help to me.

Thank you.

---

