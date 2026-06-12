---
title: "ssh -X/-Y remote viewing of specific app"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by cheway on 2012-06-13
This must be possible.

Could I...

-Get an application open on Machine A.
-ssh -X into Machine A from Machine B.
-On Machine B, view (nothing else) the application on Machine A, whilst the application is being used?

The application in question will be a virtual machine (provided by VirtualBox).

Cheers, Matt.

---

### Post by cheway on 2012-08-02
The answer to this, is no.

Cheers,
Matt.

---

### Post by papibe on 2012-08-03
Hi cheway.

Strictly no. Not using X forwarding over ssh.

However, it is a **[COLOR="Red"]YES[/COLOR]** for a VM. You can connect using Virtualbox's remote desktop (VRDP) from machine to a GUI screen of a VM on machine A.

Let us know if you need more help with that.
Regards.

---

### Post by cheway on 2012-08-03
Hi thanks for the reply.

Yes I had good sucess forwarding vbox windows, in fact with -c flag it was good enough for me to be able to use a CAD program, in XP, running inside a VirtualBox! I was amazed. So that's...

> ssh -X -C <username>@<IP>

...for anybody who's interested.

Whilst I find this very useful, I still haven't been able to work out how to allow a remote user to then connect to this same window for a collaborative effort. And I don't think this is possible.

We have however worked how to do it with VNC (so sharing the whole desktop) which seems to work well.

Cheers,
Matt.

---

