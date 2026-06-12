---
title: "Remote login via XDMCP defaults to classic desktop"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-03-12
I am glad to see XDMCP is available again in Natty after it was missing in Maverick.

When I login to Natty via XDMCP it defaults to the classic desktop even when I specify that I want to use Unity.

Am I correct in assuming this is because compiz is not supported in XDMCP?

---

### Post by seeker5528 on 2011-03-12
> **JRV said:**
> I am glad to see XDMCP is available again in Natty after it was missing in Maverick.

When I login to Natty via XDMCP it defaults to the classic desktop even when I specify that I want to use Unity.

If the classic desktop is working, that should be compiz+panel.
Classic with no FX would be Metacity+Panel.

What I see when I do it is....

When choosing Unity, no window manager no panels.

When choosing Ubuntu Classic, no window manager, but I do get the panels.

Have not tried the classic with no FX yet.

EDIT: Did the no FX login, works fine and I have compositing enabled so I could use Docky with it so compositing by itself doesn't seem to be an issue. If you google for it it seems people have gotten it to work with Compiz, but Compiz hasn´t been the most friendly to it.

EDIT2: I don´t find anything that makes it seem like something special needs to be done in order for OpenGL to work, but it could be a driver issue on the box the X server is running on (the one you are sitting at when attempting to connect to the remote desktop).

Later, Seeker

---

