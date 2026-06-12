---
title: "K3B: Please insert an empty or appendable medium"
date: 2013-01-02
forum: Multimedia Software
---

### Post by bkorb on 2013-01-02
Obviously, I have an empty medium in my drive.  K3B is trying to tell me that something is wrong, but it won't say what the problem is.  "I cannot write to it" seems unlikely since I went to a lot of trouble to ensure all the /dev/cd* and /dev/dvd* devices are world writable.  So what is the message really trying to say?  Thank you!

P.S. I tried running as root:

> unnamed app(4159): KUniqueApplication: Cannot find the D-Bus session server:  "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." 

unnamed app(4158): KUniqueApplication: Pipe closed unexpectedly.

---

### Post by bkorb on 2013-01-02
Please _insert an empty or appendable medium_**find the real device file (not the symlink) and ensure *it* has write permissions**

Sigh.  If there are any K3B developers out there, please consider improving the message.  Helpful error messages are real time savers.  Thank you.

Some update must have "fixed" the device permissions.

---

