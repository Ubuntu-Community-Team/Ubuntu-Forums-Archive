---
title: "How do I run dvds fullscreen in VLC player?"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by bwallum on 2007-08-18
Hello

I have dvds running using VLC player. I set it to fullscreen and most of the desktop disappears. However  am left with the very top and very bottom desktop menus/status lines.

In windowsXP a double click toggles between fullscreen (no desktop visible/black top and bottom bands on 4:3 monitor) and a window version on the desktop.

How do i get 'fullscreen'  in Ubuntu please?

Kind Regards
Bob

---

### Post by crispy_420 on 2007-08-18
Mine seems to work with double click just as in windows. And I haven't done any tweaking to it.

---

### Post by djrobthaman on 2007-08-19
Hi there,

I have the same problem and found a quick fix.  You can go into the preferences dialogue and navigate to Video > Output Modules.  Then click the "Advanced Options" check box on the bottom right.

You can then change output mode to x11 or xvideo.  When your done with this, in the sidebar click on x11 or xvideo (whichever one you chose... it should be a submenu item in the output modules menu) and click the "Alternate fullscreen menu" checkbox.  Once you save these settings your vlc should show fullscreen.

There is a problem with this method though.  Apparently when you do this the fullscreen vlc totally bypasses the window management system (or that's what I read when I found out about this method) so what I have found is that some of the keyboard shortcut controls (most noticeably play/pause and the current position display) don't work all the time when you're in fullscreen mode.  But you can always just use the mouse and doubleclick to get it back out of fullscreen and everything works.

---

### Post by bwallum on 2007-08-19
Works a treat, thank you for your help. followed your instructions precisely. It now starts full screen and when I double click it puts it in a window and gives me full access to desktop menus etc...perfect!

I found I had to reboot to get sound back though..curious.

Kind Regards
Bob

---

