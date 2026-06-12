---
title: "VNC4 Server Problems"
date: 2008-08-19
forum: Mythbuntu
---

### Post by nasha on 2008-08-19
Hi Guys,
Recently installed virtualbox, and post installation my vnc is no longer working. Im not sure if the two issues are related at all, but i thought its worth mentioning.
The error im getting when trying to connect is "No Password Configured For VNC Auth".
Ive reset the password with vncpasswd, and also removed and reinstalled vnc4server, all to no avail.

Any help would be greatly appreciated!
Regards,
Nasha

---

### Post by superm1 on 2008-08-19
> **nasha said:**
> Hi Guys,
Recently installed virtualbox, and post installation my vnc is no longer working. Im not sure if the two issues are related at all, but i thought its worth mentioning.
The error im getting when trying to connect is "No Password Configured For VNC Auth".
Ive reset the password with vncpasswd, and also removed and reinstalled vnc4server, all to no avail.

Any help would be greatly appreciated!
Regards,
Nasha
Make sure you update /root/.vnc/passwd as that's where the password file is stored.

---

### Post by nasha on 2008-08-19
Update how?

---

### Post by superm1 on 2008-08-20
When you use the vncpasswd command, that is not the default place, but that is where it needs to go for the VNC implementation in mythbuntu.

---

### Post by nasha on 2008-08-20
Both ~/.vnc/passwd & /root/.vnc/passwd have the same file contents.
Were these the default locations you were talking about?

---

### Post by superm1 on 2008-08-20
Yeah that's what i was referring to.  Are you just letting the automatic startup start the VNC, or did you configure something else differently?

---

### Post by nasha on 2008-08-20
Automatic, i never configured anything regarding start up

---

### Post by Chris Musampa on 2008-08-21
I use x11vnc because it does server side scaling which means I don't have to mess about scaling and resizing the client (krdc).

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

---

### Post by nasha on 2008-08-22
That kind of makes the issue more complex than it is...
VNC was working fine, and all of a sudden this issue arose.
Anyone out to offer any help???

---

