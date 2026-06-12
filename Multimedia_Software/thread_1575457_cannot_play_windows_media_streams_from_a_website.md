---
title: "cannot play windows media streams from a website"
date: 2010-09-15
forum: Multimedia Software
---

### Post by darklord06 on 2010-09-15
hello,
I am having problems listening to windows media streams from a particular website ( [http://radiotime.com](http://radiotime.com) ) whenever I try to listen to a stream from firefox, the page loads then connects but i have no sound (i am actually trying to listen to those two chinese radios [http://radiotime.com/station/s_112232/Chongqing_Radio_-_Stories_1035.aspx](http://radiotime.com/station/s_112232/Chongqing_Radio_-_Stories_1035.aspx) and [http://radiotime.com/station/s_103949/Beijing_Radio_-_Stories_603.aspx](http://radiotime.com/station/s_103949/Beijing_Radio_-_Stories_603.aspx)) 
I have the mplayerplug-in/gecko-mediaplayer installed, but it doesn't work, I tought that maybe there was a problem with that plugin so I deactivated it and installed the vlc plugin, after restarting firefox and trying to listen to those streams again, the vlc plugin tried to read it but it still would not work.
I even tried to install the Silverlight Plug-In without any result, does anybody know what I could do to make windows media audio streams work ? it is wierd because i seem to be able to watch windows media video streams from other websites, but i cannot listen to any stream from this one, it used to work for mp3 streams only, but after desinstalling/resinstalling the mplayer plug in, it doesn't work anymore on this website.

I can listen to those streams without any problem under windows 7, so the problem isn't coming from the website.

thank you

---

### Post by ron999 on 2010-09-15
Hi

Those streams won't play for me either.
Maybe the Radiotime website will only allow access to Internet Explorer or Windows.

Play them with VLC instead.;)
Like this:-

```
vlc mms://v1.cbg.cn/dushi
```

and this:-

```
vlc mms://alive.rbc.cn/am603
```

---

### Post by mc4man on 2010-09-15
They play here in firefox 3.6.9 though not in firefox 4.0b6 (the difference is the former has the mediaplayerconnectivity ext.
It actually is using vlc anyway so Ron's suggestion is the best way..

(Ron - where did you find the mms's - couldn't locate them here..?

---

### Post by ron999 on 2010-09-15
> **mc4man said:**
> They play here in firefox 3.6.9 though not in firefox 4.0b6 (the difference is the former has the mediaplayerconnectivity ext.

Aha, I'm using Firefox-4.0b5.
(I never heard of 'mediaplayerconnectivity ext')

Those links came from Mr Google.;)

---

### Post by mc4man on 2010-09-15
I'm using the beta also usually but have taken to  using the foxtester ext. which allows using multiple versions of firefox or switching defaults quite easy.

I forgot I had the mediaplayer.... installed on 3.6 till I noticed the site player saying it was using vlc
(the mediaplayer... ext won't work on the beta

---

### Post by darklord06 on 2010-09-16
it works ! thank you for the links ron999 !

---

