---
title: "Unable to remotely connect after upgrade to 10.10"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ozmian on 2010-09-24
I have been using TightVNC (on XP) to remotely connect to my Ubuntu machine at home while in the office.
This just worked fine when using 10.04.
After upgrading to 10.10, I no longer can connect. 
Errormessage: Failed to connect to server (my ip)
Looked at remote desktop settings, but these are not changed. 
Port forwarding is working and I use an internal fixed ip, so I can't imagine this being a problem (I doublechecked it anyway!).
Anyone seen similar behavior? And, more interestingly, anyone know of a way to fix this?
I have seen a thread about vnc crashing, but in my situation, I do not even have the chance to crash!
Thanks in advance!!

---

### Post by seeker5528 on 2010-09-24
There was a previous thread about not being able to connect with Vinagre in 10.10 to Vino in 10.04, where other VNC client in 10.10 could connect, so if you are using Vino (the default VNC server), you might try tightvncserver or one of the others to see if there is a general problem or if it is a Vino problem.

Later, Seeker

---

### Post by ozmian on 2010-09-29
Installed X11VNC and now everything works again...
Actually, it works a lot better now!
Thanks for the tip!
:P:P:P

---

