---
title: "Fluendo and Totem problem"
date: 2013-01-09
forum: Multimedia Software
---

### Post by Meister Kreig on 2013-01-09
I have paid for and downloaded the fluendo complete pack but I can still not play dvds on my computer and totem says that it does not have the resources for it. Is fluendo being used by totem or does this package not support commercial dvds?

Thanks for any help as this is frustrating me.

---

### Post by evilsoup on 2013-01-09
I haven't used any of the Fluendo stuff, but I'm pretty sure that they supply a separate software DVD player, rather than a plugin for gstreamer for decoding DVDs (which is what Totem would need). It's called Fluendo DVD Player, and it's in the software centre. I have no idea if it is included in the Fluendo Complete Pack, but it sounds as though it should be.

---

### Post by TOMBSTONEV2 on 2013-01-09
Perhaps install VLC Media Player to play your DVD's, I find it has smoother playback anyway. If you feel this is what you would like to do;
```

sudo apt-get install vlc
```

---

### Post by evilsoup on 2013-01-09
I'm assuming that OP is using the Fluendo stuff for legal reasons, and libdvdcss (which VLC needs for playing back encrypted commercial DVDs) would fall within that area.

---

### Post by Meister Kreig on 2013-01-09
Yeah, I'm using fluendo because of legal purposes. So, I would need their player in order to run dvds? That is kind of annoying. I've already tried vlc which doesn't do anything.

---

### Post by BicyclerBoy on 2013-01-09
No help with Fluendo..I assumed it was just some codecs..

VLC (for linux) does not include or install libdvdcss.
A windows build of VLC includes static libdvdcss.

see playback of restricted formats on/in the Ubuntu wiki.

AFAIK Having libdvdcss is not illegal because it does not contain any stolen/extracted player keys; it generates theoretical valid keys.

Using it to defeat DRM is a different story..

---

### Post by mc4man on 2013-01-09
if you got the ["Fluendo DVD Player"]("http://www.fluendo.com/shop/product/fluendo-dvd-player/") then you should get commercial  dvd playback. If so & not working you should take up with or attempt to with Fluendo

If you just got the  ['Codec Pack']("http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/"), then commercial dvd is not included.
(unless you have some personal objection or want the fluendo dvd player, then feel free to install libdvdcss2, no one cares, not at all.

---

### Post by Meister Kreig on 2013-01-10
Thanks for the help! I'll just get around to getting the dvd player one of these days. I'll just settle with what I have first.

---

