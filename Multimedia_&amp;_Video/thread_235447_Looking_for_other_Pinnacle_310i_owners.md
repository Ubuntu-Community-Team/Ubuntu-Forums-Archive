---
title: "Looking for other Pinnacle 310i owners"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by twotonz on 2006-08-13
Hi all
 I was just wondering if there are other users out there running dapper, with a Pinnacle 310i TV Card? The only post that mentions this card is from an user running breezy, and that's rather old. I have had an attempt to get the card working, and ended by messing the card up. 
 So basically I am calling out for other users out there, to share experiances, either good or bad. The ultimate goal would be to get mythtv going, but I am not choosy, any tv proggy would do. Comments that I really do not need is, "buy a card that is supported". My other pc has a haupauge pvr350 (which is supported, so i've done that), I would really like to get the pinnacle going as it has it's own tuner for dvb-t, which would be really nice (the hauppauge is connected to an external tuner).
 I have read the excellent thread dealling with the hauppauge/mythtv howto (recommended for everyone tring to get a tv card going, as it covers allmost everything that can go wrong!), and I think that mythtv is not the right direction for the pinnacle card (simply too complicated!), anyway eagerly awaiting any comments.........anybody?

Love & Peace
anthony

---

### Post by jesus_u on 2006-08-18
Hi Anthony:

I have a pinnacle 300i. This is not the same card but I think the main difference is that pinnacle 310i receives fm radio, and the 300i only tv.

My experience with this card is bad. In Ubuntu 5.10 I was able to make it work (more or less) with a lot of work, testing, and reading forums and experiences of other users.

Ubuntu 5.10 

In analogue mode, I could see video but no sound. 

In DVB mode, I could see video and sound. The quality of the recepcion was poor in lower frecuencies, but the card could not receive the higher frecuencies.

I think the problem was in my antenna cable, but I am not sure. 

Ubuntu 6.06 Dapper

I changed to Dapper. I though, may be, all would work fine, but the situation is worse: in analogue mode it is the same (no sound) and in DVB mode xine can not find the mrl.

I have tried all the solutions that have worked for other users, but none of them have been good for me. I am new in ubuntu and in linux too, I am learning things very slowly, and maybe I am a part of the problem. 

Good luck

Jesus

---

### Post by twotonz on 2006-08-19
Hi jesus_u,
 Thanks for your reply. You have for sure seen the stuff about having to use the oss sound-system if you want sound from the analog side?
 You actually got the dvb working? I would not mind to much using breezy, if that means I can watch tv. Can you remember if you were using the standard v4l drivers that comes with breezy, or did you compile from source? and most importantly, which card parameter did you use? 
You are the first person that has actually reported some success with this card (and I have read many, many, many forums dealing with this). At last, a small glimmer of hope?

Love & Peace (to all)
anthony

---

### Post by jesus_u on 2006-08-20
Hello Anthony:

The sound in analog side never worked for me. I tried everything (OSS, ALSA, ESD), unload modules (tuner, tda9887, saa7134, saa7134_dvb) and load again one by one (tda9987 before tuner & saa7134 and the last one saa7134_dvb)

The dvb never worked since I changed to Dapper. In Breezy it used to  worked with original drivers. I am sure of that because, all the times I have compiled anything, after that,  I have had to download and install kernel from Synaptics because the results was worse.

I have read many posts about problems of this pinnacle card with latest kernels (2.6). I can't post these urls: i remember have read that, but i don`t remember where (sorry) :( .

The parameters of my card in /etc/modprobe.d/options.d are: 

options saa7134  audio_debug=1 card=50 tuner=33
(maybe yours are slightly different, for the radio tuner). The dmesg command detetcs it perfectly.

The v4l drivers loaded now are v4l2_common and v4l1_compat. I can't be sure, but I suppose that were the same in breezy.

I don't think in using breezy anymore. Everything (except tv card)  is working properly in dapper, and I can live without tv.

Plese let everybody know if you reach any advance, o tell me if I can help you in any way.

Sorry for my english. It's not my native language. 

Until soon

---

### Post by twotonz on 2006-08-20
Aha,
Thank you very much for the info. By the way, your english is very good, you do not need to excuse yourself :-). With the sound stuff, I know what you mean, I have also read much on this subject.

I am also very happy with dapper actually, it is just boring having to have a windows partion, in order to watch/record tv, still, one cannot have everything in life!

I must also admit, I have another pc with a pvr350 (with is suberbly supported), and I am even having troubles setting that up, so 99% of the diffucties that I am having lies with my inability to understand all the concepts that go with setting up pvr under linux.

I am putting my hope in the v4l2 dev-team getting the card properly supported, not so much at being lazy, it is just that I recognise when I am beat.

Love & Peace
anthony

---

### Post by twotonz on 2006-08-23
Hallo,
 When passing card=50 to the 310i, it results in having to remove the card from the pc, to reset it. Apparently the 300 & 310 cards have a different chipset and are in no way identical. Just a word of warning to any 310i owners that may be tempted to try the above solution.
# Ermm Balin, did you have any luck making sense of the "patch"? I was looking around in the files that go with the v4l sources, and actually found a file that had code that resembled the stuff in the patch, but like I have allready said, my knowledge doesn't go so far as to know what one does with it.

Love and Peace
anthony

---

### Post by jesus_u on 2006-08-24
Hi Anthony:

I have read your last post and you are completely right. Pinnacle 300i & 310i don`t use the same chipset.

I have been looking for information and I have found this url, than could be  useful for you:

[http://www.bttv-gallery.de/](http://www.bttv-gallery.de/)

The download of the page is a bit slow because includes descriptions of many tv cards with photos. 

I think the interesting part for you is next:

other report
saa7133[0]: subsystem: 11bd:002f, board: Pinnacle PCTV 310i (saa7131E) [card=89,autodetected]

There is no much more information, only the dmesg output and the photo of the card.

Anyway take a look on it and be lucky.

Jesus

---

### Post by twotonz on 2006-08-25
Hi Jesus,
Thanks for your efforts. That was just the sort of page I was looking for. At least now I know it is possible. Card 89? Just need to know what driver he is using there. My v4l cardlist doesn't reach card 89, so it must be quite new. Anyway, thanks again for that one, very interesting site, even if it does need time!

Love & Peace
anthony

---

### Post by Dubstar_04 on 2007-03-13
Has anyone got this card working?? I have other cards working but i am struggling with this card!!

I'm not interested in the analog just the dvb. I have one saa7134 card already inatalled and working but this one is giving me a load of hassel. I have googled and googled, i've  reinstalled the v4l drivers ive removed the other card and i've also tried mythdora and knoppmyth with the card. 

my other cards are just installed by modprobing the correct module for example 

```
 sudo modprobe cx88-dvb 
```
```
 sudo modprobe saa7134-dvb 
```

and others either work straight away or after a cold reboot!!

any suggestions, it driving me crazy!!

---

### Post by Dubstar_04 on 2007-03-15
Anyone offer advice?

---

### Post by gus sett on 2007-03-15
:?: Have you visited pinnaclesys.com recently.  They are superb at tracking
their product generations and were quite helpful to me with software compatibility,
though I have a somewhat different product type, USB connect.  If you choose
this route, let know about any obstacles encountered.  The release notes are
robust, but obtaining a tech contact there for your inquiry is well worth the added 
steps by checking through the contact us section, I believe.

> **twotonz said:**
> Hi all
 I was just wondering if there are other users out there running dapper, with a Pinnacle 310i TV Card? The only post that mentions this card is from an user running breezy, and that's rather old. I have had an attempt to get the card working, and ended by messing the card up. 
 So basically I am calling out for other users out there, to share experiances, either good or bad. The ultimate goal would be to get mythtv going, but I am not choosy, any tv proggy would do. Comments that I really do not need is, "buy a card that is supported". My other pc has a haupauge pvr350 (which is supported, so i've done that), I would really like to get the pinnacle going as it has it's own tuner for dvb-t, which would be really nice (the hauppauge is connected to an external tuner).
 I have read the excellent thread dealling with the hauppauge/mythtv howto (recommended for everyone tring to get a tv card going, as it covers allmost everything that can go wrong!), and I think that mythtv is not the right direction for the pinnacle card (simply too complicated!), anyway eagerly awaiting any comments.........anybody?

Love & Peace
anthony

---

### Post by Dubstar_04 on 2007-03-16
I've just been on th pinnacle support and spoke to 3 differnt techies and thay all said that they do not support any linux o/s and that by using linux is not recommended as their hard ware is designed only for windows.

just to add the analog works just fine but who wants analog when you can have digital??

---

### Post by gustojr on 2007-03-31
That' easy.  One is premium.  The other one is diesel.

---

### Post by MadeR on 2008-01-22
I do not know if you still have problems, but with Gutsy Goat (7.10) the card is automatically found and configured.

let me know if you need help.

---

### Post by hermelinen on 2008-01-24
Are you sure about that? I also have the card Pinnacle PCTV 310i and it gets autodetected alright and configured. However, the sound still doesn't work in MythTV I can get sound by using sox and converting the stream myself but that is sooo tedious. Also it doesn't work with tvtime(Sound issue again). The other day I actually managed to get sound in mythtv from the card but all I got was crackling noise.

Any ideas?

---

### Post by MadeR on 2008-01-24
> **hermelinen said:**
> Are you sure about that? I also have the card Pinnacle PCTV 310i and it gets autodetected alright and configured. However, the sound still doesn't work in MythTV I can get sound by using sox and converting the stream myself but that is sooo tedious. Also it doesn't work with tvtime(Sound issue again). The other day I actually managed to get sound in mythtv from the card but all I got was crackling noise.

Any ideas?
Yes, I am.

I use kubuntu and watch tv with kaffeine or klear.

May be your kubunt detects as *default* soundcard the audio module of the pinnacle.
Make sure you tell alsaconfig that default soundcard is the rightone.

---

### Post by hermelinen on 2008-01-24
> **MadeR said:**
> Yes, I am.

I use kubuntu and watch tv with kaffeine or klear.

May be your kubunt detects as *default* soundcard the audio module of the pinnacle.
Make sure you tell alsaconfig that default soundcard is the rightone.

But how do you get the sound from the TV card to your ordinary sound card? Do you use a cable from the TV card to your sound card? I try to get the sound via DMA from the TV card. 

Thanks for the quick reply!

---

### Post by MadeR on 2008-01-24
> **hermelinen said:**
> But how do you get the sound from the TV card to your ordinary sound card? Do you use a cable from the TV card to your sound card? I try to get the sound via DMA from the TV card. 

Thanks for the quick reply!
I get the sound without using the cable.
if you use msn or skype we could try to chat to try to find a solution in a quicke way.


Did you select the sound card order?
*sudo asoundconf set-default-card "very nice sound card" *

---

