---
title: "help simple question sound"
date: 2009-01-04
forum: Multimedia Software
---

### Post by hoboboot on 2009-01-04
hi i just installed 8.04 last week, i've got my display, and wireless working now... fixed the bios clock from changing to UTC time on shutdown(so dual boot to xp doesnt come up with the wrong time) and im really getting along pretty ok so far...my memory card reader works, it is listed in lspci... my question is, if my sound card shows up in lspci, that dosent mean it works right? just says it knows what kind it is? cause the thing is, that it seems like it is installed but, i cant seem to get any audio to actually play out the speakers or out of the headphone/speaker jack either.. not a sound, playing mp3's and videos yields no sound... 

please help me understand why im not hearing anything. i figured its something stupid like, i've detected my sound card chip, but it dosnt work without some initial set-up? 

please help.


//////////////////////SOLVED:
i did this:
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

and it worked. markbuntu is god. h00ray

---

### Post by nadiutta on 2009-01-04
maybe I can attach myself to this thread cause I almost have the same problem. I just download  the same Ubuntu 8.04 and after the second installation now I can hear sound from files I have in my pc, but still I can't hear anything from files playing online. I can see a player (for example playlist.com ) but I don't hear a thing. Same for the videos: I can see them, but without audio.

---

### Post by nadiutta on 2009-01-05
nobody? please?
my husband can't watch his news and he already told me to put back Window :(

---

### Post by markbuntu on 2009-01-05
Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not fix your problems go here for more comprehensive help

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by IQRules on 2009-01-05
It will be easier, post your machine type, such as IBM laptop or model number.

Open a Terminal first, Click Up Left-hand Corner Applications tab, Accessories, Terminal (Like windows cmd)

And post '$ lspci -v', just grab multimedia section, and '$ aplay -l' and 'aplay -L'.

---

### Post by nadiutta on 2009-01-06
I have a Pentium 4...Dell dimension 4550
I dont' understand the rest you ask me to do....

@markbuntu ok thanks, I'll try to search there now

---

### Post by IQRules on 2009-01-06
Found this, Your card is Intel ICH4.

Richard Huelbig
2005-01-22, 02:37 PM CST
All,

When I went over to Bugzilla I did a search on some sound card problems and upgrading kernels. In Bugzilla I found a workaround for my FC3 machine. I opened the volume control and set the Headphone Jack Sense and Line Jack Sense settings to Mute (I checked the Mute check boxes). When I did that I started to get sound.

However, on my FC2 PC, when I open the volume control I do not have Line Jack Sense and Headphone Jack Sense selections. So, my problem remains with the latest kernel and FC2. I will post these findings on Bugzilla. If anyone has any additional information, please share it.

Thanks...

---

