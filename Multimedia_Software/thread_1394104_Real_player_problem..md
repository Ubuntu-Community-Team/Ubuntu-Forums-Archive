---
title: "Real player problem."
date: 2010-01-30
forum: Multimedia Software
---

### Post by Saint_88 on 2010-01-30
Hi 
 
I have a problem with real prayer, though it works fine, sometimes it stops. I cannot run the program without restarting my computer. I tried to re-download but its just the same. I dont know what the problem is... 
 
thank you

---

### Post by lykeion on 2010-01-30
First some troubleshooting tips to find out what the problem could be:

[LIST]
[*]Start realplayer from a commandline to get the error output
[*]Check the system logs
[/LIST]
Next I'd like to ask why you need to have realplayer at all? Is it some special content you can't play with other media players?

It's never optimal to run proprietary software like realplayer in linux, therefore I'd suggest you to install helix-player instead (it supports ram and rtsp). 

```
sudo aptitude install helix-player
```

Read more here: [HelixPlayer]("https://help.ubuntu.com/community/HelixPlayer")

---

### Post by Saint_88 on 2010-01-30
Nice! thanks for the tip and the advise I'll check out the helix!!!

---

