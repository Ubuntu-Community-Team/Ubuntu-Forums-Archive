---
title: "MPlayer ridiculously slow after upgrade"
date: 2008-05-30
forum: Multimedia Software
---

### Post by snegoviK on 2008-05-30
Hi all!

I just upgraded my system from Gutsy to Hardy and for some reason MPlayer started to play things very slow. Its literally a slide-show now so I have to relog to Windows to watch anything. In Gutsy I used to use gl2 for playing. My first guess was that 3D direct rendering was off, so I went to check that but it seems to be on:

```

sneg@snegolinux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X600
OpenGL version string: 2.1.7412 Release

sneg@snegolinux:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

```

So I am a bit clueless now. :(

Did anyone have a similar issue / can give me advice on what can done?

I am not very good at this, so if you need more info just tell me where to go and I will do what I can. :)

UPDATE:

Now that I ve checked it seems that MPlayer isn't the only thing, which is running slow. Amarok is taking 70-80% of my cpu at all times and everything else slows down significantly when its running... I tried MPlayer when Amarok closed but... That obviously didn't help. Perhaps its the power management? I have no idea. :( Help me, good people...

Thank you all in advance,
sneg

---

