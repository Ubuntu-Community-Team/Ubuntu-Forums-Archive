---
title: "[Mythbuntu 9.10] VNC not working"
date: 2010-01-19
forum: Mythbuntu
---

### Post by Techmanm on 2010-01-19
I have just upgraded my system to mythbuntu 9.10 and now VNC is not working.
I have enabled VNC in Mythbuntu control centre.

I still can not connect to the vnc server.

Please help!

---

### Post by kja999 on 2010-01-19
I would punt for installing manually (sudo synaptic on the command line) ..
or maybe tthis will help : [http://ubuntuforums.org/showthread.php?t=623902]("http://ubuntuforums.org/showthread.php?t=623902")

---

### Post by superm1 on 2010-01-20
> **Techmanm said:**
> I have just upgraded my system to mythbuntu 9.10 and now VNC is not working.
I have enabled VNC in Mythbuntu control centre.

I still can not connect to the vnc server.

Please help!

Have you restarted or at least logged out/in since?  The VNC thing only starts in the mythbuntu session type and upon login.

---

### Post by Techmanm on 2010-01-20
> **superm1 said:**
> Have you restarted or at least logged out/in since?  The VNC thing only starts in the mythbuntu session type and upon login.

Yes, i have.
I also removed the packeges and reinstalled them.
This still not worked.

---

### Post by superm1 on 2010-01-20
> **Techmanm said:**
> Yes, i have.
I also removed the packeges and reinstalled them.
This still not worked.

Ok, so the next thing to do is to see if x11vnc is even spawning.

```
ps aux | grep x11vnc

```
should do the trick

---

