---
title: "How to change samba's user password from Windows 7"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by Casimiro on 2010-10-01
Hi guys!

I've been searching the awnser for this question for a while but I could not find it, and I hope somebody knows it.

It's seems a simple problem:

I have a Samba installed and configured on a Ubuntu Server 10.04 box, as a file server, **not as an PDC**. And I have several Windows 7 machines accessing the Ubuntu Server to store files.

I would like to let users to change their passwords from windows.

Is that possible ???

I'm sorry if this question has already been awnsered, but I could not find it.

Regards!

---

### Post by sikander3786 on 2010-10-01
I doubt if it can be changed at the workgroup level. You need a domain controller for that.

---

### Post by Casimiro on 2010-10-02
> **sikander3786 said:**
> I doubt if it can be changed at the workgroup level. You need a domain controller for that.
sikander3786 thank you!
I think I'm gonna setup a PDC then...

---

