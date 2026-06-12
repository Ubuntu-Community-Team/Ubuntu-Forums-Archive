---
title: "Nvidia drivers cause flash player 9 to be slow in full screen"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by ipartola on 2008-03-17
Good time of day.

I am trying to watch youtube (and other) flash videos on Xubuntu 7.10 (I installed both the 386 and the x86_64 versions on this computer). I have an AMD X2 machine with an NVIDIA 8300 GS card. I installed the proprietary drivers and flashplugin-nonfree 9.0.115.

Now, every time I try to play a flash video it works like a charm. However, in full screen the video gets REALLY choppy.

The culprit seems to be the nvidia driver since switching to vesa seems to fix the issue. I've read on this forum that others have experienced these same issues. Does anyone have any solutions to this problem?

Thanks.

P.S.: Additional symptom: I installed VirtualBox and installed WinXP under that. I then tried to play a flash video through that and it works, but it crashes the browser (IE and FF) if I try to go to full screen.

---

### Post by askreet on 2008-03-17
115 is generally slow, I had better success with r48.  See here: [http://ubuntuforums.org/showthread.php?t=501986](http://ubuntuforums.org/showthread.php?t=501986)

---

### Post by Estesark on 2008-03-17
^ My understanding is that full-screen isn't supported in r48. I could be wrong on this though.

I couldn't get full-screen to work with either the r48 or the r115 plug-ins; the only way I could get it to work was to use the proprietary driver, but then the quality was very poor.

Using this exact same hardware set-up, full-screen flash was absolutely fine on openSUSE, but is very choppy on Ubuntu, and I have no idea why.

---

### Post by askreet on 2008-03-17
Hmm, I've never attempted to use any full-screen flash I just know that r115 was slow for all flash apps for me until I rolled back to r48.  Best of luck though D:

---

### Post by groovyMysterioso on 2008-04-01
Not sure if the issue is the same, but when I had a similar problem I turned off hardware acceleration off in the flash player.

---

### Post by ipartola on 2008-04-02
It seems that the issue is here when I am running Xgl. Once I turn it off and use plain old X flash scales just fine. This might be related to the mythtv not working when running Xgl. I believe there is a bug for the mythtv posted on launchpad.

---

