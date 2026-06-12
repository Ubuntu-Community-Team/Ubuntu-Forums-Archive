---
title: "Terminal program White screen"
date: 2010-02-27
forum: Multimedia Software
---

### Post by frogging on 2010-02-27
OK so I'm new at this and got a problem.

My terminal program comes up as a white screen (see Screen shot picture)and so does the login screen (Like when you run updates and it asks you to log in so you can update, YES that screen)  I have searched and found nothing on this

I have a Dell Optiplex GX115 
Dell LED flat screen 49T monitor
Ubuntu 9.10
512mb ram
80gb hard drive

---

### Post by frogging on 2010-03-01
OK so let me ask it this way is there a reason why a Program like Terminal, or your login screen when you do updates ( I just blindly enter my password and hit enter and it works) comes up all whited out as the screen shot above shows.  The big white area in the picture is where Terminal loaded on the screen.

ANY AND ALL HELP WOULD BE NICE thank you all

---

### Post by frogging on 2010-03-01
OK so I may have found a solution to my problem but where do I find my xorg.cfg file and how do I edit it if I can't use Terminal.  Someone help PLEASE Need to know where the xorg files are stored in Ubuntu 9.10.

Maybe I should say the hell with Linux and go back to Win XP.

---

### Post by japadamaray on 2010-03-03
> **frogging said:**
> OK so I may have found a solution to my problem but where do I find my xorg.cfg file and how do I edit it if I can't use Terminal.  Someone help PLEASE Need to know where the xorg files are stored in Ubuntu 9.10.

Maybe I should say the hell with Linux and go back to Win XP.

for editing xorg.conf:
press Alt + F2 and type
```
gksudo gedit /etc/X11/xorg.conf
```

also, there is another terminal program that may work. try pressing Alt + F2 again and type "xterm"

---

