---
title: "Disable cursor?"
date: 2008-04-29
forum: Mythbuntu
---

### Post by the[V]oid on 2008-04-29
Hi, is it possible to disable the cursor? I don't like seeing it right after login, before MythTV startup beginning.

---

### Post by justanotherhack on 2008-04-29
Strange, most people are just disturbed to see it over some videoplayers or textbrowsers that don't hide it ;) . For those, there's the unclutter package. That hides the cursor when it's not used... but you want it for the short time between login and MythTV startup, so you would have to configure it very strict or it won't do you any good.

You could change the cursor to a small, discret one, that doesn't stand out as much... but you have the problem, that it's hardly usable like that.

If you don't use the mouse at all, you could set the void driver for it. But a GUI system without a mouse....

Aside those, I can offer no suggestions, sorry.

---

### Post by the[V]oid on 2008-04-29
> **justanotherhack said:**
> If you don't use the mouse at all, you could set the void driver for it.

How can I do that? ^^ I tried setting "Driver" to "void" in the appropriate InputDevice-Section, but Xorg.log says:
```
(EE) Failed to load module "void" (module does not exist, 0)
```

---

### Post by jhfry on 2008-04-29
I think he means not to load it at all... it should be in the "Server Layout" section of your Xorg.conf file... simply comment out the line that adds the mouse device to the X11 server.

---

### Post by the[V]oid on 2008-04-30
I tried that, but it didn't work, I still can see a cursor:
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
#       InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection
```

---

