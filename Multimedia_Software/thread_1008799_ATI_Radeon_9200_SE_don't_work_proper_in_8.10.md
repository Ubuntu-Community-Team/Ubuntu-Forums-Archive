---
title: "ATI Radeon 9200 SE don't work proper in 8.10"
date: 2008-12-11
forum: Multimedia Software
---

### Post by zenkaon on 2008-12-11
Hello,
my lspci | grep VGA says
```

01:05.0 VGA compatible controller: ATI Technologies Inc RV280 [ Redeon 9200 SE] (rev 01)

```

I've had ubuntu's back to Feisty Fawn that have worked well (and flashy/show off) with this card.

However on a new install to 8.10 I cannot get any desktop effects working. If I goto:
system->Appearance and then in the tab "Visual Effects"

Even the setting "Normal" tells me that "Desktop effects could not be enabled"

This is a bit rubbish really. I used to have fancy compiz effects in 8.04 on the same PC and now I can't do squat.

Can someone please advice??
I'll be happy to give whatever info about the GPU as you want, it'll be a learning curve for me!!

Hope someone can help 
Cheers

---

### Post by IIIVAlive on 2009-06-24
I'm having the same issue in 9.04, and I have a blank xorg file.  When I try to enable compiz, I get a "searching for device driver" wait bar, and then a message that desktop effects could not be enabled.

I'm using the open-source ATI drivers on a fresh install of 9.04 desktop.

$ lspci -nn | grep VGA
01:04.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)


$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

$ glxinfo | grep "direct rendering"
direct rendering: Yes

---

