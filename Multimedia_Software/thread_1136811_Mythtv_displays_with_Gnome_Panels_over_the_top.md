---
title: "Mythtv displays with Gnome Panels over the top"
date: 2009-04-25
forum: Multimedia Software
---

### Post by scweston on 2009-04-25
Hi,

I have just done a clean install of Jaunty and added mythtv to my installation. Mythtv appears to be worked well, but the exception being that the Gnome Panels still appear at the top and the bottom of the screen. I can use the autohide feature to hide them as a workaround. But in previous versions I've never had this issue. I would like to fix it so that Mythtv appears above the gnome panels.

If anybody has experience of this or knows how to fix it then I would much appreciate your help.

I'm using an nVidia graphics card with the proprietary drivers and I do use the compiz 3D eye candy stuff if that has anything to do with the problem?

Any suggestions welcome please

Stephen

---

### Post by scweston on 2009-04-25
Hi,

Unfortunately nobody offered a solution, but I managed to find the solution myself... Yay

What I did was turn on 'Legacy Fullscreen Support' in System>Preferences>CompizConfig Settings Manager>Workarounds

Hope this solution works for anybody else having this issue.

Stephen

---

### Post by 10101011 on 2009-04-25
I was having that problem too, and the workaround option fixed it.

Many thanks. :)

---

### Post by rich86 on 2009-04-25
Brilliant thanks for that, was playing for a while to fix it.

---

### Post by belbo on 2009-04-27
Likewise. Thanks.

---

### Post by Sendervictorius on 2009-04-28
Thanks. I finally worked out that I had to install "CompizConfig Settings Manager" from synaptic first!

---

### Post by kawabago on 2009-04-28
To hide the panels you just turn off visual effects.  Go to System/Preferences/Appearance select Visual Effects tab and set it to None.

---

### Post by scweston on 2009-04-28
Thankyou Kawabago. You are certainly correct that turning off the visual effects like you describe does work. But, there are many people who would like to use mythtv alongside having the visual affects (Like me!). So in that case you can achieve that by using the 'Legacy fullscreen support' option in CompizConfig Settings Manager>Workarounds (as in post 2).  Although, as SenderVictorius suggested, you must install CompizConfig Settings Manager from synaptic first.

---

