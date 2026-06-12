---
title: "MythTV frontend only on TV &amp; wireless."
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by Baka no Kami on 2007-07-31
Has anyone set up MythTV frontend on a system using wireless?  I'm talking about using the Ubuntu-MythTV package that has the computer boot up into MythTV.  If so how did you setup the computer to log into your wireless automatically?

I log in under my account, log out after the wireless comes up, then let the MythTV user log in and it works fine. But the goal is to get the thing working without me having to log into my account first.


I also have another problem. The system is hooked up to a TV and I can switch the video to the TV by running 'atitvout -f t' from a terminal. But as soon as I log out the video switches back to the screen. The goal is to remove the monitor and only use the TV out. Is there a way to have the system switch the video during boot, and not switch back when a user logs in? Even if I added the command to a startup script for the MythTV user if I wanted to switch to my account to admin the system I'd lose the video when Myth exited.

---

### Post by Scorpuk on 2007-08-01
Not 100% sure about this answer, but its worth a shot.


For wireless connection try setting it to manual and input the wireless info. ie SSID, etc.


As for the TV part have you tried booting your computer with only the TV connected? I know for nVidia cards, well mine anywho, the TV out is detected on boot and is activated. I can then, at a later time, connect a monitor to it if I want to.

More often than not I'll just VNC Viewer to the desktop the mythfrontend/backend is running on to control it from my, cough, windows computer. :D

---

### Post by Baka no Kami on 2007-08-01
I had tried it with a manual config and my account will login to the wireless but the myth account still wouldn't. It was a little while back, so I'll have to try it again and see if I get any errors.

I had an old ATI card and I know they will boot up on the TV if they don't see a monitor. I didn't say before, but this system is actually a laptop, so I don't know if it'll do the same.  I was going to sell the LCD panel because it's probably worth at least half of what I could get for the system as a whole.  I'll unplug it and see what happens.

---

