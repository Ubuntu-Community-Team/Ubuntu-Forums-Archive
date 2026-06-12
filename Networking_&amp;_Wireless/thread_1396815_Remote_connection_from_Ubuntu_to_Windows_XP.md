---
title: "Remote connection from Ubuntu to Windows XP"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by firemedic624 on 2010-02-02
I am new to the remote desktop connection scene so please be bear with me.  I have a Windows XP Professional desktop that I would like to remote connect to from my Ubuntu 9.10 laptop.  I would like to connect in such a way that the current user of the XP machine doesn't get logged off when I connect.  I have googled this subject and have been unable to find this exact subject.  I am fairly comfortable using the terminal although I am still learning it.  I have heard FreeNX is a good program but from what I can tell it's only used to connect from Windows to Ubuntu.  Is this correct?  I would also like to remote connect from the above mentioned laptop to the XP machine while at work over the internet if that's possible.  Thank you in advance for your help.

---

### Post by johnson.d on 2010-02-03
FreeNX is a tool you would install on Linux systems so that you can connect to them from a remote client. Please see [http://freenx.berlios.de/](http://freenx.berlios.de/) for more details.

Windows XP does not allow more than one simultaneous logins. This causes RDP to terminate a session when an RDP session is opened.

If reusing an existing windows session suits you, you can probably install realvnc free edition from [http://www.realvnc.com/](http://www.realvnc.com/) to remote connect to your XP machine.

---

