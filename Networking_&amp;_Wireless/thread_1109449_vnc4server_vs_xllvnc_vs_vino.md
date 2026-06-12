---
title: "vnc4server vs xllvnc vs vino?"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by Universal344 on 2009-03-28
I am running xubuntu and I want to be able to remote desktop connect to it from a Windows machine running vnc viewer.  I was looking the repositories and found vnc4server, x11vnc, and vino.  I was initially inclined to go with vino because it came prepacked with Ubuntu but worried about problems with it and Xfce.  That made me think about getting vnc4server, however, I read about x11vnc and that just confused me more as I could not get a good idea of exactly how it worked.  Is there one of these that is better than the others?  Please note I would prefer something straight forward, I plan on leaning more about this later but now I want to quick configuration.  Thanks for any help you can provide.

---

### Post by krunge on 2009-03-29
x11vnc is a command line tool pretty much for power users.  However, you will find some useful howtos in these forums on how to apply it to various usage scenarios.

vino, like x11vnc, shares the current X session on the physical graphics hardware.

vncserver creates virtual X sessions (RAM framebuffer only; no graphics hardware) that can only be viewed remotely.

For naive users I'd recommend vino.

---

### Post by Universal344 on 2009-03-29
Thanks for the reply.  I am now down to either vnc4server or vino.  However, is one faster than the other (faster connection between computers) and does one create more of a security hole than the other?  And will Vino integrate into Xfce like it does with GNOME (or work at all with Xfce for that matter)?

---

### Post by krunge on 2009-03-29
I don't know.  Why don't you try a few cases and report back here what you find for your usage mode and environment.

---

