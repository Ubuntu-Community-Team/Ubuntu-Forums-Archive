---
title: "No XFCE desktop after exiting the 9.04 frontend"
date: 2009-06-03
forum: Mythbuntu
---

### Post by therealbrewer on 2009-06-03
After a long but victorious struggle with getting TVout and X working with my PVR-350 and 9.04, I seem to have come up with an unusual problem. When I exit from the frontend, I just get a blank screen with a mouse pointer. No panel, no menus, nothing. When I right-click, no context menu comes up. However, if I hit Alt-F2, I can get a "run application" dialog, and from there I can run xterm and/or any graphical tool I can think of, so X is basically working. If I run firefox and download something from the net, even though firefox saves it to the desktop, I don't see the download on my blank screen. Yet if run thunar, and browse to the desktop, my download is there, so clearly the XFCE desktop is somehow not fully started. Everything I've described also happens if I don't exit the frontend, but rather just switch to the second desktop using ctrl-alt-right arrow. Nothing obvious stands out in the logs.

Suggestions?

---

### Post by klc5555 on 2009-06-03
> **therealbrewer said:**
> After a long but victorious struggle with getting TVout and X working with my PVR-350 and 9.04, I seem to have come up with an unusual problem. When I exit from the frontend, I just get a blank screen with a mouse pointer. No panel, no menus, nothing. When I right-click, no context menu comes up. However, if I hit Alt-F2, I can get a "run application" dialog, and from there I can run xterm and/or any graphical tool I can think of, so X is basically working. If I run firefox and download something from the net, even though firefox saves it to the desktop, I don't see the download on my blank screen. Yet if run thunar, and browse to the desktop, my download is there, so clearly the XFCE desktop is somehow not fully started. Everything I've described also happens if I don't exit the frontend, but rather just switch to the second desktop using ctrl-alt-right arrow. Nothing obvious stands out in the logs.

Suggestions?

I hadn't noticed this when I posted in your other thread.

What happens in your blank terminal when you type startxfce4 ?

---

### Post by therealbrewer on 2009-06-03
Hey, thanks again...

startxfce4 tells me that an x window manager (or session manager) is already running.

I noticed that if I do "xfdesktop" then I get the default wallpaper instead of a blank screen, and right clicking works, but still no panel. On the other hand, if I do "xfce4-panel", I get the panel, but no desktop. Neither of these gives any error messages.

Seems like the launch of the desktop and panel isn't completing, but I'm not sure why. I have to wonder are there any other, perhaps less obvious, components that are not starting properly? How could I tell?

Oh, and one more thing, after I noticed this problem, I installed NX and connected to the myth box from another machine. In this case, my remote session launches the XFCE desktop just fine.

---

### Post by klc5555 on 2009-06-03
> **therealbrewer said:**
> Hey, thanks again...

startxfce4 tells me that an x window manager (or session manager) is already running.

I noticed that if I do "xfdesktop" then I get the default wallpaper instead of a blank screen, and right clicking works, but still no panel. On the other hand, if I do "xfce4-panel", I get the panel, but no desktop. Neither of these gives any error messages.

Seems like the launch of the desktop and panel isn't completing, but I'm not sure why. I have to wonder are there any other, perhaps less obvious, components that are not starting properly? How could I tell?

Oh, and one more thing, after I noticed this problem, I installed NX and connected to the myth box from another machine. In this case, my remote session launches the XFCE desktop just fine.

So this is happening whenever X starts up? And not just after you have run your PVR350 and then exited from mythfrontend?

It sounds a bit like xfce-mcs-manager isn't running at the start of startxfce4, or that startxfce4 isn't in your .xinitrc, or that an environment variable for xfce4 is not set properly --you might want to start combing a bit through the setup docs for xfce4 at [http://www.xfce.org/documentation/4.2](http://www.xfce.org/documentation/4.2)

---

### Post by therealbrewer on 2009-06-03
OK, well as silly as it sounds, all I had to do was this:

exit the frontend, then

xfdesktop &
xfce4-panel &

log out and select "remember these settings for the next session?"

log back in, or reboot, and everything was OK.


One small issue though - how can I make mythfrontend.real keep the "Always on top" property so that the panel stays behind? I mean, I can manually do this anytime I boot the system, but can I get that to stick so I don't have to do it each time?

---

### Post by klc5555 on 2009-06-04
> **therealbrewer said:**
> OK, well as silly as it sounds, all I had to do was this:

exit the frontend, then

xfdesktop &
xfce4-panel &

log out and select "remember these settings for the next session?"

log back in, or reboot, and everything was OK.


One small issue though - how can I make mythfrontend.real keep the "Always on top" property so that the panel stays behind? I mean, I can manually do this anytime I boot the system, but can I get that to stick so I don't have to do it each time?

Seems like you might need to save your xfce settings and exit xfce while mythfrontend.real is still running. Or make sure mythfrontend.real is among the AutoStarted applications in Settings.

---

