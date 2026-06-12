---
title: "This is getting ridiculous"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by l337a on 2007-08-28
I tried envy. I tried an install of my ATI Radeon 9200 PRO drivers. 

Figures. Not supported. So I did a manual install. Everything installed fine, right down to the xorg config.

Then came time to reboot.... I did.

(EE) No devices found

No screens found

and it kicks me to the failsafe mode. I see they indeed installed the driver, and changed it to fglrx. A while ago i tried to manually install everything from the .run file. Then i came across the error that my X version was to new. Go figure.

Could my X version be the reason as to why the fglrx driver isn't working for me? Is there ANYONE that could possibly help with this? I've googled to no extend, and even tore out a few hundred hair folocles in the process. Should I try and downgrade to a lower version of ubuntu? Like v6.06?

I just want 3D acceleration. Thats all. I'm not asking for Bushes IQ to increase, thats impossible. But this, my friends is possible. Anything is possible with linux, I have faith. But I'm too inexperienced to do this on my own. So any help would be amazing.

---

### Post by WinterWeaver on 2007-08-28
hmm... unfortunately I cant help you, but if no one is able to help you in this thread, and you run out of options, you could always try trade in your ATI for a NVIDIA??

EDIT: I know I know... it's not really a solution to the problem, but it was the only one I could, sincerely, think off, cause I see sooo many complaints with ATI

---

### Post by mysticmatrix on 2007-08-28
> **l337a said:**
> I tried envy. I tried an install of my ATI Radeon 9200 PRO drivers. 

Figures. Not supported. So I did a manual install. Everything installed fine, right down to the xorg config.

Then came time to reboot.... I did.

(EE) No devices found

No screens found

and it kicks me to the failsafe mode. I see they indeed installed the driver, and changed it to fglrx. A while ago i tried to manually install everything from the .run file. Then i came across the error that my X version was to new. Go figure.

Could my X version be the reason as to why the fglrx driver isn't working for me? Is there ANYONE that could possibly help with this? I've googled to no extend, and even tore out a few hundred hair folocles in the process. Should I try and downgrade to a lower version of ubuntu? Like v6.06?

I just want 3D acceleration. Thats all. I'm not asking for Bushes IQ to increase, thats impossible. But this, my friends is possible. Anything is possible with linux, I have faith. But I'm too inexperienced to do this on my own. So any help would be amazing.

Well first off all, ATI drivers are not supported for 9200 series. Second is that I have the same card, and the open source RAdeon drivers work fine for me. I was able to play WoW, CS:CZ and Max Payne and also was able to use all Bling Bling Beryl and Compiz without touching xorg.conf once. I also got some performance boost by use of this.[http://ubuntuforums.org/showthread.php?t=520364](http://ubuntuforums.org/showthread.php?t=520364)

Now I don't have faintest idea about about IQ of Bush, but its impossible to increase IQ of ATI !!!!

---

### Post by WinterWeaver on 2007-08-28
> **mysticmatrix said:**
> Now I don't have faintest idea about about IQ of Bush, but its impossible to increase IQ of ATI!!!!

:lolflag:

EDIT: lol ... permission to add that in my sig??

---

### Post by l337a on 2007-08-28
> **mysticmatrix said:**
> Well first off all, ATI drivers are not supported for 9200 series. Second is that I have the same card, and the open source RAdeon drivers work fine for me. I was able to play WoW, CS:CZ and Max Payne and also was able to use all Bling Bling Beryl and Compiz without touching xorg.conf once. I also got some performance boost by use of this.[http://ubuntuforums.org/showthread.php?t=520364](http://ubuntuforums.org/showthread.php?t=520364)

Now I don't have faintest idea about about IQ of Bush, but its impossible to increase IQ of ATI !!!!


See, now that's interesting. On a freshly installed ubuntu 7.04 system I only get maybe 400fps on glxgears. I get crap fps on that Endgame Screensaver, like 5fps at the max.

Are you sure its the same card? PCI ATI Radeon 9200 PRO [Rv280]

---

### Post by mysticmatrix on 2007-08-28
> **WinterWeaver said:**
> :lolflag:

EDIT: lol ... permission to add that in my sig??

Sure permission granted. After all, it is such a well known fact that no one would even bother.

l337a, yes I have the exactly same card, excpet that its a AGP card.( Yours is PCI ). Now it might be that your vendor might have made some other specific tweaks. or may be my vendor had made them. I would suggest you to reinstall your system and check. Also, try performing the tweaks of xorg.conf that helped me.

Also 9200 is a OLD CARD, please don't expect so much out of it. Even my integrated Intel X3000 is giving 1200 FPS in glxgears. Its another topic that I can't play Wine games  on it.

---

### Post by l337a on 2007-08-28
> **mysticmatrix said:**
> Sure permission granted. After all, it is such a well known fact that no one would even bother.

l337a, yes I have the exactly same card, excpet that its a AGP card.( Yours is PCI ). Now it might be that your vendor might have made some other specific tweaks. or may be my vendor had made them. I would suggest you to reinstall your system and check. Also, try performing the tweaks of xorg.conf that helped me.

Also 9200 is a OLD CARD, please don't expect so much out of it. Even my integrated Intel X3000 is giving 1200 FPS in glxgears. Its another topic that I can't play Wine games  on it.


I used to get about 45FPS solid on half-life 2 with this card. I did modify xorg.config like the solved post told me, and it did improve somewhat. But no where near what I would get under windows. And this is a Fresh install.

l337a@l337a-desktop:~$ glxgears
3101 frames in 5.0 seconds = 620.120 FPS
3581 frames in 5.0 seconds = 716.118 FPS
2049 frames in 5.0 seconds = 408.956 FPS
1943 frames in 5.0 seconds = 388.553 FPS
3955 frames in 5.0 seconds = 790.817 FPS
3949 frames in 5.0 seconds = 789.724 FPS
3945 frames in 5.0 seconds = 788.895 FPS
3953 frames in 5.0 seconds = 790.443 FPS
3968 frames in 5.0 seconds = 793.438 FPS
3909 frames in 5.0 seconds = 781.728 FPS
3944 frames in 5.0 seconds = 788.748 FPS
3930 frames in 5.0 seconds = 785.957 FPS
3922 frames in 5.0 seconds = 784.361 FPS
3909 frames in 5.0 seconds = 781.633 FPS

---

### Post by mysticmatrix on 2007-08-29
> **l337a said:**
> I used to get about 45FPS solid on half-life 2 with this card. I did modify xorg.config like the solved post told me, and it did improve somewhat. But no where near what I would get under windows. And this is a Fresh install.

l337a@l337a-desktop:~$ glxgears
3101 frames in 5.0 seconds = 620.120 FPS
3581 frames in 5.0 seconds = 716.118 FPS
2049 frames in 5.0 seconds = 408.956 FPS
1943 frames in 5.0 seconds = 388.553 FPS
3955 frames in 5.0 seconds = 790.817 FPS
3949 frames in 5.0 seconds = 789.724 FPS
3945 frames in 5.0 seconds = 788.895 FPS
3953 frames in 5.0 seconds = 790.443 FPS
3968 frames in 5.0 seconds = 793.438 FPS
3909 frames in 5.0 seconds = 781.728 FPS
3944 frames in 5.0 seconds = 788.748 FPS
3930 frames in 5.0 seconds = 785.957 FPS
3922 frames in 5.0 seconds = 784.361 FPS
3909 frames in 5.0 seconds = 781.633 FPS

Well you are almost getting what I got, near 800 FPS. Also, you will be running Half-Life 2 under Wine/Cedega. Remember they are in one form or other, compatibility layers to run Windows Games on Linux. So you will usually, not always, get a little performance hit.

If you are running HL2 under Wine, you can learn various tricks related to squeezing maximum out of Wine on a thread by cogadh. [http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

Also check Wine's AppDB at appdb.winehq.org. 

If you are stuck with Cedega, hit there heads. You ought to get support for what you paid.(Like you would have for Windows :) )

If you really want to compare performance, run native games like Doom 3, Quake, Tremulous, and other good one.

---

