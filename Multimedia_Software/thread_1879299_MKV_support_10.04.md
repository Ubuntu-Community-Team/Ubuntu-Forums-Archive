---
title: "MKV support 10.04"
date: 2011-11-11
forum: Multimedia Software
---

### Post by yusuo85 on 2011-11-11
I have a dual boot system and Im trying to get my mkv files to work flawlessly on Ubuntu 10.04, I've tried using VLC and there jumpy and skip alot, it was the same in Windows, I had to use Media Player Classic in Windows to get MKV's to work properly.

Is there a better media player for Ubuntu that will play my MKV files flawlessly.

I have the latest graphics driver off ati's website, but I'm guessing and this is only a guess, VLC is not streamlined enough to play mkv content on my crappy netbook.

---

### Post by wolfen69 on 2011-11-11
I'm not sure what you mean by not streamlined enough. You mean memory wise? VLC is actually pretty lean compared to others. Since netbooks are notorious for having "less than good" video chipsets in them, there's probably not much you can do about it. 

But you could also go into vlc's preferences and try a different video setting. Btw, what is the resolution of the vids you're trying to play?

---

### Post by yusuo85 on 2011-11-11
yeah my old netbook was poo for hd content but my new one had a hd graphics chip in it so it can handle it, as I said my windows partition can play it flawlessly with media player classic but im trying to find a player that can do it in ubuntu, Ive got mplayer now, trying to find the support for it

When I try and play it I get 

"Fatal Error

Error opening/initializing the selected video_out (-vo) device"

Any ideas

---

### Post by andrew.46 on 2011-11-11
> **yusuo85 said:**
> 

```
Error opening/initializing the selected video_out (-vo) device
```


Could you post the full terminal output? Also perhaps experiment a little with an alternative -vo device....

---

### Post by beew on 2011-11-11
mplayer2. Install with this ppa. 

[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

(Just install the player, dishowserver is only for coreavc and you don't need it)

You can install a gui for it like gnome-mplayer or Umplayer

The latter is available from this ppa
[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

---

