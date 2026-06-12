---
title: "xine can't handle mp3s anymore :("
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by pompos on 2007-12-09
Hey...
Amarok stopped playing mp3s yesterday :(
It prompts a little dialog box saying that Amarok currently cannot play MP3 files. It asks me if I want to install the MP3 support. If I hit yes nothing happens.
 
I tried another xine Player (Kaffeine) but I does not work, either. I also tried to reinstall xine but still nothing changed ;(
 
OGG-Files work like they are supposed to.

P.S. I already posted my problem in the Multimedia Production Forum but Stochastic suggested my to post it here too.

---

### Post by bobpaul on 2007-12-09
> **pompos said:**
> Hey...
Amarok stopped playing mp3s yesterday :(


Same problem. Fresh install but old home folder. Amarok complains it can't play mp3s, but both GXine, Totem, and Rhythmbox play them fine..

---

### Post by bobpaul on 2007-12-09
Wait, I think the following might have fixed it:
```
sudo aptitude install ubuntu-restricted-extras
``` If not, the packages  libxine1-gnome and libxine1-plugins must have. I just realized when I thought I was restarting amarok, it was actually running in the tray the whole time.

If you're on kubuntu, use kubuntu-restricted-extras instead...

---

### Post by Whiffle on 2007-12-09
Hmph.  mp3 support disappeared for me in an update a few days ago, I just updated again, and now xine doesn't work at all.  This is what I get when I try to update

```
The following packages have been kept back:
  libxine1-plugins mencoder mplayer

```

mplayer plays mp3's just fine though....

Those look important, but it won't upgrade them.    I have all of the restricted extras installed.  I think I should just not upgrade things, they seem to break all too often...

---

### Post by igb on 2007-12-10
Same thing happened to me. Amarok tells me that it can't play mp3,even though I have all the required extras installed and it has all worked fine before. Xine won't play mp3 either. No amount of uninstalling and reinstalling Amarok and all the required bits of xine have worked.

I suspect that a recnt update has broken something.

Ian.

---

### Post by pompos on 2007-12-10
I have got it working again... unfortunately I don't know what was the exact reason.

The magic seemed to happened between endless reinstalls of all the xine packages, deleting ~/.xine, deleting ~/.kde/share/apps/amarok and ~/.kde/share/config/amarokrc (I guess the last two deletes were not needed) and one reboot.
The result of all that is amarok is working again but Kaffeine is crushing even worse and sooner :( Since I don't need it I don't care.

---

### Post by igb on 2007-12-11
Thanks, deleting .xine then forcing a re-install of libxine1-ffmpeg seems to have fixed it for me.

Ian.

---

### Post by DSK on 2007-12-11
> **bobpaul said:**
> Wait, I think the following might have fixed it:
, it was actually running in the tray the whole time.

If you're on kubuntu, use kubuntu-restricted-extras instead...

Dang I did the same thing...pulling my hair out but I never actually restarted it cause it was in the tray!!!

---

