---
title: "rhythmbox hangs in when playing netradio :S"
date: 2010-05-15
forum: Multimedia Software
---

### Post by svenskmand on 2010-05-15
When I try to play netradio in Rhythmbox it hangs. This only happens with Windows Media Streams, not with Ogg Streams, but as most internet radio is in Windows Media Streams this is a problem :(

The link I am trying to play uses the mms protocol. When I try to play the link in Movie player it also just hangs, :S, but in VLC it works, but VLC is not a very handy music player.

I suspect that I would maybe need some GStreamer plugins but which?

The link I try to play is this: mms://wmscr1.dr.dk/e04ch10m But I am not sure it will play outside Denmark, so you might not be able to this the link out yourself :S

Any ideas?

---

### Post by mc4man on 2010-05-15
You haven't said what version of ubuntu you are using...
gstreamer apps can play mms streams - in lucid and with the use of a ppa for karmic they can play most of them. (but not all

They can have an issue sometimes if stream doesn't connect promptly or if the url isn't quite complete

So while what you posted above worked here in vlc and pana - not so in totem
Making a slight adjustment allowed totem to play (I have removed rhythmbox in my lucid install

Try this instead - takes about 8 sec's or so to connect - be patient

```
mms://wmscr1.dr.dk/e04ch10m?MSWMExt=.asf
```

---

### Post by svenskmand on 2010-05-16
Nice the link mms://wmscr1.dr.dk/e04ch10m?MSWMExt=.asf worked :) but what does the extra thing you added mean? And why is it necessary? When I open up the link in VLC it does not need this stuff, and as far as I can see in the "Media Information" windows in VLC it actually plays the url mms://wmscr1.dr.dk/e04ch10m :S

But thanks for the help, now I can use Rhythmbox again :)

And by the way I have Lucid Lynx :)

---

### Post by svenskmand on 2010-05-17
What did the extra thing of
```
mms://wmscr1.dr.dk/e04ch10m?MSWMExt=.asf
```
at the end do compared to the original url which was
```
mms://wmscr1.dr.dk/e04ch10m
```
Please explain, as I would like to know :)

---

### Post by svenskmand on 2010-07-19
Also how can I get this link to play?
[http://www.kickradio.nl/tunein/WindowsMediaRadioTuner/KickRadio80s90sWithHTMLView.asx](http://www.kickradio.nl/tunein/WindowsMediaRadioTuner/KickRadio80s90sWithHTMLView.asx)

---

