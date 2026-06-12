---
title: "radio player in Mozilla problems"
date: 2008-07-27
forum: Multimedia Software
---

### Post by ra2008 on 2008-07-27
when i play a radio here is what i get:[ATTACH]79143[/ATTACH]
the player is not show, no buttons only black screen.my firefox is up to date.
any hints?

---

### Post by gandaran on 2008-07-28
I tried this same radio in firefox with the gstreamer totem plugin and it works just fine, also tried it in opera with mplayer plugin and it didn't work! but some other radios on the same webpage work, mplayer plugin is not very good on online streaming.
now, which media plugin have you installed for firefox?
do you have the codecs/plugins installed (gstreamer plugins for totem)
does this only happen with this radio?

if you haven't installed anything yet, install this package **ubuntu-restricted-extras** find it in add/remove or synaptic.

---

### Post by ra2008 on 2008-07-28
> **gandaran said:**
> I tried this same radio in firefox with the gstreamer totem plugin and it works just fine, also tried it in opera with mplayer plugin and it didn't work! but some other radios on the same webpage work, mplayer plugin is not very good on online streaming.
now, which media plugin have you installed for firefox?
do you have the codecs/plugins installed (gstreamer plugins for totem)
does this only happen with this radio?

if you haven't installed anything yet, install this package **ubuntu-restricted-extras** find it in add/remove or synaptic.

hi,
actually it happens with all radios.
now music plays but i still have th black screen as in the image.
i have all the plugins in firefox. 
how u choose which lugin to play the muscic in firefox? is it by enable disable a specific one?
thanks

---

### Post by gandaran on 2008-07-28
> now music plays but i still have th black screen as in the image

check with synaptic if totem-mozilla is installed, if you don't like the totem-mozilla plugin, you just remove it and install another mozilla player plugin, there are many in synaptic.

---

### Post by ra2008 on 2008-07-28
now it works fine after installing gecko-mediaplayer plugin,

---

### Post by ra2008 on 2008-08-12
actually the problem of bllack screeen is because of VLC plugin.
i removed it and now it works fine,,,,,

---

