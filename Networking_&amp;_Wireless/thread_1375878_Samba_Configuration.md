---
title: "Samba Configuration"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by michillin212 on 2010-01-08
Hello, I was once again trying to set-up file and printer sharing but tripped over the same stone.  In all the help forums, videos, archives, etc.  My smb.conf file is different mine is different every file in the /etc/samba/ folder is blank.  The file (as i understand it is supposed to say something about global parameters) has nothing in it so i assume this is why it is not working.  On my laptop which i am trying to share files with won't recognise my computer or printer any more which it used to.  Could someone please post where I could get the missing file or what I need to but in the file.  That would be great!

---

### Post by SecretCode on 2010-01-08
That's odd. Have you installed the packages samba (on the server) and smbclient (on client and server)?

See if you have a copy at /usr/share/samba/smb.conf

Here are some links to documentation: [Samba Documentation](http://samba.org/samba/docs/) - [Configuring Samba (smb.conf)](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2551976)

- But I can't find a copy of the default smb.conf there.

---

### Post by michillin212 on 2010-01-09
Thank you for the help but Samba was fine.  Norton Internet Security wasn't allowing my share.  I let it through and now it works!  I know it wasn't samba's fault!

---

