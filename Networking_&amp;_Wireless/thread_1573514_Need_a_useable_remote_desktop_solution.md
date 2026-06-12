---
title: "Need a useable remote desktop solution"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by foxmajik on 2010-09-12
Hi all,

I'm looking for a useable remote desktop solution that works like Microsoft's RDP.

The included "remote desktop" vnc server in Ubuntu doesn't work because every time I want to log in remotely, I have to first go sit down in front of the machine running ubuntu, log in, disable desktop effects, then manually adjust the desktop resolution to fit the target guest machine.  I can't really do that if I'm on my laptop at the airport.

Some things I have tried:

NoMachine NX does not work because once I've launched applications remotely on my laptop there's no way to get them back once I'm at the machine locally.  Also, there's a sound feature, but it doesn't work.

Remote X11 doesn't work for the same reasons.


What I need:

1. I need to be able to launch an application remotely, then when I get home, go sit at the machine locally and use that application there without having to re-launch it.

2. I need to be able to hear the sound playing on the remote computer.

3. I need it to work with desktop effects enabled.

Essentially, I want it to "just work" the way Windows' Remote Desktop works.

Any suggestions?

---

### Post by Greycloak on 2010-09-12
Have a look at Teamviewer. It's available for both linux and windows, and should do the trick. You have to have it installed on both systems however. On the windows machine you can even configure it to run as a service so that if the machine reboots you will still be able to log back in via the Teamviewer connection. Also, in order to enable desktop effects you will need to tweak the default settings a bit.

---

### Post by foxmajik on 2010-09-12
> **Greycloak said:**
> Have a look at Teamviewer. It's available for both linux and windows, and should do the trick. You have to have it installed on both systems however. On the windows machine you can even configure it to run as a service so that if the machine reboots you will still be able to log back in via the Teamviewer connection. Also, in order to enable desktop effects you will need to tweak the default settings a bit.

Can you please tell me the settings I need to tweak?

---

