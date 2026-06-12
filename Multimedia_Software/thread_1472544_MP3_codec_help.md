---
title: "MP3 codec help"
date: 2010-05-04
forum: Multimedia Software
---

### Post by mbrady76 on 2010-05-04
All, I've used unix/linux stuff sporadically for some time.  I'm not a novice user, but not advanced.  I'd like to listen to MP3 files.  I understand there are patent / restrictions on this type of thing.  Why is it in Ubuntu 10 that I now get messages looking for codec players and want to install the gstreamer0.10-  utilities and I have to agree that it's legal in my country, USA, to do so.  Why is this?  All kinds of MP3 players that I have used in the past windows and UNIX alike didn't have these kinds of messages.  Is using the gstreamer0.10- utilities even legal in the USA?

---

### Post by tsucol11 on 2010-05-04
> **mbrady76 said:**
> All, I've used unix/linux stuff sporadically for some time.  I'm not a novice user, but not advanced.  I'd like to listen to MP3 files.  I understand there are patent / restrictions on this type of thing.  Why is it in Ubuntu 10 that I now get messages looking for codec players and want to install the gstreamer0.10-  utilities and I have to agree that it's legal in my country, USA, to do so.  Why is this?  All kinds of MP3 players that I have used in the past windows and UNIX alike didn't have these kinds of messages.  Is using the gstreamer0.10- utilities even legal in the USA?


In some countries, the US for example, it is illegal to download & play MP3's. Since Ubuntu is being deployed worldwide it has to take certain legalities under consideration. Bottom line you install the codex your are responsible for the outcome. There is also the fact that certain programs/code are not open source.

I doubt that the US music industry will take you to court over using Gstreamer to listen to your music.

Brian

---

### Post by tgalati4 on 2010-05-04
More specifically, in the US, it requires a license from Thomson Electric ([http://www.mp3licensing.com/royalty/emd.html](http://www.mp3licensing.com/royalty/emd.html)).  You've paid $2000 for your license haven't you?

Relax, there is a personal exlusion clause (in the link above) that allows royalty-free mp3 encoding for personal/non-profit use.  Phew.

So if you want to set up your own little independent radio station (US-based) and stream mp3 music, expect a phone call or letter.

The hoops that you have to jump through separate your actions from Ubuntu/Canonical's actions, since they are not legally allowed to distribute the mp3 codec (since they didn't license it) to the US.  But you can download the source code for LAME (Lame ain't an mp3 encoder) and compile it yourself). 

Before this, you had to search the forums for how-to's, enable the restricted repository and install such codecs without consenting to the legality.  Now it's automatic.

Thankfully there are not patents on Air, otherwise you would have to pay royalties to breathe.

---

