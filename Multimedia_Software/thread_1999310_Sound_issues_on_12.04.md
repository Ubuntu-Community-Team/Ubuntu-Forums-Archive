---
title: "Sound issues on 12.04"
date: 2012-06-07
forum: Multimedia Software
---

### Post by sanaga on 2012-06-07
Fresh install of 12.04. Haven't been able to find a similar problem in my google searches...

Sound is working fine if I open something that uses sound however, if I run World of Warcraft through Wine... I get no sound in game but it works in any other program.

If I run the game before opening another program that uses sound, I get no sound in anything other than the game.

Winecfg's Audio tab is set to use System Default for all options.

Reminds me of how OSS used to work... but I'm fairly sure I'm only using Pulse/Alsa.

Troubleshooting logs here: 
[FONT=monospace]http://www.alsa-project.org/db/?f=8c622aa7e19487e774c99caeaf2ec2bd7944c9a4

I don't know where to go from here or if it's Ubuntu's fault or WINE's fault.

Thanks in advance,
Sanaga
[/FONT]

---

### Post by sanaga on 2012-06-08
Apparently I didn't have the 32 bit alsa drivers installed.

```
sudo apt-get install ia32-libs
```

Sound works perfect everywhere now, but seems to have extended the time it takes for my system to boot up... but meh.

---

### Post by RaphaelBaer on 2012-06-21
Hey, thank you for this hint.

I thought it would take hours to get behind the reason of this problem, but gladly the first thing I found was this thread.

---

