---
title: "xvid audio out of sync"
date: 2008-09-22
forum: Mythbuntu
---

### Post by lime4x4 on 2008-09-22
When playing an xvid video on my ubuntu desktop it plays fine. When i transfer it over to my mythubuntu box the audio is out of sync. I hear people talking then i c there lips moving. Any ideas?

---

### Post by Lester_Burnham on 2008-09-23
I think it's a problem with mplayer. Try playing it on the same PC with VLC or Xine and it will be OK.

I'm not sure where the problem lies with mplayer or pulse audio!

---

### Post by boralyl on 2008-09-23
I have the same issue, switching the default mythvideo player to vlc fixes it.  And as said above xine also works without any sync issues.

---

### Post by lime4x4 on 2008-09-23
how do i change the default mythvideo player?

---

### Post by lime4x4 on 2008-09-23
i found it under setup video player settings
chnaged it from mplayer to the following and everything is in sync now

xine -pfhq --no-splash

---

### Post by fenx7 on 2008-10-12
Is xine or vlc better suited for this type of problem. Ideally I would like to have all kinds of video (divx, xvid, dvd iso, m4p, etc) all working to a normal audio and video quality.

---

### Post by jbman on 2008-10-13
I am seeing this problem after installing the backports in Sept with the internal player. mplayer and vlc are fine.

Its not all xvid files just a few. The video breaks up then the audio will be out. Playing with mplayer or vlc and there is no audio or video problems with the same file.

It never happened before until i installed the backports. I have removed backports now since I don't want to have another drama like this again.

Hopefully this is fixed in 8.10

---

