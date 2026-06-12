---
title: "Add Icons to Desktop"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jethro10 on 2011-04-06
Hi,
I've just looked at this new version (11.04) for the first time last night, and I'm stuck on something - well many things, but we'll start here!
How to add an icon to the desktop. It seems a forbidden function?

I can add to the bar on the left easy enough though.

Strange thing is that I upgraded from the previous version of ubuntu and the icons that were on the desktop are still there.

I've looked into the Desktop folder in Nautilus but I can't drag into there either.
It doesn't look like a permission thing either.

Funny thing, I've been searching for a comprehensive tutorial on the new interface and can find nothing substantial.

Thanks
Jeff

---

### Post by coffeecat on 2011-04-06
> **jethro10 said:**
> How to add an icon to the desktop. It seems a forbidden function?

What sort of icon? If I right-click on the Unity desktop I can add a folder, launcher or document just as in classic gnome. If I want computer, home, network, trash and/or volumes icons on the desktop, I can do that in gconf-editor just as in classic gnome.

What exactly did you try which didn't work for you?

One useful feature of the Unity desktop is that if I create a custom launcher on the desktop, I can drag it into the dock.

---

### Post by kerry_s on 2011-04-06
You can drag & drop from /usr/share/applications to the desktop.

---

### Post by coffeecat on 2011-04-06
> **kerry_s said:**
> You can drag & drop from /usr/share/applications to the desktop.

I get a "permission denied" if I try that - to the desktop, that is. OK dragging to the dock, though.

---

### Post by RomeReactor on 2011-04-06
You can copy the launcher from **/usr/share/applications** to your home directory; once there, right-click it, go to **Properties->Permissions**, mark it as executable, and move it to the desktop.

---

### Post by coffeecat on 2011-04-06
> **RomeReactor said:**
> You can copy the launcher from **/usr/share/applications** to your home directory; once there, right-click it, go to **Properties->Permissions**, mark it as executable, and move it to the desktop.

Not here. The problem with drag and drop copying is that the launchers in /usr/share/applications are owned by root. You'd have to do a 'sudo cp' and then a chown and chmod to get the permissions and ownership right. In which case one might just as well do that straight to the desktop.

Whatever - a bit off-topic. We need to see what the OP is having problems with.

---

### Post by RomeReactor on 2011-04-06
> **coffeecat said:**
> The problem with drag and drop copying is that the launchers in /usr/share/applications are owned by root.
Correct. However, I didn't suggest a drag and drop.

> You'd have to do a 'sudo cp' and then a chown and chmod to get the permissions and ownership right. In which case one might just as well do that straight to the desktop.
Copying/pasting does work, even from **/usr/share/applications** and paste directly on the desktop (right-click, select "Copy to-->Desktop") without need to mark the launcher as executable, as it will already be executable. Tested with the default user account (me) and an unprivileged second user account. Could be a permissions thing on my system, but I doubt it.

---

### Post by coffeecat on 2011-04-06
> **RomeReactor said:**
> right-click, select "Copy to-->Desktop"

OK. I see what you mean now. That works just fine. Useful to know.

---

### Post by jethro10 on 2011-04-06
> **coffeecat said:**
> Not here. The problem with drag and drop copying is that the launchers in /usr/share/applications are owned by root. You'd have to do a 'sudo cp' and then a chown and chmod to get the permissions and ownership right. In which case one might just as well do that straight to the desktop.

Whatever - a bit off-topic. We need to see what the OP is having problems with.

Yeah, that seems to be it, permissions.
I should have originally said, oops! that "if you drag an icon from the menu to the desktop"
It all looks quite slick, but seems a big step back in functionality.

J

---

### Post by jethro10 on 2011-04-06
> **RomeReactor said:**
> Correct. However, I didn't suggest a drag and drop.


Copying/pasting does work, even from **/usr/share/applications** and paste directly on the desktop (right-click, select "Copy to-->Desktop") without need to mark the launcher as executable, as it will already be executable. Tested with the default user account (me) and an unprivileged second user account. Could be a permissions thing on my system, but I doubt it.

Ok, this looks like the answer, it's a bit counter intuitive, not many folk would need to know /usr/share/applications as opposed to dragging from the menu like you could with gnome.
Still, needs must!
Thanks, I'll try that tonight.
J

---

