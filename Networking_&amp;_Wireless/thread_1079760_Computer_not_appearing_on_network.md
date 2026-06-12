---
title: "Computer not appearing on network"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by sms0611 on 2009-02-24
I have just installed 8.04 onto a PowerMac G4.

I have a wired internet connection (via a router) which works fine.

I have 3 PC's running windows XP

From the Mac I can access the 3 PC's and their peripherals

I cannot access the Mac from any of the PC's (it does not appear in the list of computers when I do a map network drives)

I have changed /etc/samba/smb.conf so that the workgroup is correct

Any Suggestions?

---

### Post by Iowan on 2009-02-24
Have you installed Samba? (I refer to it as  Samba-server... Samba-client comes pre-installed - that's why you can access the PC's)

---

### Post by sms0611 on 2009-02-25
Oops.

OK done that now. Followed the advice in this link

[http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/)

Does not appear to be entirely correct.

I can now see the Mac from the Windows machines but I cannot see any shared directories

I have changed the group permissions to sambashare on the documents directory for a test. But no joy

Any Ideas?

---

### Post by Iowan on 2009-02-25
Are you getting error messages (access denied), or are shares just not visible?  If the shares aren't showing, it may be configuration.  I'm used to editing /etc/samba/smb.conf, but the shares **might** be defined in /var/lib/samba/usershares.

---

### Post by jimmyhacker on 2009-02-25
i think samba doesn`t work with macs.

---

### Post by sms0611 on 2009-03-01
Thanks for the help guys, it was indeed a lack of definition in usershares.

Job done.

---

