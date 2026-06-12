---
title: "Vgaswitcheroo upon startup"
date: 2012-05-30
forum: Multimedia Software
---

### Post by Aldo93 on 2012-05-30
Basically, all I want to do is run the command 'Echo OFF > /sys/kernel/debug/vgaswitcheroo/switch' upon startup to turn off my discrete GPU so I don't have to type it out manually in the terminal every time I log on, I've tried a few things to no avail so far.

I have tried using sysfsutils, which worked the first time I rebooted but for some reason stopped working thereafter. I have also tried adding the command line to rc.local, which again, worked the first time I rebooted but didn't work thereafter. 

I'm not very experienced with Ubuntu and have ran out of ideas, I'm sure there must be a simple way to do it as it's only a simple command but it seems all the solutions I have found on the internet are very temperamental and don't always work. 

I'm not going to be using the discrete card and want to power it off or disable it to stop my fan being so loud and my system overheating. Any solutions would be great.

Thanks.

---

### Post by Aldo93 on 2012-05-31
Bump

---

### Post by brainwash on 2012-05-31
Delaying the execution of the command might solve your issue. Add this line to /etc/rc.local (before exit 0):
```
(sleep 5 && echo OFF > /sys/kernel/debug/vgaswitcheroo/switch) &
```

---

