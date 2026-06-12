---
title: "how to remove totem recent files"
date: 2010-02-21
forum: Multimedia Software
---

### Post by ldso on 2010-02-21
So to avoid any embarrassing situations, it would be nice to be able to turn off the "recent files" list in the totem "File" menu.  There is an archived (read only) thread that was talking about how to this.  I found a way that might be cleaner.

I know that there is a way to do it in Ubuntu under the main Gnome menu, but it doesn't work if you compile your own stuff, or use totem under some other distro, or use some other window manager, etcetera.

Anyways, the line in /usr/share/totem/totem.ui that makes the recent files list happen is:
<placeholder name="recent-placeholder"/>

You can delete it, but I like to comment out things rather than delete them, in case I want to revert my change later.  So I messed around and figured out how to make comments in the xml.  If you change it to:
<!--placeholder name="recent-placeholder"/-->
Then it is seen by the xml parser as a comment, the recent files list is excluded from the gui when you run totem, and you can uncomment it easily if you want to revert it.  This might get clobbered by a software update, so you might want to copy it to totem.ui.no_recent_files so it will stick around.

enjoy :)

---

