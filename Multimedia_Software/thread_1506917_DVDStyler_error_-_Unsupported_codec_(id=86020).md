---
title: "DVDStyler error - Unsupported codec (id=86020)"
date: 2010-06-10
forum: Multimedia Software
---

### Post by earther on 2010-06-10
I have been using DVDStyler 1.7.0 for years on Gutsy Gibbon to create DVDs from mpgs created by Avidemux.2.4 (r3322).  I can't remember what it took to get it working it's so long ago.  All I know is that it's never failed me.

Last week, I finally installed Hardy Heron (clean install not upgrade).  Avidemux creates the mpgs as before.  But DVDStyler fails with this error:

> Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86020) for input stream #0.1
Error by transcoding of /home/xxxxx/Videos/projects/602final/disk1/2_608.mpg

I have been Googling for hours trying to find a solution and coming up empty.  PLEASE help me get DVDStyler working again.

Thanks for you help.

earther

---

### Post by WinterRain on 2010-06-11
This may seem obvious, but did you install libdvdcss2 and codecs?

---

### Post by earther on 2010-06-11
> **WinterRain said:**
> This may seem obvious, but did you install libdvdcss2 and codecs?
DUH!  As I said, it's been a long time since I last struggled with this.

I just installed libdvdcss2 and non-free-codecs but still no joy. I would just go ahead and install ubuntu-restricted-packages but I don't want Flash.  I'm not quite sure exactly what packages I need just to create set top playable DVDs with menus.

As I said Avidemux seems to be working properly - mpeg encoded on Hardy worked in DVDStyler on Gutsy but throwing the error on Hardy.  Any specific suggestion would be very welcomed.  Thanks.

I can play disks on Hardy - no problem.

[**This thread**]("http://ubuntuforums.org/showthread.php?t=766683") seems to have the answer buried somewhere in it but I'm having a hard time sorting it out.

---

### Post by earther on 2010-06-12
OK.  I followed instructions in that thread (omitting Flash and Sun Java) but DVDStyler is still throwing up the error.

What am I missing here?  Please help!!

---

### Post by mc4man on 2010-06-12
Don't have a hardy install handy but the error seems to be the audio stream (ac3  ..?)

Maybe try adding medibuntu and updating the ffmpeg libs (libavcodec1d, libavformat1d, ect.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by earther on 2010-06-12
> **mc4man said:**
> Don't have a hardy install handy but the error seems to be the audio stream (ac3  ..?)

Maybe try adding medibuntu and updating the ffmpeg libs (libavcodec1d, libavformat1d, ect.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Thanks for the suggestion.  Have already done the Medibuntu thing. Maybe I should install the dev packages too?

---

### Post by earther on 2010-06-12
Reread your suggestion and UPDATED the packages.  It's now creating the ISO.  Unfortunately, there are no menu buttons and sound is coming on track 2 on VLC.  More things to fix . . .

---

### Post by earther on 2010-06-13
Have FINALLY gotten everything sorted.  VLC started to behave once it was set as the default player.

---

