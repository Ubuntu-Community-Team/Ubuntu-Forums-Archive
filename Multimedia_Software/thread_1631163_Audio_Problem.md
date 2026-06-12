---
title: "Audio Problem"
date: 2010-11-26
forum: Multimedia Software
---

### Post by Kevin147 on 2010-11-26
Hey,

I am having trouble with Kubuntu. I just switched over from  Ubuntu, and when I logon, I hear bits of sound. Then when I try to play a  youtube video, it goes like its in fast forward mode. I'm not very good  with Kubuntu, so I would like some help on how to fix this. Thanks!

---

### Post by lykeion on 2010-11-26
You can check these pages:
[LIST]
[*]Ubuntu Documentation: [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")
[*]Ubuntu Forums: [Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449")
[/LIST]
(last link might not be updated to Lucid/Merkaat, but still contains good troubleshooting info)

---

### Post by Kevin147 on 2010-11-26
To the first link: I can hear it, its just in bits...like example, if it says: RIGHT, I hear RI*Then nothing*then like a little static noise. Thats the problem I'm having.

---

### Post by lykeion on 2010-11-26
Does all sounds get clipped with static noise?

Have you checked cables and connections?

Start a terminal (Applications > Accessories > Terminal)
1. Paste the output of this command:```
aplay -l
```
2. Paste the output of this command: ```
lspci -v | grep -A 7 Audio
```

---

