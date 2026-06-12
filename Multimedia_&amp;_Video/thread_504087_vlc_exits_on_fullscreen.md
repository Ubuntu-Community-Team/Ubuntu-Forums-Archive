---
title: "vlc exits on fullscreen?"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by Hybrid86 on 2007-07-18
When I try to set vlc to fullscreen (or even resize it past a certain size), vlc just exits.
I am running ubuntu 7.04

---

### Post by overdrank on 2007-07-19
> **Hybrid86 said:**
> When I try to set vlc to fullscreen (or even resize it past a certain size), vlc just exits.
I am running ubuntu 7.04

Hi I read some of your previous post and it seems that you may have some video issue. Have you been able to resolve them.?

---

### Post by Hybrid86 on 2007-07-20
Unfotunatly no. I've yet to get help on [either post]("http://ubuntuforums.org/showthread.php?t=504067") :(

---

### Post by benx009 on 2007-07-20
I had this problem w/ vlc too (and gxine and kaffine now that i think back on it), especially when playing DVDs. why don't u just use mplayer instead? it's the only thing that plays my DVDs for me on linux.

---

### Post by Hybrid86 on 2007-07-20
> **benx009 said:**
> I had this problem w/ vlc too (and gxine and kaffine now that i think back on it), especially when playing DVDs. why don't u just use mplayer instead? it's the only thing that plays my DVDs for me on linux.
I shouldn't have to; I love VLC. I switched to ubuntu because it "just works", yet I have had more glitches and problems with it than I've EVER had with windows and mac combined. :(

---

### Post by overdrank on 2007-07-21
> **Hybrid86 said:**
> I shouldn't have to; I love VLC. I switched to ubuntu because it "just works", yet I have had more glitches and problems with it than I've EVER had with windows and mac combined. :(

HI if you search for that video card in the forums I have seen that envy has worked for some. I believe the cammand some use was 
```
envy -t
``` Hope this helps and maybe the search will help also good luck! :)

---

### Post by Hybrid86 on 2007-07-21
> **overdrank said:**
> HI if you search for that video card in the forums I have seen that envy has worked for some. I believe the cammand some use was 
```
envy -t
``` Hope this helps and maybe the search will help also good luck! :)

Got this:
```
bash: envy: command not found
```

---

### Post by dabl on 2007-07-21
Assuming you have an Nvidia graphics card, download Envy from here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want the file named "envy_0.9.6-0ubuntu2_all.deb" which is about half way down the page.

Install this file on your system, then Envy will appear in your System menu. Run it, and install the latest Nvidia driver.  Once you have a good driver, you will be able to get the most out of your graphics chip, and maybe even run vlc full screen.

:)

---

### Post by Hybrid86 on 2007-07-22
Installed and updated. still having the same problems (though now system tools has a "nvidia settings" option). Maybe ram really is the problem? How much ram does a screensaver normally take up?

---

### Post by overdrank on 2007-07-22
> **Hybrid86 said:**
> Installed and updated. still having the same problems (though now system tools has a "nvidia settings" option). Maybe ram really is the problem? How much ram does a screensaver normally take up?

Hi I have had the best results running beryl and screen savers is 512mb or better. You can monitor you system with system monitor and it will tell you what resources are lacking. Just start it up under system, administration, system monitor and then wait and when your screen saver opens up then you can stop it an see the effects it has on your system. Can you give some specs on your system and maybe we can help you?

---

### Post by Hybrid86 on 2007-07-23
I have a Dell laptop inspiron 8600 with a GeForce FX Go5200 graphics card, 512mb or ram, and a pentium M processor. When I had xp, everything ran fine graphics wise.

I just checked the system moniter, and both vlc and the screensavers used suprisingly little ram...

---

