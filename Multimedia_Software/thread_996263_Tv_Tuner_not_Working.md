---
title: "Tv Tuner not Working"
date: 2008-11-28
forum: Multimedia Software
---

### Post by wandman on 2008-11-28
I am trying to get my TV card to work with Ubuntu 8.10.

I tried using it via Totem by selecting the "Watch TV on DVB adapter 0" option after using w_scan to find the TV channels. It seems to have found the channels successfully as they appear down the side in Totem but I just have a black screen when I try and watch TV. I have tried TVTime and xawtv and both programs just have black screens.

My card is a Hauppauge WinTV 88x

Any help would be hugely appreciated.

---

### Post by steefjeqv on 2008-11-29
Hi,

Give Kaffeine a try.
It's available in the Ubuntu repo.

Greetings,
Steven

---

### Post by wolfen69 on 2008-11-29
try vlc. go to file>open capture device>dvb tab>click OK. if you get a picture, download ivtv-utils from synaptic, then you can do ```
ivtv-tune -c25
``` 25 being the channel #.

---

### Post by wandman on 2008-11-29
Hi guys,

Thank you to both of you for helping me out. I tried both Kaffeine and VLC.

Kaffeine worked fine but I couldn't get VLC to show any picture.

I am enjoying Kaffeine though, it seems really good.

Thanks for your help.

---

