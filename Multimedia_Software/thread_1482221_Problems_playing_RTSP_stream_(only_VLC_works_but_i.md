---
title: "Problems playing RTSP stream (only VLC works but it lags)"
date: 2010-05-13
forum: Multimedia Software
---

### Post by d3sm0nd on 2010-05-13
Hi all,

I'm new to the forum but I have general linux knowledge and i'm working in an IT department... so be prepared for a real challenge... :D
I'm using the latest version - Ubuntu Lucid Lynx.

It's all about a live tv stream from a bulgarian site ([www.bgtelevizor.net]("http://www.bgtelevizor.net")). It's a paid service and it's working perfect under Windows. I've tried several ways to run the stream... totem, xine, mplayer (yes with w32 codecs and stuff)... all of them and all of the mozilla browser plugins... nothing worked. 
I think it's a special stream (Not sure but i think it's LIVE555) because mplayer is showing me a error message that it's a ASF stream and it can't be opened even with w32 codecs... I've been googling this and found a solution - [http://bisqwit.iki.fi/source/ms-rtsp-dump/](http://bisqwit.iki.fi/source/ms-rtsp-dump/) but I don't have PHP and I don't think that this is a proper solution... there must be an other way!

The only way that works is with this addon - [https://addons.mozilla.org/en-US/firefox/addon/446/](https://addons.mozilla.org/en-US/firefox/addon/446/) (MediaPlayerConnectivity). It finds the rtsp url and is able to open it with VLC.

The stream works but it's very slow and the lag is big. I've tried to set low and large caching size (yes, for both rtsp-caching and realrtsp-caching)... and it's still laging even with a 30s caching!!!

I've spent 3 hours trying to find a solution but couldn't... hope someone here is able to help me!

Thanks in advance

---

### Post by d3sm0nd on 2010-05-14
Is nobody able to help me? :(

---

### Post by andrew.46 on 2010-05-14
Hi d3wm0nd,

> **d3sm0nd said:**
> Is nobody able to help me? :(

Can you give the exact stream address? I had a look at the page but could not decipher the ?Bulgarian text.

Andrew

---

### Post by d3sm0nd on 2010-05-14
> **andrew.46 said:**
> Hi d3wm0nd,



Can you give the exact stream address? I had a look at the page but could not decipher the ?Bulgarian text.

Andrew

Hi and thanks for your answer, andrew!
Here one stream for example:
rtsp://74.63.102.80/onlineNOVA

BTW, there are several stream urls, as it's a paid service i suppose it has some kind of protection, here i sniffed all urls with urlsnooper:
[http://i40.tinypic.com/2upv7g4.png](http://i40.tinypic.com/2upv7g4.png)

---

### Post by andrew.46 on 2010-05-15
Hi d3sm0nd,

I am afraid that I could only duplicate your findings, MPlayer would not play the stream at all on my system and vlc had no trouble but in fits and starts. With any luck mc4man will see this thread, he has much more experience with caching and vlc...

Andrew

---

### Post by d3sm0nd on 2010-05-15
> **andrew.46 said:**
> Hi d3sm0nd,

I am afraid that I could only duplicate your findings, MPlayer would not play the stream at all on my system and vlc had no trouble but in fits and starts. With any luck mc4man will see this thread, he has much more experience with caching and vlc...

Andrew

Thanks for your time! In worst case i'm thinking to try Firefox on WINE... but this would be very laggy.

EDIT: Tried and it doesn't work... I am not able to install WMP on WINE :D

---

