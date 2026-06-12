---
title: "one more 'i followed a walk-through and now compiz is busted' thread :( ati m300/7.10"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by ijason on 2007-11-18
hey all. well, i ignored some advice to wait another two weeks to get newer drivers from ATI and followed this ([http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)) walk-through to the letter. everything on it seemed to work fine, except that when i ran compiz it spat out some pretty important sounding errors... and fails to work. :(

here are the error messages on running the "SKIP CHECKS=yes compiz" :
> 
jason@jason-laptop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "XFree86-DRI" missing on display ":0.0".
present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed


the good news is, that at least the drivers work well enough for the screen to look fine, i just would love some help getting compiz to work with the new drivers >,<

---

