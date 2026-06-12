---
title: "HDMI audio good in MythTV, bad in XBMC/Boxee"
date: 2010-12-30
forum: Mythbuntu
---

### Post by ceenvee703 on 2010-12-30
So this is not exactly a Mythbuntu question, but since I wasn't finding anything about this particular problem with my Google searches I thought I'd start here.

Thanks to various threads here and elsewhere, I got my Mythbuntu-based FE/BE working with digital audio over HDMI. I'm at work and would have to look at my box to see the exact setup, but I'm pretty sure I have it set up in MythTV as "ALSA:hw1,7". It works great with recordings, but more specifically, with all my MP4 movies under MythVideo, regardless of their soundtrack.

However, if I try to play those same movies under XBMC or Boxee, the majority of them sound tinny and scratchy and highly unpleasant. A small minority sound fine... I haven't yet determined if AC3 or AAC or MP3 is involved in the ones that work vs the ones that don't.

I've tried adding asound.conf and that either doesn't help or breaks all audio, depending on what I put there (I used various options I found out there).

I also have tried ~/.asoundrc settings, and like asound.conf, it either hasn't helped or breaks all audio. I can list those settings in a follow-up message once I get home.

Any ideas? The puzzling thing is that, if MythVideo can do it, I don't see why XBMC and Boxee can't.

Thanks!

---

### Post by ceenvee703 on 2010-12-31
Followup: I have no active /etc/asound.conf right now. The user account that's running mythtv/XBMC/boxee has this as its .asoundrc


```
pcm.dmixer {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "hw:0,7"
rate 48000
channels 2
period_time 0
period_size 1024
buffer_time 0
buffer_size 4096
}
}
pcm.!default {
type plug
slave.pcm "dmixer"
}
```

---

### Post by iitywygms on 2010-12-31
go here and read up.
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
I would try the suggested fixes before doing an upgrade.

---

### Post by ceenvee703 on 2010-12-31
Thanks. I actually used that script to get HDMI audio in the first place. I will check out the card list and see if customizing for my card helps.

---

### Post by iitywygms on 2010-12-31
> **ceenvee703 said:**
> Thanks. I actually used that script to get HDMI audio in the first place. I will check out the card list and see if customizing for my card helps.

Adding my card to the alsa config file is what did it for me.  Like you, I had sound in myth but not anywhere else.  Explicitly adding my card did the trick.

---

