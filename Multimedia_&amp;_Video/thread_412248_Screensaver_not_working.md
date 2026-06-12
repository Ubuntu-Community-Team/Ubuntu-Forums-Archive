---
title: "Screensaver not working"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by Tanker Bob on 2007-04-17
I am running Edgy (6.10) with a GeForce 8800GTS (nvidia driver) and Beryl. Beryl works great on my system.  I can "test" the screensavers with no problem and the GL ones look great.  However, when I set them to activate after a period of time, the screen simply blanks when the time expires.  No screensaver executes.  I've checked the settings many times, including the priority, but nothing seems to work.  Anyone have an idea?

As an alternative to the timing, is there a way to get the screensaver to activate on command?  I've searched the message database, but came up empty.

---

### Post by gunthermeyer on 2007-04-17
Are you using a lap top computer? If so, Are using battery only. If you are using battery only the screen saver will not kick in because it's trying to conserve your battery. plug your ac or power supply in and  then try to wait and you prescribed time and should kick in.r If your not using a laptop then I'm uncertain what the cause will be. This how I found out when my didn't kick until I pluged my power supply in and then it kicked right in.

---

### Post by Tanker Bob on 2007-04-17
Sorry that I didn't specify.  I'm using a desktop always on AC.

---

### Post by ar1stotle on 2007-04-17
Actually, the same thing happens to me. I'm also running Beryl... but I just updated my nvidia drivers too, so I'll see if maybe that fixed it.

---

### Post by ar1stotle on 2007-04-17
Yup, try updating your nvidia drivers. After updating mine, the screensaver just successfully initialized twice. So either that fixed it, or it was just a fluke.

[Here's the FTP directory for the drivers that worked for me. The 14mb one is what you need.](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755)

Edit: On second thought, it just loaded a blank screensaver again. Maybe it's just something Beryl related?

---

### Post by Tanker Bob on 2007-04-18
> **ar1stotle said:**
> Yup, try updating your nvidia drivers. After updating mine, the screensaver just successfully initialized twice. So either that fixed it, or it was just a fluke.

[Here's the FTP directory for the drivers that worked for me. The 14mb one is what you need.](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755)

Edit: On second thought, it just loaded a blank screensaver again. Maybe it's just something Beryl related?

Thanks for your note.  I already have version 9755 of the driver loaded. I seem to have a few other, seemingly random, issues like lines of text not painting until selected, icons on the desktop not painting until I roll the mouse pointer over them, and after running Beryl for a while (about a day) the tooltips come up as black boxes. I'm not sure if all this is Beryl or nVidia related or both.  If I don't run Beryl, it all works fine but then the 8800GTS is basically idle as well.

---

### Post by ar1stotle on 2007-04-18
I'd say it's beryl. It's not like it's final, 100% stable software yet. But it sure is fun :guitar:

---

### Post by erichgamba on 2007-06-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdeartwork/+bug/70991](https://bugs.launchpad.net/ubuntu/+source/kdeartwork/+bug/70991) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Might also have to do something with this bug

[https://bugs.launchpad.net/ubuntu/+source/kdeartwork/+bug/70991](https://bugs.launchpad.net/ubuntu/+source/kdeartwork/+bug/70991)

---

