---
title: "[SOLVED] VNC viewer"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by daanbrg on 2007-08-12
Hi guys,

Today I set up the preferences from Remote Desktop at my Ubuntu computer (Ubuntu 7.04, "Feisty"), because I wanted to control my computer at my Windows XP computer.

I already had installed VNC because I have some other Windows XP computers on the network which I also control with the VNC viewer.

So, I put in the IP adress of the Ubuntu computer with :0 behind it, and pressed OK.

He asked for my password, I filled in my password and pressed Enter.

And then...
[(click here to watch image)]("http://www.mediafire.com/?6tm0nwkgmh5")

I clicked no, changed the password, tried again on the Windows PC, but it won't work :( :confused:

Why doesn't it works :confused:

Please help me...

My Ubuntu computer is a IBM NetVista with 112MB RAM and a 20GB hard disk drive, 2,4 GB is used.

My Windows XP computer is a Acer Aspire T650 with 768MB RAM and 2 harddisks from 160GB and one from 80GB.

Thanks in advance for helping me!

---

### Post by uclalinux on 2007-08-12
are you using VNC or  RDP,

---

### Post by daanbrg on 2007-08-12
> **uclalinux said:**
> are you using VNC or  RDP,

I use VNC to control the computers in my network.

I don't know what you mean with RDP :)

I set up the "server" on my Ubuntu computer by going to System > Preferences > Remote Desktop.

I switched on:
[LIST]
[*]Allow other users to view your desktop (Sharing)
[*]Allow other users to control your desktop (Sharing)
[*]Require the user to enter this password: (Security)
[/LIST]

Is this clear enough or do I need to collect more information, what information and how do I get the information?

Let me know it!

---

### Post by uclalinux on 2007-08-12
try to connect to your self, 

in the terminal type: vncviewer (yourip):0

---

### Post by xtremepinoy on 2007-08-12
try tightvnc..work fine for winxp to ubuntu pc. [www.tightvnc.com](www.tightvnc.com)

---

### Post by daanbrg on 2007-08-13
> **uclalinux said:**
> try to connect to your self, 

in the terminal type: vncviewer (yourip):0

Hi there!

I just installed ThightVNC Viewer, and tried it again. Still didn't worked, so than tried it your way.

I typed into the terminal:

```
24.132.95.30:0
```

...and it said that there were too much security failures...

...so then I typed:

```
daanpc:0
```

It worked! But, that's ehm... *internal*, not on the network. So, what is my networkname, and must there be \\ before the networkadress when typing into VNC Viewer (well, that's how it works with Windows PC's in a network...)?

[CENTER]**[COLOR="Red"]EDIT:[/COLOR]**[/CENTER]

I just found out "*24.132.95.30*" is the IP-adress from my router :oops:
Now I want to find out what my network name is and, what I asked already above: does it works the same as Windows' network names; like your computer is named Acomputer, you should type at VNC viewer:
```
**\\**Acomputer:vncport
```

So, help me with that, I would appreciate that.

Thanks in advance!

---

### Post by Scorpuk on 2007-08-13
When you were trying VNC viewer with your first method you mention:

> I switched on:
Allow other users to view your desktop (Sharing) 
Allow other users to control your desktop (Sharing) 
Require the user to enter this password: (Security) 


Did you also uncheck:

Ask you for confirmation (security)


Unfortunately I'm at work and their web filter wont allow me to view your image. :|

---

### Post by daanbrg on 2007-08-13
> **Scorpuk said:**
> When you were trying VNC viewer with your first method you mention:



Did you also uncheck:

Ask you for confirmation (security)


Unfortunately I'm at work and their web filter wont allow me to view your image. :|

Nice try, but it has always been switched off...

Some other suggestions...?

---

### Post by daanbrg on 2007-08-14
Ehm... anyone...?

---

### Post by daanbrg on 2007-08-14
:confused: Does really nobody has an answer? :confused:

:confused::confused:
Disappointing, a bit confused; the forum has been for me always the best place to find support or tips and tricks for my Linux system.

I believe you guys up there in the U.S. (I'm sitting here in Holland, I'm Dutch) just don't know the answer.

Does anybody has an idea, because I want to get it work!

If the Linux-installed client doesn't works, tell me please which program should work.

Please, please, please, help me to get it work!

Daan.

---

### Post by daanbrg on 2007-08-15
I'm closing down this thread, no one is responsing.

If someone has an tip or response, please mail it to me or send me an private message.

Thanks.

Daan.

---

### Post by uclalinux on 2007-08-15
did you try to connect to your self on the ubuntu meachine?

"vncviewer (your IP:0)"

---

