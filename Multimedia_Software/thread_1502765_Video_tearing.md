---
title: "Video tearing"
date: 2010-06-06
forum: Multimedia Software
---

### Post by warlord360 on 2010-06-06
Hi,


I'm using nvidia 275 gtx with the latest offical drivers from nvidia site, I'm using vlc and I have also tried other media players mplayer, and few others. I changed the video out put to video memory, x11, opengl and others and it was still tearing.

I'm using the highest graphics on compiz I also tried to disable it with adding something to end of xorg conf which disabled graphics it still lags.

I tried following this guide: [http://www.omgubuntu.co.uk/2010/01/how-to-stop-video-tearing-vlc-nvidia.html](http://www.omgubuntu.co.uk/2010/01/how-to-stop-video-tearing-vlc-nvidia.html) and still does the same.

I even upgraded the kernal to real time or something and does the same.


I was having this problem before so I said screw it and waited till the ubuntu 10.04 released and seems their not gonna fix the bug. So I want a perm fix.


I won't disable the graphics to watch a movie everytime and I will not disable it perm. And if I can't watch a video I may as well not use it since I will have to boot into windows all the time.



So I really wanna use ubuntu but seems the developers doesn't really care to fix this. So could someone please help me end the freaking tearing? I really wanna use linux as my main os but I can't if it's gonna do this.


EDIT: I have no swap installed but I have 4gb of ram.

---

### Post by warlord360 on 2010-06-06
Anyone? I really wanna get this fixed.

---

### Post by NUboon2Age on 2010-06-07
Here's at least a start:

With some investigation I found that the** [http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/)** is referred [off of the **nVidia support page**]("http://www.nvidia.com/page/support.html") as the Linux/Unix support forums, so I guess that is an officially endorsed site.

I checked my 10.04 Xorg package and it has 7.5 installed, so it looks like this set of instructions may apply:[B][URL="http://www.nvnews.net/vbulletin/showthread.php?t=72490"]
Debian GNU/Linux or (K)Ubuntu with Xorg 7.x[/URL][/B]

Here's are **[detailed instructions for how to post a problem report]("http://www.nvnews.net/vbulletin/showthread.php?t=46678") **on the nVnews.net site in order to get help.

[**nVidia Knowledgebase **]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_alp.php")where you can search if the answer is there and if necessary also post questions
[URL="http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=44"]
**nVidia instructions for bug reporting**[/URL]

---

### Post by farbird on 2010-06-07
disable composite in xorg.conf

---

### Post by warlord360 on 2010-06-07
> **farbird said:**
> disable composite in xorg.conf

Again I did that. And even if it worked I still wouldn't disable it perm since I want the 3d graphics if I'm not allowed to have good video play with crap disabled then I may as well not use it.

---

### Post by NUboon2Age on 2010-06-11
Also found the #nvidia irc channel which provides:
"UNOFFICIAL NVIDIA Linux/FreeBSD/Solaris Graphics Driver Support"

---

### Post by kircher on 2010-06-21
Did you try this? I had similar problems and this fixed mine.

[http://microsoft_rules.ubuntuforums.org/showthread.php?t=1390284](http://microsoft_rules.ubuntuforums.org/showthread.php?t=1390284)

---

