---
title: "xterm sound"
date: 2010-11-15
forum: Multimedia Software
---

### Post by spider_ktx on 2010-11-15
Hello,
I have one problem, i am using an computer on which i run Ubuntu 9.04 karmic, this computer runs just an animation in flash, i am using xterm session and for full screen i use a script that starts the x-window-manager and this flash movie. The problem is that every time i reboot the machine the sound is on mute, i even put in the startup script commands for unmute ( with amixer), but when flash is playng sound the speaker is muted ( i open alsamixer is ssh connection on other pc) when i was using gnome session there was no problem like this.
I appreciate any help.
Thanks in advance,
Adrian

---

### Post by spider_ktx on 2010-11-16
Anyone might know how to solve my problem?

---

### Post by honeybear on 2010-11-27
> **spider_ktx said:**
> Hello,
I have one problem, i am using an computer on which i run Ubuntu 9.04 karmic, this computer runs just an animation in flash, i am using xterm session and for full screen i use a script that starts the x-window-manager and this flash movie. The problem is that every time i reboot the machine the sound is on mute, i even put in the startup script commands for unmute ( with amixer), but when flash is playng sound the speaker is muted ( i open alsamixer is ssh connection on other pc) when i was using gnome session there was no problem like this.
I appreciate any help.
Thanks in advance,
Adrian

normally the sound is memorized and remains at boot, reboot, and halt
surely

maybe a program chagne it or gnome, who knows.
check what does your WM

however you can use aumix to unmute at boot, using a boot script for that, surely

---

### Post by spider_ktx on 2010-11-28
thanks for answer but gnome-session does not start, xterm-session i use. I used script for unmute and even set it to play sound at startup, the main problem is that the flash animation was using sound and when it used it it was mute again, i added the user to pulse audio ( the user of flash) and still same problem... 
Regards, Adrian

---

