---
title: "vlc cannot open files with long file names"
date: 2014-03-10
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2014-03-10
Hi,

I have experienced a strange problem. VlC is having problems opening some media files with long file names. When I click several times nothing happens but the top command shows that there are several instances of vlc struggling in the background. Playing in command line works, as does opening vlc, go to play and choose file. Just clicking doesn't work.

 After renaming the files to something shorter then it opens on click with no problem.

It is vlc 2.1.4 on Ubuntu 13.10. It is self compiled (against ffmpeg 2.1.4) 


Edited: hmm.. seems to be format related as it can open .mkv and .mp4 with even longer names. The ones that it fails are .wav (audio) and .flv, used to be able to open them in their long names with vlc 2.1.3 and before.

---

### Post by andrew.46 on 2014-03-10
Are there any hints if you run from the commandline with:

```

cvlc -vvv "long filename.wav"

```

With any luck the terminal output may contain a clue, although I see that it is really only 2ble clicking that causes the problem...

---

### Post by monkeybrain20122 on 2014-03-10
> **andrew.46 said:**
> Are there any hints if you run from the commandline with:

```

cvlc -vvv "long filename.wav"

```

With any luck the terminal output may contain a clue, although I see that it is really only 2ble clicking that causes the problem...

There is no error, only clicking doesn't work. Command works fine.

---

