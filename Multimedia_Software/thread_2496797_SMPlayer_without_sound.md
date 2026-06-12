---
title: "SMPlayer without sound"
date: 2024-04-13
forum: Multimedia Software
---

### Post by satimis on 2024-04-13
SMPlayer
Version: 21.10.0 (revision 10000)
OS - Ubuntu 22.04

There is no sound.  Pls advise how to fix the problem?

Thanks

Regards

---

### Post by ajgreeny on 2024-04-13
Do any other music players give you sound and work properly?
What hardware have you got?  Please show us the output of command ```
inxi -Fzx
``` 
Please use code tags for years output.

---

### Post by 14nd on 2024-04-13
```
sudo apt update
```
[FONT=var(--font-mono)]```
sudo apt install ubuntu-restricted-extras
```

[/FONT]

---

### Post by satimis on 2024-04-13
> **ajgreeny said:**
> Do any other music players give you sound and work properly?
What hardware have you got?  Please show us the output of command ```
inxi -Fzx
``` 
Please use code tags for years output.
Hi@ajgreeny,

Other media players, VLC and Videos, works without sound problem.

$ inxi -Fzx > output.txt

output.txt is attached here

Hardware - component ?

AMD Ryzen 5 8-core cpu
RAM 32G DDR3
OS harddrive - SATA3 2TB SSD
DVD-Writer
Display - Dell 32" 4K display

Thanks

**[COLOR="#FF0000"]For your information.[/COLOR]**

VLC Media player can convert video CD to .wav

and then I run following command to convert it to.mp4

```

$ ffmpeg -i 'Track 10.wav' -s 1980x1080 -c:a aac -b:a 128k track-10.mp4

```

but the file size increases dramatically, 3~4 times.  Up-to-now I couldn't make "HandBrake" to work?

Regards

---

### Post by satimis on 2024-04-13
> **14nd said:**
> ```
sudo apt update
```
[FONT=var(--font-mono)]```
sudo apt install ubuntu-restricted-extras
```

[/FONT]
Thanks for your advice.

ubuntu-restricted-extras already installed

$ apt policy ubuntu-restricted-extras```

ubuntu-restricted-extras:
  Installed: 67
  Candidate: 67
  Version table:
 *** 67 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages
        100 /var/lib/dpkg/status

```

Regards

---

### Post by 14nd on 2024-04-13
the newest version is 23.12 , maybe an update will fix?
i'm still on 19.10 and mine works perfect
btw this is what my audio preferences look like

---

### Post by satimis on 2024-04-13
> **14nd said:**
> the newest version is 23.12 , maybe an update will fix?
i'm still on 19.10 and mine works perfect
btw this is what my audio preferences look like
I just installed this software a few days before.

Screenshot of Preferences is attached here.

Thanks

---

### Post by satimis on 2024-04-13
Hi all,

Just test on Video DVD

All tracks .VOB are displayed on "Files".  Please refers to screenshot.

The tracks can be played on VLC media player without problem and with sound.   The tracks can ALSO be played on SMPlayer but without sound.

I think there may be a miss-match between SMSPlayer and Ubutun 22.04

Regards

---

### Post by satimis on 2024-04-13
Hi all,

The Video DVD can be converted directly on VLC to mp4 format.

It took;
**[COLOR="#FF0000"]3hr : 46min : 38sec[/COLOR]**
to finish the conversion.

Next round to convert another DVD video to .MP4

I'll run ffmpeg commands on Terminal;

1)```

$ ffmpeg -i VTS_01_1.vob VTS_01_1.mp4|ffmpeg -i VTS_01_2.vob VTS_01_2.mp4|ffmpeg -i VTS_01_3.vob VTS_01_3.mp4" etc.

```
Check the .vob file having video content inside first.

2)```

$ ffmpeg -i "concat:VTS_01_1.mp4|VTS_01_2.mp4|VTS_01_3.mp4|etc." -c copy VTS_01.mp4

```

The time of conversion would be much faster.  It won't need >3 hrs to finish

---

### Post by amiarg on 2024-04-19
Smplayer is just a frontend, for either mp eller mpv, which one it is using? The info is in prefrenbes. If you try and play your video directly with mplayer  or mpv and you hear sound then it is something in sound settings in smplayer that is the problem, otherwise you should look at solving the problem with mplayer or mpv.

---

