---
title: "No sound fix in 8.04.1 (?)"
date: 2008-07-04
forum: Multimedia Software
---

### Post by romansky on 2008-07-04
OK, I run 7.10 on my computer, but I've been dying to upgrade. I tried installing 8.04 right after the initial release, but due to a persistent sound problem, I eventually reverted to 7.10. I thought this problem was due to a bug, and that it would soon be patched. Thus, I was fairly certain I'd have no problems when I installed 8.04.1 today. No such luck, though! The problem is still there. I guess this means it won't be fixed at all (?) Oh no! Am I stuck with Gutsy forever? I mean, it's real nice and all, but it would be nice to try something new every once in a while.

The problem is detailed in this post:

[http://ubuntuforums.org/showthread.php?t=766340](http://ubuntuforums.org/showthread.php?t=766340)

But to sum it up, I'm unable to adjust the volume. It's either 100% or 0%, and it's impossible to make the volume button stay anywhere between. I can adjust the volume within each application, bur not the main volume, so that's cumbersome. From what I could gather from my last posting, it seems to be a alsa-related problem, but I never managed to find a completely satisfactory solution. Does anyone know if this is a bug that's being worked on, or if this problem is here to stay for good?

Thanks ahead.

---

### Post by romansky on 2008-07-05
I think it has to do with alsa and my sondcard, as alsa don't show up under 'preferences' in the sound menu. This is the lspci-info about my audio device:

*Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)*

Any thoughts or known solutions?

---

### Post by romansky on 2008-07-06
Only a OSS-mixer is available. alsa-utils are installed, but when I write 'alsamixer' in the terminal, I get the following error:
[I]
alsamixer: function snd_mixer_load failed: No such file or directory[/I]

I've tried re-installing all alsa-related packages, but to no avail. Any comments or tips would be welcome :-)

---

