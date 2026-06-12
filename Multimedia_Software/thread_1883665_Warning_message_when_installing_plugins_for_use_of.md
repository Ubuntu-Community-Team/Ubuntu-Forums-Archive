---
title: "Warning message when installing plugins for use of Banshee and other audio programs"
date: 2011-11-19
forum: Multimedia Software
---

### Post by wpshooter on 2011-11-19
What is the meaning of the attached warning and what action (if any) do I need to take to resolve this issue ?

Thanks.

---

### Post by beew on 2011-11-19
Open Synaptic and install those packages.

---

### Post by wpshooter on 2011-11-20
> **beew said:**
> Open Synaptic and install those packages.

All of those packages were JUST installed by/when attempting to play an MP3 file.

This is the message that appeared just AFTER that installation of those packages were/is finished.

Again, what does this message mean and what do I need to do about it ?

Thanks.

---

### Post by mc4man on 2011-11-20
> **wpshooter said:**
> All of those packages were JUST installed by/when attempting to play an MP3 file.

This is the message that appeared just AFTER that installation of those packages were/is finished.

Again, what does this message mean and what do I need to do about it ?

Thanks.

Likely nothing - do mp3's now play in the player you where using? (banshee, totem

---

### Post by wpshooter on 2011-11-20
> **mc4man said:**
> Likely nothing - do mp3's now play in the player you where using? (banshee, totem

Yes, they play just fine.

But why is this message popping up ?  If there is really some type of problem, there should be a solution to it.  If there is not really any problem then someone needs to change something so this message does not pop up.

Thanks.

---

### Post by mc4man on 2011-11-20
> **wpshooter said:**
> Yes, they play just fine.

But why is this message popping up ?  If there is really some type of problem, there should be a solution to it.  If there is not really any problem then someone needs to change something so this message does not pop up.

Thanks.

I guess a bug could be filed on though I doubt it would be fixed. The 'gnome-codec-install' generally works ok but does have some oddities like you've seen. Best to just ignore.

Another thing it does list all the possibilities, even if not completely needed. So in your case it showed the gstreamer ffmpeg plugin & the fluendo one. 
mp3 decoding in gstreamer is provided by either one, you don't need both.

Overall the ffmpeg plugin is more useful, the fluendo is specific to mp3 & licensed if that matters to an individual

---

### Post by wpshooter on 2011-11-20
> **mc4man said:**
> I guess a bug could be filed on though I doubt it would be fixed. The 'gnome-codec-install' generally works ok but does have some oddities like you've seen. Best to just ignore.

Another thing it does list all the possibilities, even if not completely needed. So in your case it showed the gstreamer ffmpeg plugin & the fluendo one. 
mp3 decoding in gstreamer is provided by either one, you don't need both.

Overall the ffmpeg plugin is more useful, the fluendo is specific to mp3 & licensed if that matters to an individual

Really needs to be fixed.

When you are trying to convince friends & associates to use this operating system and they see this kind of thing, it sure does not help you sell them on using it !!!

Thanks.

---

### Post by MoreOrLess on 2011-11-20
[https://bugs.launchpad.net/ubuntu/+source/gnome-codec-install/+bug/856943](https://bugs.launchpad.net/ubuntu/+source/gnome-codec-install/+bug/856943)

It means you have some file format in your collection without a gstreamer plugin.

---

