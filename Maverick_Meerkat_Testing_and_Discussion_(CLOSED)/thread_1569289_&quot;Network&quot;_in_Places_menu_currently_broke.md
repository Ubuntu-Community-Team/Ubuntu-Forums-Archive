---
title: "&quot;Network&quot; in Places menu currently broken"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by exploder on 2010-09-06
Getting an error and cpu use on one core staying at 100%. Anyone report this yet? I can easily reproduce the error if need be.

---

### Post by exploder on 2010-09-06
Here is the eror.

Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.

---

### Post by coffeecat on 2010-09-06
I get this with other parts of Nautilus. Clicking on Network in Places gives me the whirly wheel for a time, but no error, and after a couple of minutes the desktop goes back to normal. When I opened a Nautilus window, did a ctrl-L to get a text path address bar, and typed in 'smb://servername/' I got the Dbus error message after a long time. Then I tried 'smb://192.168.1.100/' (my NAS network address) and got the whirly wheel for ages.

Finally, File > Connect to Server with the smb://192.... address gave me a whirly wheel for ages as well, and then the Dbus error after at least 5 minutes. Or that could have been the Dbus error after one of the above.

However, 'smb://192.168.1.100' in a Firefox address bar connected me to the server in seconds. But when I tried to download a file from the Public folder on the NAS, I got "Error while copying" and "The specified location is not mounted."

**edit:** and now I've got two "could not display..." windows on the desktop which won't close and neither will the nautilus windows.

---

### Post by whoop on 2010-09-06
Whoah, glad I'm not the only one:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/631740](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/631740)

---

### Post by exploder on 2010-09-06
Thanks guts! I added to the bug report as well.

---

### Post by whoop on 2010-09-06
> **exploder said:**
> Thanks guts! I added to the bug report as well.
You can also click: "This bug affects you" in the bug report. Than they know I'm not making stuff up ;-)

---

