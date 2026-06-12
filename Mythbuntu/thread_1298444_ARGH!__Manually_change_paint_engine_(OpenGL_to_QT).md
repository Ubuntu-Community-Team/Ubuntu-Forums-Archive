---
title: "ARGH!  Manually change paint engine (OpenGL to QT) w/o using menu system?"
date: 2009-10-22
forum: Mythbuntu
---

### Post by the_pod on 2009-10-22
Well, I just dorked out.  Messed with my settings to do tweeks and now I'm stumped.  In a nutshell, I was in the Setup > Appearance menu.  I changed the Paint Engine setting from QT to OpenGL.  Once I "finished" that menu branch the front-end crashed to the desktop, requiring a restart.

Now, sub menus no longer work, and I can't watch video.  I'm stuck being mocked by the basic menus.  I believe what I need to do is change the paint engine back to QT and not do this again but I don't know how to manually make that happen and I am surfing blind in that setup option since the sub-menu doesn't work.

Anybody have an idea?  :(

---

### Post by mitchell2345 on 2009-10-22
> **the_pod said:**
> Well, I just dorked out.  Messed with my settings to do tweeks and now I'm stumped.  In a nutshell, I was in the Setup > Appearance menu.  I changed the Paint Engine setting from QT to OpenGL.  Once I "finished" that menu branch the front-end crashed to the desktop, requiring a restart.

Now, sub menus no longer work, and I can't watch video.  I'm stuck being mocked by the basic menus.  I believe what I need to do is change the paint engine back to QT and not do this again but I don't know how to manually make that happen and I am surfing blind in that setup option since the sub-menu doesn't work.

Anybody have an idea?  :(

mythfrontend -O ThemePainter=qt

:)

~Mitchell

---

### Post by the_pod on 2009-10-22
Most excellent. Thanks.

---

