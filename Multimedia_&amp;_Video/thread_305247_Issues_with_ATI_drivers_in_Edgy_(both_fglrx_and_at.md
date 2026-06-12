---
title: "Issues with ATI drivers in Edgy (both fglrx and ati)"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by eye208 on 2006-11-23
Hello!

I've got an ATI X800 GT in my desktop PC and a Mobility X700 in my laptop. When I use Blender (2.42a) with fglrx (latest version) on Ubuntu Edgy, the menus in the program are not drawn anymore when I open them, i.e. they are invisible. This doesn't happen with the same fglrx on Dapper, so I think it's an X.org issue, maybe related to AIGLX.

Since I don't want to go back to Dapper, I tried using X.org's own ATI driver ("ati") instead of fglrx. It works fine with Blender, but not with Firefox. Some websites, when opened in Firefox, cause X.org to freeze with the ati driver. This doesn't happen with fglrx, and it doesn't happen with Konqueror either. It's just Firefox + ati = freeze. This happens with both Dapper and Edgy.

I've spent some time investigating the problem and found a page that makes those freezes very easy to reproduce. Here's the URL:

[http://home.arcor.de/eye208/xorg-ati-firefox-crash/](http://home.arcor.de/eye208/xorg-ati-firefox-crash/)

This is the xorg.conf I am using:

[http://home.arcor.de/eye208/xorg-ati-firefox-crash/xorg.conf](http://home.arcor.de/eye208/xorg-ati-firefox-crash/xorg.conf)

As you can see, the config is nothing special. Of course I played with some options afterwards, but none of them affected the crashes in any way. When I remotely log into a machine after it freezes, "top" shows the Xorg process consuming 99.9% CPU. It cannot be killed using "kill -9" either. The rest of the system seems to work just fine. The mouse pointer can still be moved, but X doesn't register any clicks or keypresses.

Since I need both Blender and Firefox, I'm running short of options now. The vesa driver is too slow and consumes too much CPU which is a serious problem on the laptop (battery, fan). The only option left would be to go back to Dapper where at least fglrx doesn't give me any issues.

Any ideas how to make fglrx display Blender's menus properly again or how to stop the "ati" driver from crashing with Firefox? Either would be fine. Thanks in advance!

---

### Post by daradib on 2006-11-23
I'm not exactly sure. I know for one thing that you would probably be better off with XGL and Beryl instead of Aiglx on an ATI card. Aiglx requires 3D and composite extensions, but composite extensions must be disabled to enable 3D support in fglrx. I'm not sure since you said you had support in Dapper.

I have ATI X800 and I had no problems with XGL and Beryl.

To disable Composite extensions, add the following lines to the end of /etc/X11/xorg.conf file:

Section "Extensions"
Option "Composite" "false"
EndSection

You will get 3D, DRI, and OpenGL support.

---

