---
title: "DVDs not playing because it doesn't recognize the audio"
date: 2009-08-24
forum: Multimedia Software
---

### Post by gobberpooper on 2009-08-24
I have some South Park DVDs that I want to watch but I don't want to watch it on the TV while my sister is around. So I popped it into the computer and when opening it up with VLC, nothing happens. With Movie Player, it just closes automatically.
I opened the DVD in a folder and I saw that there was a Video_TS but no Audio_TS. The same problem happened with ever single South Park DVD, and even other DVDs like Million Dollar Baby and Lord of the Rings. Please help!:(

---

### Post by starcraft.man on 2009-08-24
> **gobberpooper said:**
> I have some South Park DVDs that I want to watch but I don't want to watch it on the TV while my sister is around. So I popped it into the computer and when opening it up with VLC, nothing happens. With Movie Player, it just closes automatically.
I opened the DVD in a folder and I saw that there was a Video_TS but no Audio_TS. The same problem happened with ever single South Park DVD, and even other DVDs like Million Dollar Baby and Lord of the Rings. Please help!:(

The short answer is, there aren't supposed to be any files in the audio_ts folder. It's a legacy thing I suppose, I have plenty of DVDs I own and they also have the empty audio folder. The audio tracks for video are blended in with the video tracks during encoding of the DVD. It will play fine long as ya have dvdcss and point VLC to the video directory (use open directory on video folder instead of open DVD sometimes). If you don't have dvdcss installed, see medibuntu repo.

---

### Post by gobberpooper on 2009-08-26
I did that and it didn't work at first. I restarted the computer and still it didn't work. The next day it still didn't work. Now all of a sudden it's working today and I'm watching it. Thank you very much! :)

---

