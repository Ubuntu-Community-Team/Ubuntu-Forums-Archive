---
title: "Can't install restricted drivers on NVIDIA GeForce GT 550m and Ubuntu 11.4 64bit"
date: 2011-09-18
forum: Multimedia Software
---

### Post by zoquero on 2011-09-18
[COLOR=#000000][FONT=Arial]Hi![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I’ve got a [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**Dell XPS 17 (L702X)**[/FONT][/COLOR][COLOR=#000000][FONT=Arial] shipped with a “[/FONT][/COLOR][COLOR=#000000][FONT=Arial]**NVIDIA GeForce GT 550m**[/FONT][/COLOR][COLOR=#000000][FONT=Arial]”. I installed [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**Ubuntu Desktop 11.4 64 bits**[/FONT][/COLOR][COLOR=#000000][FONT=Arial] with latest updates and can’t install NVIDIA’s restricted drivers following the tip “[/FONT][/COLOR][COLOR=#000000][FONT=Arial]*Additional drivers*[/FONT][/COLOR][COLOR=#000000][FONT=Arial]”. After enabling the restricted drivers and rebooting it doesn’t work, and I fall back to an unaccelerated driver.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]$ uname -mr[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]2.6.38-11-generic x86_64[/FONT][/COLOR][COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ lspci -nn[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]…[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]00:02.0  VGA compatible controller [0300]: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller [8086:0116] (rev 09)[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0dd6] (rev a1)[/FONT][/COLOR][COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]First, following this instructions : [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia_[/FONT][/COLOR]]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")[COLOR=#000000][FONT=Arial]  I verified that I have the packages linux-headers-2.6.38-11 ,  linux-headers-2.6.38-11-generic and linux-image-2.6.38-11-generic , but  couldn’t find any package like linux-restricted-modules-2.6.38-11 on any  repository . Maybe this is a problem for Nvidia drivers.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]repositories in my /etc/apt/sources.list :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]natty main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]natty-updates main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]natty universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]natty-updates universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]natty multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]natty-updates multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]natty-security main restricted[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]natty-security universe[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]natty-security multiverse[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I also tried to install the latest drivers from Nvidia website but I wasn’t luckier.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Can any body help me? Maybe some test to do or some link to more info?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks a lot!

/ Angel
[/FONT][/COLOR]

---

