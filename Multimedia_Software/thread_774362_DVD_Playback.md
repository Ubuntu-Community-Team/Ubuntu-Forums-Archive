---
title: "DVD Playback"
date: 2008-04-29
forum: Multimedia Software
---

### Post by VitalityChernobyl on 2008-04-29
This page from the feature tour ([http://www.ubuntu.com/products/whatisubuntu/804features/music/](http://www.ubuntu.com/products/whatisubuntu/804features/music/)) claims, "By default the video player will provide DVD playback..."

So I naively inserted my DVD and the first thing I see is Totem telling me that it needs a codec to play the DVD.  So I think, ok, go get it and I click on the button to go search for it.

The only result found is a GStreamer plugin that will play unencrypted DVD's

So, basically, I am screwed.  I can't play my DVD's in Hardy Heron.

Can anyone point me to software that will allow me to play my DVD's?

Thanks in advance.

---

### Post by Ek0nomik on 2008-04-29
> **VitalityChernobyl said:**
> This page from the feature tour ([http://www.ubuntu.com/products/whatisubuntu/804features/music/](http://www.ubuntu.com/products/whatisubuntu/804features/music/)) claims, "By default the video player will provide DVD playback..."

So I naively inserted my DVD and the first thing I see is Totem telling me that it needs a codec to play the DVD.  So I think, ok, go get it and I click on the button to go search for it.

The only result found is a GStreamer plugin that will play unencrypted DVD's

So, basically, I am screwed.  I can't play my DVD's in Hardy Heron.

Can anyone point me to software that will allow me to play my DVD's?

Thanks in advance.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by VitalityChernobyl on 2008-04-29
> **Biggus said:**
> Hi dude, you could try vlc media player, it will play pretty much just about anything you want to throw at it.

Thanks Biggus.  I went to [www.videolan.org](www.videolan.org) but they don't seem to have a version for Hardy yet.

---

### Post by VitalityChernobyl on 2008-04-29
> **Ek0nomik said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Thanks for this suggestion.  The instructions on that page were very easy to follow.

After having followed them and installed the extra software, the DVD now plays in Totem, but the video is scrambled.

So, I am still stuck unless someone has another suggestion.

---

### Post by lancern on 2008-04-29
[http://ubuntuforums.org/showthread.php?t=767449](http://ubuntuforums.org/showthread.php?t=767449)

You could try reading that thread and see if anything in there helps you.

---

### Post by mc4man on 2008-04-29
you just need libdvdcss2
either add medibuntu repo to sources  -from terminal
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
``` and then
```
sudo apt-get install libdvdcss2
``` or go here and manually install
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)   
choose libdvdcss2 1.2.9-2medibuntu4_i386.deb  (27-sep-2007)

---

### Post by VitalityChernobyl on 2008-04-29
> **mc4man said:**
> you just need libdvdcss2
either add medibuntu repo to sources  -from terminal
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
``` and then
```
sudo apt-get install libdvdcss2
``` or go here and manually install
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)   
choose libdvdcss2 1.2.9-2medibuntu4_i386.deb  (27-sep-2007)

Cool, that worked.  Thanks everyone!

---

