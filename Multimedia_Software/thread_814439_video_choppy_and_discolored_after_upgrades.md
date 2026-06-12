---
title: "video choppy and discolored after upgrades"
date: 2008-05-31
forum: Multimedia Software
---

### Post by holiday on 2008-05-31
After a recent 8.04 upgrade that included a kernel update (not sure if that is the trigger) my mplayer video became choppy. Thinking it might be an mplayer-specific problem I installed gxine. Gxine failed at runtime - a missing library.

So I went back to mplayer and found that the color was a mess. Even totem color was a mess. I start these from the console and there was nothing in the output, nothing in dmesg to indicate a problem. 

So I've removed both mplayer and gxine, re-installed mplayer - and the colour problem *and* the choppy problem both persist. 

I've tried running the media installs from the sticky but it fails on the win32 codecs even though I have enabled the media repositories suggested by the sticky. And even though I've been happily playing videos without a problem on 8.04 for a few weeks. 

I suppose I could just wipe everything and reinstall but given that I've kept up with the updates my guess is I'd be right back here again so...

Where do I go now?

---

### Post by ajgreeny on 2008-05-31
If youhave a nvidia graphics card, try reinstalling the proprietary driver, as the kernel upgrade will mean that you are using the open source driver at the moment.

---

### Post by ksennin on 2008-05-31
Well, I used to be able to play every video format flawlessly in 7.10, but after the upgrade to 8.04, playing a dvd in any player (mplayer, vlc, etc) will give discolored images, with diagonal lines, and a green smudge at the bottom.  I dont know enough to go messing with video settings, so I am kinda bummed about it.

I guess if 7.10 wasnt broken for me, there was no need for a fix...  Oh, well.

---

### Post by Jeanpaul145 on 2008-07-23
I use the Envy driver on Ubuntu 8.04, and I have a GeForce 8600M GT gfx card. I have the discoloring problem as well.

---

