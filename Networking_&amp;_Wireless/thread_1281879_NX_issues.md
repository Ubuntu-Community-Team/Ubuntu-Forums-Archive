---
title: "NX issues"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by caustic386 on 2009-10-03
I've found quite a few scattered threads on the subject, and ultimately it looks like there's a bug preventing NX connections from functioning properly when visual effects are activated.  As a workaround, I've found in NX's server.cfg a few options to run scripts during the logon/logoff procedure.  Can someone recommend a few good commands to disable visual effects upon logon, and then re-enable them on logoff?  I've found metacity --replace and compiz --replace , but those had some awkward effects when I tried them out locally (terminal window froze and/or resized off the screen).

Also, when I change my SSH and NX port from anything but 22, my connections fail authentication.  I'm setting "Listen port" in sshd_config and server.cfg (2 settings total).  Are there extra steps I'm missing?

Running 9.04, BTW.

---

### Post by kreggz on 2009-10-03
You might be able to run a script upon login for you ssh user, see this:

[https://help.ubuntu.com/community/EnvironmentVariables#Graphical%20desktop-related%20variables](https://help.ubuntu.com/community/EnvironmentVariables#Graphical%20desktop-related%20variables)

In regards to NX on a different port you could try a port forward on the router.

---

### Post by caustic386 on 2009-10-04
I just decided to drop the desktop effects until they're worked out properly.

As for the port, I switched back to FreeNX because it seemed much easier to manage, but just as effective.  All is well there, now.

The problem with FreeNX, however, seems to be the Ubuntu thinks those packages aren't needed.  Computer Janitor and/or apt-get autoremove blows them away.  Is there any way to specify that I want to keep them?  Occasionally I'll run a command I'm not familiar with (aptitude install was tonight's mistake), and it'll delete them without warning.

Thanks!

---

