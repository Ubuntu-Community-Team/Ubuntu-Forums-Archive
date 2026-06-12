---
title: "Realtek ALC1200 Not detected in intrepid"
date: 2008-11-20
forum: Multimedia Software
---

### Post by phyrelin on 2008-11-20
Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)

Any hints where to start in getting this sound to work?

Thanks Alot

---

### Post by markbuntu on 2008-11-20
If you have an ALC 1200 sound chip (ASUS P5QL-EM mobo) add the following line to the end of the /etc/modprobe.d/alsa-base file:

```

options snd-hda-intel probe_mask=1

```

This should work for you in Intrepid. It works with alsa 1.0.17 and 1.0.18 but not earlier versions.

---

### Post by ggv6 on 2008-12-27
Hi

I had the same problem and added this line on the alsa -base file but it only worked the first time. After reboot had the same problem. It seems to detect it 2-3 times out of about 50 reboots.
I run lspci and the system always detects the card.

Any more ideas on how to fix this

Thanks

---

### Post by nathandrewsire on 2009-02-17
I used the fix:

options snd-hda-intel probe_mask=1

added to /etc/modprobe.d

It fixed the sound and it worked a few times. Then it quit. I am looking through

/var/log/messages

and I see pulse audio problems. I read that pulse audio enables you to play sound through flash players.

---

