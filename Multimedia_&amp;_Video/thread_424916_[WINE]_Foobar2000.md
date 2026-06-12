---
title: "[WINE] Foobar2000"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by Crackh34d on 2007-04-27
I really love Ubuntu but I haven't found a real equivalent for Foobar2000.
So I installed it with Wine. However, it won't play my mp3 or OGG files. When I press play it just won't start

Rhythmbox does play these files. 


Any solution?

---

### Post by dreadlord_chris on 2007-04-27
> **Crackh34d said:**
> I really love Ubuntu but I haven't found a real equivalent for Foobar2000.
So I installed it with Wine. However, it won't play my mp3 or OGG files. When I press play it just won't start

Rhythmbox does play these files. 


Any solution?

Ya, I haven't found anything to replace foobar myself. You can try to get your sound working by following the advice here: [http://appdb.winehq.org/appview.php?iVersionId=3429](http://appdb.winehq.org/appview.php?iVersionId=3429)

From my experience though - even if you do get the sound working in foobar, you're not going to be happy with it. If you try to do **anything**, including just moving the mouse, while foobar's playing the audio will start stuttering very bad. I found it completely unusable as an audio player w/wine.

The only thing I use foobar for now is tagging/management.

Quod Libet is about the closest I've found as a replacement - it has alot of potential, but it does have some issues reading some ID3 tags created by foobar.

---

### Post by Crackh34d on 2007-04-28
> **dreadlord_chris said:**
> Ya, I haven't found anything to replace foobar myself. You can try to get your sound working by following the advice here: [http://appdb.winehq.org/appview.php?iVersionId=3429](http://appdb.winehq.org/appview.php?iVersionId=3429)

From my experience though - even if you do get the sound working in foobar, you're not going to be happy with it. If you try to do **anything**, including just moving the mouse, while foobar's playing the audio will start stuttering very bad. I found it completely unusable as an audio player w/wine.

The only thing I use foobar for now is tagging/management.

Quod Libet is about the closest I've found as a replacement - it has alot of potential, but it does have some issues reading some ID3 tags created by foobar.

Thx, Quod Libet looks really good although I can't add any of my MP3/OGG. It keeps saying 0 songs, No Time Information on the bottom of the screen. Google won't help me here

---

### Post by dreadlord_chris on 2007-04-28
You need to install the codecs:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Should point you in the right direction

---

### Post by Crackh34d on 2007-04-29
Thx that worked. I thought because rythmbox already played Mp3's the codec would be already installed

---

### Post by dreadlord_chris on 2007-04-30
> **Crackh34d said:**
> Thx that worked. I thought because rythmbox already played Mp3's the codec would be already installed

Different players will often use different codecs (unfortunately) - basically it depends on the *backend* the player uses.

---

### Post by michux on 2007-05-13
> **Crackh34d said:**
> I really love Ubuntu but I haven't found a real equivalent for Foobar2000.
So I installed it with Wine. However, it won't play my mp3 or OGG files. When I press play it just won't start

Rhythmbox does play these files. 

Any solution?

Of course Rhythmbox plays these file, like any other Linux audio player. You only need codecs which are player-independent.

For a Foobar-close check out MESK, here is a review: [Mesk Audio Player 0.2.1](http://polishlinux.org/apps/mesk-audio-player-0-2-1/)

---

