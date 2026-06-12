---
title: "High tones suffering from noise/crackling."
date: 2009-02-25
forum: Multimedia Software
---

### Post by Lupusceleri on 2009-02-25
Hello,

As of late my PC has issues with its sound card drivers on Kubuntu. Whenever a high tone comes up, you can hear some crackling (you know, a bit like when you blow air into a microphone). As you can probably imagine, that's pretty annoying.

So I went and experimented some to see if I could narrow the issue down. The issue pops up with any sound playing program I use - mplayer, amarok-kde4, old amarok 1.4 with xine engine, dragonplayer, vlc. At first I'd tried reinstalling the sounddrivers and soundplayers as described in the guide stickied in this forum ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)), but that didn't solve anything.

Then tried if it mattered where the source came from, so I plugged my MP3 player into the aux and zero problems there. So it had to be the computer. Next, I tried some different operating systems. First Windows Vista with Winamp, flawless high tones. Then I grabbed my Kubuntu LiveCD (the very same I installed from), downloaded some mp3 codecs, and again - flawless high tones.

So, whatever the exact problem is - it is software-dependant. Reinstalling sounddrivers (including --purge) didn't solve the problem.

I'm using the onboard sound of my motherboard - an Asus A8N-SLI, and I think it's AC97 sound (I had to download Realtek drivers for them to get it to work with Windows). So that is pretty standard. OS I'm having issues with is the AMD64 version of Kubuntu 8.10, with KDE4.2.

Anyway, I'm now officially at a loss of what the problem could be and I don't know any solutions short of a reinstall, which I of course would like to avoid.

Thank you very much in advance,

Martijn Schmidt.

---

### Post by Lupusceleri on 2009-02-25
Up.. any ideas how I can solve this short of reinstalling Kubuntu? :)

---

### Post by Lupusceleri on 2009-03-27
Necro time for reference.

Today's xine update (repository) fixed this. So if you have the same issue... purge xine and every other xine-named-thingie, and install it again. :)

---

