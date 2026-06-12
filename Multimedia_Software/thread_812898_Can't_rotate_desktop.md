---
title: "Can't rotate desktop"
date: 2008-05-30
forum: Multimedia Software
---

### Post by Mark Phelps on 2008-05-30
Trying to get Hardy working on my Tablet PC with the stylus.  The PC has a rotating lid that uses either portrait or landscape mode.  Tried testing its rotation using the Screen Resolution panel by selecting Right under rotation.

But I can't reset it!

Problem is that when the desktop appears, it's just blank.  There are no upper or lower bars or any menus.  Clicking with the mouse does nothing.

I've tried doing a dpkg-reconfigure xserver-xorg, and while that appears to work, once I reboot, using ctl-alt-backspace, I'm back to no menu bars again.

I've booted into the console (Alt-F2) and run a rotate script to reset the orientation, but it fails due to no desktop being displayed.

Without the menu bars, I know of no way to open an X-term on the desktop so I can enter commands.  Also, I believe that there is a dpkg-configure (something) that launches the screen resolution panel, but again, without a command window, I know of no way to do that.

Can someone help me?

---

### Post by Mark Phelps on 2008-06-04
WOW -- 5 days and not a single response!  Guess this is too tough a question for anyone to answer...

---

### Post by wenuswilson on 2008-06-04
Well I don't have that computer but I have a question.

When the computer goes "blank" is the desktop itself still visible and is there a text box cursor somewhere on the screen? If so, put your password into the "invisible" textbox.

Do you have compiz or any other desktop effect app? That could be the problem, try reinstalling...

Other than that, I don't know.

---

### Post by Mark Phelps on 2008-06-05
No, the desktop is no longer visible.  In subsequent testing, I disabled compiz and the problem goes away.

But I was still hoping that someone could tell me how I could insert something into the startup process that would force the display to come up in "landscape" mode.

Guess no one knows how to do that.

---

