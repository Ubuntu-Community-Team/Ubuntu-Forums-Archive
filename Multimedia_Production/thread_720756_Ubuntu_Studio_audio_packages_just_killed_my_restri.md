---
title: "Ubuntu Studio audio packages just killed my restricted drivers =/"
date: 2008-03-10
forum: Multimedia Production
---

### Post by alexforcefive on 2008-03-10
Hi guys, this is more of a warning than a request for help. I'm running Gutsy on an AMD 64 and after reading an article, I decided to install some Ubuntu Studio packages from the synaptic package manager. BIG MISTAKE!

After rebooting and logging in, I was presented with a completely white screen. No icons, pointer, menus, nothing. So I killed X, switched to a failsafe gnome session and uninstalled the ubuntu studio packages. Restarted and nothing! Still the white screen!

Long story short, Ubuntu Studio had for some reason UNINSTALLED the linux-restricted-modules package and killed my ati drivers. Maybe this is standard procedure? Anyway, I wasn't expecting it so I guess other people might get caught out.

So, if you're going to install this package, disable your restricted drivers first!

PS if I have the wrong end of the stick, I'd love to hear what I did wrong

---

### Post by alexforcefive on 2008-03-10
Sorry for the double post, but now I do need to ask for help. In addition to killing linux-restricted-drivers, it also killed my fglrx driver, and I can't get it to reinstall. Getting it installed in the first place was hard because I have an ATI x1950 agp, but when I follow the method I used before, it just... doesn't work. I don't understand it!

Can anyone help?

---

