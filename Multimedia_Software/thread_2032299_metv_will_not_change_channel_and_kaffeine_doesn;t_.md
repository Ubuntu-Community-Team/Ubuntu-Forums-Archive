---
title: "metv will not change channel and kaffeine doesn;t work"
date: 2012-07-23
forum: Multimedia Software
---

### Post by qwertyjjj on 2012-07-23
My dvbt is working and metv added a load of channels on autosearch. However, when I go to channels and click on one and press ok it never changes channel?

Secondly, kaffeine won't list any channels at all. I go to device and select uk-Crystal Palace and then start search and it says device not found.

Any ideas what I can do?
I am using a avertv voltar HD PRO a385

---

### Post by asmoore82 on 2012-07-23
I've always done a channel scan with the command line dvb tools. Actually I do multiple scans with the antenna pointed different directions; then splice the channel.conf files together by hand.

It might be worth checking out the latest version of metv from source or a PPA. Awesome program.

---

### Post by qwertyjjj on 2012-07-24
> **asmoore82 said:**
> I've always done a channel scan with the command line dvb tools. Actually I do multiple scans with the antenna pointed different directions; then splice the channel.conf files together by hand.

It might be worth checking out the latest version of metv from source or a PPA. Awesome program.

The channel scan works and picks up channels but I just can't change channel.
I open up metv, go to view-->channels, then click on another channel and press ok and it doesn;t change.

Any why won;t kaffeine see channels when metv can?
Kaffeine says no available device found when I start a scan even though it has selected a dvbt device

---

### Post by asmoore82 on 2012-07-24
MeTV used to stay running in the tray even after closing it, so it could do its auto-recording function. If you're on the new Unity interface, it may be very difficult to notice that it's still running.

It may be worth a complete reboot, and then immediately try kaffeine before launching metv, just to make sure that's not the issue.

---

### Post by oldos2er on 2012-07-24
Moved to Multimedia & Video.

---

### Post by jimmac49 on 2012-07-24
I use an AverMedia Volar DV3 T, with Kaffeine, and when I choose an Individual area to scan, I get no results, but when I choose Auto-Scan, I get lots of TV and Radio channels.

Its worth a try at least.

Luck

---

### Post by jimmac49 on 2012-07-24
As an also have you configured Television?, under kaffeine

Luck

---

### Post by qwertyjjj on 2012-07-25
> **jimmac49 said:**
> I use an AverMedia Volar DV3 T, with Kaffeine, and when I choose an Individual area to scan, I get no results, but when I choose Auto-Scan, I get lots of TV and Radio channels.

Its worth a try at least.

Luck

That seems to work.
Thanks

---

### Post by John3e on 2012-07-28
I have the same problem with DVB-T ( SAA7134/SAA7135HL from Medion ) in Me-Tv. Can't find way to change channel :(. 
Mabe there is some  bug?
Kaffeine works ok. But in Me-Tv i can't change channel, epg event search works and shows other channels. 

ps standard scan files dindn't work for me so i edited it, then rescaned for new channels.
Best regards,
Lucas

---

### Post by thesaint4cs on 2013-01-29
In Me-TV the channel selection area might not be visible. 
You can pull it up using the mouse: The cursor will change when you place it at the top of the bottom tool-bar, then you can click left, hold and move up.
You might have to "Change View Mode" first, which will toggle visibility of the  channel selection area.

Best regards,
thesaint4cs

---

