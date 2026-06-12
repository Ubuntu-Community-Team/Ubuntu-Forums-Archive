---
title: "Default aspect ratio in VLC and TVTIME"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by DaVinciXL on 2007-08-12
Hey guys.

I got myself a new TFT which is, unlike my old one, widescreen (16:10).

Now, everytime I start VLC or TVTIME i have to correct the aspet ratio manually and I haven't found a button labeled "set as default" yet.

Well, of course that's no big deal - but still annoying. Does anyone know how to tell these programs once and for all what aspect ratio to use?

---

### Post by rominet7777 on 2007-09-23
Hi,

I suppose you're hitting the "a" key to change to 16:9 ?
When I do so, tvtime backups the settings for me... weird it doesn't do it for you ?

You can either launch tvtime with the '-a' switch, or you can edit you configuration file ~/.tvtime/tvtime.xml :

```
sed -i -e '/Widescreen/s/value="0"/value="1"/' ~/.tvtime/tvtime.xml
```

Hope this will solve your problem... if not, I'll tell you soon because I just ordered an 16:10 new screen ;)

):P

Cheers

---

### Post by eldragon on 2007-11-14
that stretches the screen

what i think he's talking about is "apply matte" and pick the screen's aspect ratio..
that cannot be configured, or i didnt find how......
ive been trying to do this too..... :(

---

