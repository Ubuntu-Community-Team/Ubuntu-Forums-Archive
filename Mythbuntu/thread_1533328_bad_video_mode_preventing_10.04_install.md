---
title: "bad video mode preventing 10.04 install"
date: 2010-07-17
forum: Mythbuntu
---

### Post by mgrusin on 2010-07-17
Hi, I'm doing a long overdue upgrade of my MythTV, which uses S-Video output from an older NVidia card.  So far this has worked beautifully and I want to keep this connection through the upgrade.

I'm trying to install Mythbuntu 10.04.  The CD boots to the menu fine, and the screen showing the menu is clear, but any of the options lead to a "rolling" video screen mode that I can't read.

I was hoping the "advanced options" menu item would have a graphics-safe mode, but there's nothing under that menu... ?

Any ideas on what to do or try?

Thanks! -Mike.

---

### Post by mgrusin on 2010-07-18
Think I solved it - hitting F6 at the right time does bring up some boot options, "nomodeset" did the trick for me.

Part of my problem may have been that I was trying to install off of an .ISO on a USB FLASH drive; when I burned a real CD it worked much better.

Thanks, hope this helps someone else. -Mike.

---

