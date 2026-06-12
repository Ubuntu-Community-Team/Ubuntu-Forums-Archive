---
title: "Errors on Hauppauge pvr-500"
date: 2008-05-02
forum: Mythbuntu
---

### Post by jolly79 on 2008-05-02
Hi guys

Im a frequent user on the ubuntu forum, thus i dont post much.
I can usally get the info i need of others post.

But this time i cant find enybodyu that is having the same issues that i have.

I have a backend running kubuntu 8.04 with a pvr-150 and a pvr-5oo, the pvr gives a buetifull picture, but the pvr-500 give alot of snow.
I thougt i was a bad connection i cable splitter, so i pullede out the pvr-150 and i only left ind the 500 card, giving it a direkt feed from my cable.
But i still gives alot of snow.
My backend log keeps saying this:

 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not
 properly capture VBI data on PVR-250 and PVR-350 cards.


Is this a driver issue or do enyoby know o answer to this??
I had a perfect myth setup with 7.10, all thre tuners workede and gave no snow.
Would it be possible for me to run a 7.10 server with the 0.20 mythbackend and run 8.04 frontend with 0.21 myth??

Hope enybody can help me with this, because i really bugges me.


Cheers from Gustav

---

### Post by jolly79 on 2008-05-02
when i run: dmesg | egrep -i '(ivtv|tveeprom|tuner)'

i get:

[   31.678829] ivtv:  Start initialization, version 1.1.0
[   31.678911] ivtv0: Initializing card #0
[   31.678914] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   31.681959] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   31.744833] tveeprom 2-0050: Hauppauge model 23559, rev E696, serial# 9978568
[   31.744837] tveeprom 2-0050: tuner model is Samsung TCPG 6121P30A (idx 96, type 73)
[   31.744840] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   31.744843] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   31.744846] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   31.744848] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   31.744850] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   31.744852] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   31.809490] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   31.809511] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   31.809514] tuner 2-0043: type set to tda9887
[   31.813202] tuner 2-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   31.813214] tuner 2-0060: type set to tea5767
[   31.813437] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   31.856709] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   31.877230] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   31.885037] tuner-simple 2-0061: type set to 73 (Samsung TCPG 6121P30A)
[   31.885040] tuner 2-0061: type set to Samsung TCPG 6121P3
[   31.885250] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   31.885264] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   31.885279] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   31.885292] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   31.885305] ivtv0: Registered device radio0 for encoder radio
[   31.885307] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
[   31.885367] ivtv1: Initializing card #1
[   31.885370] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   31.885805] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   31.891156] tuner 3-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   31.891170] tda9887 3-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   31.891172] tuner 3-0043: type set to tda9887
[   31.894162] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   31.909211] cx25840 3-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   31.909444] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   31.978413] tveeprom 3-0050: Hauppauge model 23559, rev E696, serial# 9978568
[   31.978417] tveeprom 3-0050: tuner model is Samsung TCPG 6121P30A (idx 96, type 73)
[   31.978420] tveeprom 3-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   31.978423] tveeprom 3-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   31.978425] tveeprom 3-0050: audio processor is CX25843 (idx 37)
[   31.978427] tveeprom 3-0050: decoder processor is CX25843 (idx 30)
[   31.978429] tveeprom 3-0050: has radio, has no IR receiver, has no IR transmitter
[   31.978431] ivtv1: Correcting tveeprom data: no radio present on second unit
[   31.978433] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   32.015917] tuner-simple 3-0061: type set to 73 (Samsung TCPG 6121P30A)
[   32.015921] tuner 3-0061: type set to Samsung TCPG 6121P3
[   32.016139] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   32.016154] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   32.016170] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   32.016184] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   32.016187] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
[   32.016994] ivtv:  End initialization
[   47.889922] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   48.087504] ivtv0: Encoder revision: 0x02060039
[   52.346215] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   52.544676] ivtv1: Encoder revision: 0x02060039

---

### Post by jolly79 on 2008-05-02
Enybody???

I was maybe thinking that i was the:  31.885805] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)

That is giving me the problems.

---

### Post by jolly79 on 2008-05-02
Bump.... No help??

---

### Post by jolly79 on 2008-05-15
So nobody is having errors on their pvr-500???
Just bought a second pvr-150... and two pvr-150 workd fine.
But when ever i plug in the pvr-500 card it messes up the reception on every tuner the machine has.
Please if enyboby got eny idea of what i can do... get back to me. It would be nice to be able to use the card again.

---

### Post by ian dobson on 2008-05-15
Hi,

From what I've read there are 3 different versions of the PVR-500, 2 with philips tuner chips that work quite well and one with a Samsung tuner.

The Samsung tuners aren't that good (They are very sensitive to signal strength - Too High/Low you get a bad picture), and it looks as if you have that version, sorry.

Note the PVR-500 has 2 tuners and has an onboard amp. which can affect the picture quality. 

Sorry that I don't have a better answer than this.
Regards
Ian Dobson

---

### Post by jolly79 on 2008-05-21
hi...

nice to get an responce from some one... the wired thing is that the card workede perfect on 7.10, and now just because of the upgrade, nothing works with this card.

I dont really know how to see what tuner is in it... but i do think this is an error on mythbuntu or mythtv.

Well nothing else to do but to sell it to some of those windows users, i hear rumors that their out there somewhere :-)

-Gustav

---

### Post by novellahub on 2008-05-21
What frequency table are you using with the PVR-500?  If it is set to US Broadcast, you will not get a signal about channel 13 or so and get snow.  I have to use us-cable on mine.

---

### Post by jolly79 on 2008-05-30
Hi

I use Europe-west i live in Denmark, so that is properly the best one for me to choose.
Dont you think??

Even if i did choose the wrong one, why would only the 500 card act this way??
The 2 pvr-150 works nicely, no snow or nothing.

I was thinking it was something with the power settings, or the ivtv driver that have changed since mythbuntu 7.10.

Hate not having 3 tuners, and now with my new pvr-500 i could actually have 4 :-( 

I think it&#347; really wired no one else is having the same problems that i am having.

Thanks for the help guys... maybe i just have to put the pvr-500 on storage til mythbuntu 8.10 or somthing.

---

### Post by ian dobson on 2008-05-30
Hi,

I've got both a PVR-150 and a PVR-500 and have noticed that the PVR-150 has a better picture quality. 

Also I also noticed the the picture quality for the PVR-500 got abit worse after upgrading to 8.04.

As I've "upgraded" to DVB-C and can get almost all the channels that I want per DVB rather than analog, I just installed the PVR-150 for the issing channels and packed the PVR-500 away.

I know this doesn't help you much but from my experiance the PVR-150 always has a better picture quality than the PVR-500.

Regards
Ian Dobson

---

### Post by jensk on 2008-07-06
I have up until now been using Knoppmyth with my PVR-150 with a samsung tuner. I have experienced the same problems. I solved it by using another frimware for the samsung. I cant remember which right now but when i get home to the server i can look for it and post it here.

With the standard formware here was quality and channel poblems. With the right frmware everything sortet out fine. I can tune the channels and the quality og the picture/sound is fine.

Also in the Knopmyh discussions it is mentioned to turn of VBI in the myth-setup and not recording with 480x480 resolution. So i did this to.

I live in Denmark as you. Have you found a good card for the H.264 DVB-t that is starting in Denmark by november this year?
/JK

---

### Post by Lex148c on 2008-11-24
I am also having this problem with my Hauppauge pvr-500. It was working fine with 8.04. I’m thinking I’m going to have to downgrade to get myth working again. The weird thing is I think it was working in vlc. I will have to try again tonight to verify (not at home right now). If so this is looking more and more like an issue in mythtv

---

### Post by Lex148c on 2008-11-25
In case anyone is interested, there was an error between the keyboard and chair. I had myth set to us-broadcast not us-cable

---

