---
title: "No sound w/speakers but sound w/headphone jack, Ubuntu 10.04, Toughbook CF-52"
date: 2011-09-14
forum: Multimedia Software
---

### Post by sgthudsonkj on 2011-09-14
I need some help. I have been chasing my tail for quite a while searching and searching the forums for help in resolving my issues but I haven't been able to nail it down, so I am posting here in hopes someone will know how to help me. (I know it's a lot to ask, lol.) Here the output I get for basics.

sh-4.1$ uname -a
Linux hud-laptop 2.6.38 #1 SMP Thu Mar 17 22:59:29 EDT 2011 x86_64 GNU/Linux
sh-4.1$ aplay -l
aplay: device_list:223: no soundcards found...
sh-4.1$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
sh-4.1$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Analog Devices AD1884

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

I am hoping someone out there has been able to get sound of the speakers, and not just the headphone jack. 
-The Hud
"The Quieter You Become The More You Are Able To Hear."

---

### Post by JD8182 on 2011-09-14
Try System/Preferences/Sound: open the output tab and see if you have two options if so, switch the option, if still no sound that you should make sure all your volumes are turned on and up. Open a terminal and type: ```
 alsamixer 
``` , when this opens, make sure all your volumes there are open then, click F6 while alsamixer is still open change your device to make sure those volumes are turned up as well. Hope this helps.. By the way, is your headphones USB or Standard jack?






> **sgthudsonkj said:**
> I need some help. I have been chasing my tail for quite a while searching and searching the forums for help in resolving my issues but I haven't been able to nail it down, so I am posting here in hopes someone will know how to help me. (I know it's a lot to ask, lol.) Here the output I get for basics.

sh-4.1$ uname -a
Linux hud-laptop 2.6.38 #1 SMP Thu Mar 17 22:59:29 EDT 2011 x86_64 GNU/Linux
sh-4.1$ aplay -l
aplay: device_list:223: no soundcards found...
sh-4.1$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
sh-4.1$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Analog Devices AD1884

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

I am hoping someone out there has been able to get sound of the speakers, and not just the headphone jack. 
-The Hud
"The Quieter You Become The More You Are Able To Hear."

---

### Post by sgthudsonkj on 2011-09-14
I have already done these things to no avail, and attempted them again after your response. I am attempting to use the standard soundboard that came with my laptop. It's a standard headphone jack. Not USB.

---

