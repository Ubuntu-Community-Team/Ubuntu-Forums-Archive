---
title: "How do I create a home network with Ubuntu?"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by LiamWilson on 2009-03-26
I've just bought a Buffalo wireless router, and I would like to create a home network, so I can share files with another PC, running Windows XP. Is this possible, and how can I go about setting this up, can anyone point me to a HowTo or something similar?

Thanks in advance;

LiamWilson

---

### Post by 505 on 2009-03-26
If the other PC is running Windows, it is best to set up Samba on your Linux computer. This allows you to access shared folder on Windows, and you can share folders on the Linux computer which can be accessed by Windows. There is [good documentation](https://help.ubuntu.com/community/SettingUpSamba) on how to set up Samba.

---

### Post by stchman on 2009-03-26
> **LiamWilson said:**
> I've just bought a Buffalo wireless router, and I would like to create a home network, so I can share files with another PC, running Windows XP. Is this possible, and how can I go about setting this up, can anyone point me to a HowTo or something similar?

Thanks in advance;

LiamWilson

My thing is that Ubuntu has a difficult time connecting to an SMB share like the one Windows creates.  Also setting up Samba is a real PITA IMO.  You can setup a Samba share on your Ubuntu PC and the Windows PC will see it easily.

I have 4 PCs on a home network using Linux's NFS protocol.  That was easy.

---

### Post by LiamWilson on 2009-03-26
Thanks, I'll look into it.

Edit:// If I want to access files from both PC's, but only want to print files to the printer connected to the XP Computer, which package do I install, Samba, or smbfs? (The Ubuntu Laptop, is that The server or the client?)

And Do I hav e to install either on the Windows PC?

---

### Post by Iowan on 2009-03-26
The machine that provides the files (printer) is the server, the client is the machine that receives the files. So, if the laptop is sharing files TO XP, it is the server... if/when it gets files FROM XP, it is the client.
The Setting up Samba link is already posted, [Here]("http://samba.netfirms.com/") is another to consider.

---

