---
title: "Tearing video playback with Compiz"
date: 2009-11-11
forum: Multimedia Software
---

### Post by teonghan on 2009-11-11
Hi all,

With Compiz on, whenever I play video using SMPlayer/MPlayer/VLC, the video won't played smoothly. I already enable VSync on the compiz setting manager and nvidia settings but still did not work. Any idea on this one? I am using nvidia 8600M GS. Did not happen when I was using Jaunty.

---

### Post by lovinglinux on 2009-11-11
[http://ubuntuforums.org/showpost.php?p=7950332&postcount=2](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2)

---

### Post by pkchips on 2009-11-11
Hello,

I have the same problem. How do I activate VSync in Compiz?

Although I haven't tried the fix posted above yet, when I run "glxinfo | grep -i direct" I get the result of yes to Direct Rendering, so I don't think this is my issue...

Are there any other potential fixes?

Thanks,
pkchips

---

### Post by keypox on 2009-11-11
> **pkchips said:**
> Hello,

I have the same problem. How do I activate VSync in Compiz?

Although I haven't tried the fix posted above yet, when I run "glxinfo | grep -i direct" I get the result of yes to Direct Rendering, so I don't think this is my issue...

Are there any other potential fixes?

Thanks,
pkchips

yeah that link got me excited too, but it doesnt fix anything.  That was old bug seems to have been fixed.

I ditched ATI last year because of tearing, now its back.  What a shame.

---

### Post by mc4man on 2009-11-11
While possibly tearing is hardware related i certainly noticed with nvidia that it was more likely in intrepid and jaunty than in hardy.
I've only used hardy and karmic for real and have eliminated it completly by setting vsync in 3 places. ( though I've seen suggested you shouldn't use all 3

This is on 2 desktops with with agp cards (7800 Gs OC) and 1 laptop (8400m

Atm use the chase scene in Quantum of Solace, ch.3, to test, though hasn't appeared elsewhere

In compiz it's in general options -> display settings ( also make sure the unredirect fillscreen windows is unchecked under general tab - prevents flashing in fs with mouse movements

In nvidia x server settings I enable vsync for both  Xvideo and OpenGl 

YMMV

---

### Post by keypox on 2009-11-11
> **mc4man said:**
> While possibly tearing is hardware related i certainly noticed with nvidia that it was more likely in intrepid and jaunty than in hardy.
I've only used hardy and karmic for real and have eliminated it completly by setting vsync in 3 places. ( though I've seen suggested you shouldn't use all 3

This is on 2 desktops with with agp cards (7800 Gs OC) and 1 laptop (8400m

Atm use the chase scene in Quantum of Solace, ch.3, to test, though hasn't appeared elsewhere

In compiz it's in general options -> display settings ( also make sure the unredirect fillscreen windows is unchecked under general tab - prevents flashing in fs with mouse movements

In nvidia x server settings I enable vsync for both  Xvideo and OpenGl 

YMMV

i have all the same except not in OpenGL.  I dont run movies in open GL.  But I did switched the the restricted driver to see if that helped.  It did not.  

bummer

---

### Post by lovinglinux on 2009-11-11
> **keypox said:**
> yeah that link got me excited too, but it doesnt fix anything.  That was old bug seems to have been fixed.

It's funny, because this is not first time I recommend that workaround and it didn't work. Nevertheless, it worked for me on Jaunty and on Karmic. It seems to me that the bug hasn't been fixed.

---

### Post by teonghan on 2009-11-12
> **lovinglinux said:**
> [http://ubuntuforums.org/showpost.php?p=7950332&postcount=2](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2)

Thanks for the link. I will try it as soon as possible. By the way, I found some sort of workaround on this one. The thing is I go to the gconf-editor -> apps -> compiz -> general -> screen0 -> enable unredirect fullscreen windows. After that I test playing my video in SMPlayer/VLC, and I notice I did not have the problem anymore. Well, I did not have time to test for some other video yet but at the video I test before the tweak works without tearing after tweak.

---

### Post by pkchips on 2009-11-12
> **teonghan said:**
> Thanks for the link. I will try it as soon as possible. By the way, I found some sort of workaround on this one. The thing is I go to the gconf-editor -> apps -> compiz -> general -> screen0 -> enable unredirect fullscreen windows. After that I test playing my video in SMPlayer/VLC, and I notice I did not have the problem anymore. Well, I did not have time to test for some other video yet but at the video I test before the tweak works without tearing after tweak.

Hello again,

I tried unredirect fullscreen windows and also enabled compiz VSync, and now things seem to be working a lot better. However, on Jaunty I had absolutely NO tearing on my videos, whilst in Karmic there is still some when the video becomes very graphically active.

If I can't find a way to fix this I may have to return to Win XP after having had a great 2 or 3 months with Jaunty :-(.

---

### Post by teonghan on 2009-11-12
> **pkchips said:**
> Hello again,

I tried unredirect fullscreen windows and also enabled compiz VSync, and now things seem to be working a lot better. However, on Jaunty I had absolutely NO tearing on my videos, whilst in Karmic there is still some when the video becomes very graphically active.

If I can't find a way to fix this I may have to return to Win XP after having had a great 2 or 3 months with Jaunty :-(.

Dear pkchips,

I also did not face this problem when I was using Intrepid or Jaunty though it did happened in Hardy for me.

---

### Post by Minsky on 2009-11-16
Hi, I've also got the same problem, I get a choppy DVD video output with VLC, and I can't use Movie Player with DVDs as it just hangs and I have to force quit. I'm using Karmic with an ATI 4830, Compiz/Emerald installed and Extra Effects enabled. I've tried disabling Compiz in case that was causing the issue but it didn't make a difference. I've also tried the suggestions posted above but with no joy. The problem occurs with DVDs only, downloaded files play fine. Can anyone help?

---

### Post by Minsky on 2009-11-22
Can anyone help me out with this?

---

### Post by onemanclapping on 2009-12-07
I wrote a thread with this same problem some time ago... no solution yet... how can't noone at least find out why this happens?!

---

### Post by sambolinux on 2009-12-09
First what have you installed as far as codecs ?? It sounds as if you haven't installed " libdvdcss2 " but you are using vlc it has its own files. Have you tried mplayer or smplayer with these you do have to have libdvdcss2 installed or they wont work at all with dvds and "movie player" also depends on  it, too. Another question , are you trying to play the dvd from the menu or navigating to vob files ???

---

### Post by Minsky on 2009-12-13
Thanks for the replies and I'm happy to say that I've managed to rectify the problem and that DVD's are playing fine now. I've installed the latest 9.11 ATI drivers and switched the video output to OpenGL, DVD menus work fine as well.

---

