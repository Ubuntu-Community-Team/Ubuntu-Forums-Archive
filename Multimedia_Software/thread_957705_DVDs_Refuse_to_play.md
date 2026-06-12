---
title: "DVDs Refuse to play"
date: 2008-10-24
forum: Multimedia Software
---

### Post by CorrosiveMonkey on 2008-10-24
I cannot seem to get DVDs to play in my Ubuntu installation.  The disk is recognised and is mounted by Ubuntu, but VLC and Totem refuse to play.

in VLC I select the open disk leave the settings as default and press ok

in Totem when I tell it to play the DVD an error message pops up saying it could not read from resource.

I've tried following the steps in the sticky at the top of the page but it hasn't helped.

Any ideas?

---

### Post by tonyh6243 on 2008-10-24
Try these steps

> [sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list]
[sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update]
[sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w32codecs]


---

### Post by CorrosiveMonkey on 2008-10-24
it says w32codecs has no installation candidate.

the DVDs still don't play

---

### Post by xc3RnbFO8P on 2008-10-24
You did install Ubuntu Hardy 32 bit?

---

### Post by CorrosiveMonkey on 2008-10-24
no 64 bit

---

### Post by xc3RnbFO8P on 2008-10-24
> no 64 bit
then read this:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by CorrosiveMonkey on 2008-10-24
Thanks, it's working now

---

### Post by xc3RnbFO8P on 2008-10-24
And this to:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

