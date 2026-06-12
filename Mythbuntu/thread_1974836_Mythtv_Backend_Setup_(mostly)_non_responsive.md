---
title: "Mythtv Backend Setup (mostly) non responsive"
date: 2012-05-06
forum: Mythbuntu
---

### Post by bhusa2012 on 2012-05-06
Upgraded from 11.10 0.24 to 12.04 0.25, fortunately most everything is working. However, I'm unable to change most backend settings using MythTV Backend Setup.
When running MythTV Backend Setup, the only menus I'm able to enter are "Channel Editor" and "System Events". All of the other options just cause the system to hang until hitting escape. Same is true for most of the setup items within mythfrontend.

Update:

Just noticed that the display is stuck on the main menu in Mythtv Backend Setup, while in the background, it is actually paging through the menu. I can see a flash of the intended menu if I hit escape or page through the entire menu.

Any ideas why the backend setup menus will not draw?

Thanks in advance!

---

### Post by nickrout on 2012-05-07
> **bhusa2012 said:**
> Upgraded from 11.10 0.24 to 12.04 0.25, fortunately most everything is working. However, I'm unable to change most backend settings using MythTV Backend Setup.
When running MythTV Backend Setup, the only menus I'm able to enter are "Channel Editor" and "System Events". All of the other options just cause the system to hang until hitting escape. Same is true for most of the setup items within mythfrontend.

Update:

Just noticed that the display is stuck on the main menu in Mythtv Backend Setup, while in the background, it is actually paging through the menu. I can see a flash of the intended menu if I hit escape or page through the entire menu.

Any ideas why the backend setup menus will not draw?

Thanks in advance!

Try changing your theme, or changing between the xv painter and the opengl painter.

---

### Post by theopulus on 2012-05-07
> **bhusa2012 said:**
> Upgraded from 11.10 0.24 to 12.04 0.25, fortunately most everything is working. However, I'm unable to change most backend settings using MythTV Backend Setup.
When running MythTV Backend Setup, the only menus I'm able to enter are "Channel Editor" and "System Events". All of the other options just cause the system to hang until hitting escape. Same is true for most of the setup items within mythfrontend.

Update:

Just noticed that the display is stuck on the main menu in Mythtv Backend Setup, while in the background, it is actually paging through the menu. I can see a flash of the intended menu if I hit escape or page through the entire menu.

Any ideas why the backend setup menus will not draw?

Thanks in advance!

I've suffering the same problem. After "resetting" mythfrontend I  found out that the problem came from "OpenGL" painter. Everything worked OK with Qt painter.

The problem is that I'm using a Zotac AD02 with AMD E350 Zacate and to have VAAPI enabled and watch any movie I'v got to enable OpenGL so at this moment MythTV is useless to me...

Does anyone know how can this be fixed?

---

### Post by ps3681 on 2012-07-11
I'm having this problem (non-responsive backend and front end setups)... this just recently started happening.  Help?  how do I change painters if I cant get into the setup screens for backend/frontend.

---

### Post by nickrout on 2012-07-11
> **ps3681 said:**
> I'm having this problem (non-responsive backend and front end setups)... this just recently started happening.  Help?  how do I change painters if I cant get into the setup screens for backend/frontend.

```
mythfrontend -O ThemePainter=qt -O UIPainter=qt
```

---

