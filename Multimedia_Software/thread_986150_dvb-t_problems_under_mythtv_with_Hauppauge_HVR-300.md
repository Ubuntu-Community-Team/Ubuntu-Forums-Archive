---
title: "dvb-t problems under mythtv with Hauppauge HVR-3000"
date: 2008-11-18
forum: Multimedia Software
---

### Post by nicola76b on 2008-11-18
Hi all,
With Ubuntu 8.10 (original kernel) and steve toth driver I get work this card.
The card kork almost well on kaffeine; but does not work under mythtv. Any tips?
Under Mythtv works ONLY analogic and dvb-s, but I CAN'T select dvb-t, that it is the only one I needed..

Please help me, or address me.. I search on web but I don't find anything...

Best regards,
   -nicola

---

### Post by Bloemetjesgordijn on 2008-11-19
Nicola


Can you please tell me how you got it working on kaffeine??

Which Steven Toth driver dit you use, the 
s2-mfe-6b6e9be35963.tar.bz2 (and what did you do then??)
or the patch with "hg clone -r 8894 http://linuxtv.org/hg/~stoth/s2-mfe"??

Thx.

Bloemetjesgordijn

Nicola,

I just found a link for you , this might help....[http://ubuntuforums.org/showthread.php?t=884456&highlight=hvr+3000](http://ubuntuforums.org/showthread.php?t=884456&highlight=hvr+3000) & 
[http://wiki.linux.net.nz/FreeViewMythTvSetup](http://wiki.linux.net.nz/FreeViewMythTvSetup)

---

### Post by nicola76b on 2008-11-19
I lost a lot of time because I try to install it on vanilla kernel.
I format all (..sigh..), I reinstall ubuntu 8.10, with kernel headers.
I follow this guide: "http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000"
with method 1 (Steve Toth's repository (22 Sep 2008)), but instead download this sources, I open 
"http://linuxtv.org/hg/~stoth/s2-mfe/" and download tar.bz2 in the top of the screen...

Remember: on ubuntu you need to delete the "original" modules for cx88 and saa7134 

make, make install
RESTART PC!!!!
and that's it!!!


hope this helps...

ATTENTION!! I cannot get dvb-t work under mythtv (it is not selectable), I must use kaffeine, if someone give me a tip THANKS A LOT

---

### Post by nicola76b on 2008-11-20
I get it work also mythtv, but ONLY dvb-s and analogic tv. I need dvb-t.

Has anybody get it work? (sure, into mythtv..)

The problem is that mythtv recognize the card DVB "DTV capture card (v3.x)" as hauppauge BUT in the below field (where it SHOULD be selectable "0" for dvb-s and "1" for dvb-t) it's ONLY displayed "0".

How can I make "1" choiche?
In the system there is, the proofs is that it is present also in /dev/dvb an WORKS with caffeine...

Bloemetjesgordijn, I try to follow your links but they didn't help me... Have you get the card working? Try with mythtv?

Thank you everybody,
  -nicola

---

### Post by Bloemetjesgordijn on 2008-11-20
> **nicola76b said:**
> I lost a lot of time because I try to install it on vanilla kernel.
I format all (..sigh..), I reinstall ubuntu 8.10, with kernel headers.
I follow this guide: "http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000"
with method 1 (Steve Toth's repository (22 Sep 2008)), but instead download this sources, I open 
"http://linuxtv.org/hg/~stoth/s2-mfe/" and download tar.bz2 in the top of the screen...

Remember: on ubuntu you need to delete the "original" modules for cx88 and saa7134 

make, make install
RESTART PC!!!!
and that's it!!!



Thx man I wil give it a go this evening. (If the wife lets me :)) And will give a status update.


> **nicola76b said:**
> ATTENTION!! I cannot get dvb-t work under mythtv (it is not selectable), I must use kaffeine, if someone give me a tip THANKS A LOT

I am afraid I cannot help you here. My knowledge on Mythv is even lower then my phatetic knowledge of Ubuntu / Linux

However I am planning to use MEtv instead of Mythtv. Maybe in this MeTV it is selectable .....? (If memory serves me correct, MeTV is available in synaptic)


Cheerz 

Bloemetjesgordijn

---

### Post by Bloemetjesgordijn on 2008-11-20
Well I had some spare time but no success

I followed the instructions of nicola76b

Installed Kaffeine and I see the following:
Conexant CX22702 DBV-T
type: Antenna

and

Conexant CX24123/CX24109
type: Satelite


However, I think it should be analogue ... and I cant find any channels

So how can I set the Kaffeine to analogue....??


This card is driving me up the walls

Cheerz

Bloemetjesgordijn

---

### Post by nicola76b on 2008-11-21
I founf that "Multiple dvb different dvb cards" (that it seem exactly my problem); 
[http://www.mythtv.org/wiki/index.php/User:Grueni#Setup](http://www.mythtv.org/wiki/index.php/User:Grueni#Setup)
can someone translate me?!?!?

what should I do to work with dbv-t?!?!

Regards,
   -nicola

---

### Post by Bloemetjesgordijn on 2008-11-21
> **nicola76b said:**
> I founf that "Multiple dvb different dvb cards" (that it seem exactly my problem); 
[http://www.mythtv.org/wiki/index.php/User:Grueni#Setup](http://www.mythtv.org/wiki/index.php/User:Grueni#Setup)
can someone translate me?!?!?

what should I do to work with dbv-t?!?!

Regards,
   -nicola

Thx I will try it out at home.

It seems that it also should / could work for you. If it works, and I understand it...I will try to make a howto

By the way

If I run scan -c the following message appear: 
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)


Maybe my firmware (fo the HVR3000) is not upgraded???
Do you know how to check the version of the firmware on the HVR3000???

Getting close  :)


Cheerz

Bloemetjesgordijn

---

### Post by nicola76b on 2008-11-21
sorry, I'm not so good linux user...
I'm a bit new in this word, but I like it!!
Have you try with my tips?
Have you reistalled - with 8.10?

Probably till monday I don't open pc...

Regards,
   nicola

---

### Post by Bloemetjesgordijn on 2008-11-21
Well I suck at linux and this HVR 3000 problem isnt improving my feeling

Sidenote
I am googling around the web in trying to solve this and each time I google for HVR 3000 and ubuntu your name pops up :lolflag:

I am trying your tips as we 'speak'

This TV card is eating away my freetime, and still not working :(

I can kiss the person who can help me...(hope its a girl though)

Cheerz

Bloemetjesgordijn

---

### Post by nicola76b on 2008-11-23
As I told you I spent A LOT OF TIME in forums to get it work this card, but I don't receive good answer from anybody.
if your dmesg feel ok and you already installed steve toth patch, I think you have to change kaffeine sat settings.
Reading you previous posts I understand you have some problems with "scan", but I didn't install the corresponding package so I haven't this command to test..

I remember (for dvb-s) I have changed on menu DVB->Configure DVB on device Conexant cx24123/cx24109 "LNB 1 setting.." Universal LNB, (before I can't get any channel) but, this depends of you sat hardware..  

I want underline that I'm not try to helping you for "your kiss"...  ;-)

-nicola

---

