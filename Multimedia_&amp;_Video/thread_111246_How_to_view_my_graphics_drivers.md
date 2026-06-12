---
title: "How to view my graphics drivers ?"
date: 2006-01-01
forum: Multimedia &amp; Video
---

### Post by Fibre on 2006-01-01
I've tried fglrxinfo, but it says - command not found?

I want to try and resolve the graphical problems I'm having, but I can't even see what I've got any more.

Do I have sought out some kind of permissions problem or what?

All I've done to my pc is installed UBUNTU 5.10 / added Automatix / tvtime and updated all updatable software.

HELP!!!:(

---

### Post by mazelado on 2006-01-01
You can only use fglrxinfo to see your graphics card info if you've installed the ATI drivers. If you're sure you have a supported ATI card you can install the drivers using these instructions:

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)

Otherwise, I'm not sure how to check which graphics driver you have installed. Perhaps someone else does...

---

### Post by Fibre on 2006-01-02
Thanks Mazelado,

After ages of trying to get my 9550 back on track it worked. I followed that Wiki site,

On step 3 after rebooting I tried the last option of the 3 or so choices there that he or she gave. And also I didn't let it find it automatically. Then chose fglrx myself.

After following the steps and rebooting it didn't let me use 'fglrxinfo' - so i went into synaptic package manager and searched 'fglrx' and one of the choices that was there was 'fglrx-control' so I marked and applied it.

Went back to my Terminal and hey presto ye ha :) Happy days are here again LOL.

When I entered fglrxinfo it came up -

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

So that's it I'd say, got my sound and graphics, now to master that tvtime program?

Thanks for your help mazelado - I don't know whether I'd gotten this far before and just didn't know what was going wrong but it's all fixed now.

---

