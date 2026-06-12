---
title: "DVD play erratic"
date: 2008-11-09
forum: Multimedia Software
---

### Post by nss0000 on 2008-11-09
Gents:

I'm running a fully patched HH_8.04.1 system: AMD5400/NV7600 w/o the proprietary NV drivers.

Approx 1/2 of all DVDs I grab from the library fail to play properly. Failure modes vary: sometimes the language is not English w/o subtitles, sometimes there's no sound and sometimes the movie will play (less than) a minute and then stop dead. Something does always happen ....

Sometimes an error message appears ( 'can't find source') and sometimes not. 

When the DVD does play properly ( ~50% ) it plays without issue. Am I looking at a hardware fault ??

---

### Post by mc4man on 2008-11-09
> Approx 1/2 of all DVDs I grab from the library fail to play properly
What is the condition of these disks, my experience is people tend to treat disks from the library like they're frisbees.

---

### Post by nss0000 on 2008-11-09
mc4:

The library DVDs are no prize. Rough handling is obvious. But the behavior under DD_6.06 was very consistent and successful, while with my newly installed HH any-DVD can sink-or-swim. 

It still "smells" like a hardware weakness to me, but mebby a bug was introduced in DVD_playback_software for the new OS.

---

### Post by psyke83 on 2008-11-09
> **nss0000 said:**
> mc4:

The library DVDs are no prize. Rough handling is obvious. But the behavior under DD_6.06 was very consistent and successful, while with my newly installed HH any-DVD can sink-or-swim. 

It still "smells" like a hardware weakness to me, but mebby a bug was introduced in DVD_playback_software for the new OS.

Are you using Totem? It's DVD playback support is notoriously bad. I suggest you install VLC and give it a shot.

Also, you may be lacking the libraries to decode CSS-protected disks. Add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository to your system and install the "libdvdcss2" package.

---

