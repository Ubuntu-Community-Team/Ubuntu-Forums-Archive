---
title: "Browsing Samba Shares in PCManFM ---&gt; Empty"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by rekado on 2009-01-07
Hi,
I'm running Arch Linux on a notebook and want to connect to a server running FreeBSD. In the LAN there are only Windows PCs which all have access to the shared directories on the server. I may not change anything in the FreeBSD setup, and I think this is not necessary as the Windows PCs can all access the shares.

I've just installed samba on my notebook and can connect to the shares with *smbclient* from the terminal. I specify the very same user name and password that the Windows PCs use to access the server's files. This all works. I only had to change the workgroup name in the smb.conf file.

I'm running the smbnetfs daemon on startup (listed in the DAEMONS vector in /etc/rc.conf <---- I just love that in Arch it is all configurable from here!) which automatically mounts the shares to /mnt/smbnet/.

In PCManFM (as well as in Thunar) I can browse to the shared directories but cannot open them. In PCManFM I just see no contents, Thunar tells me that I don't have permissions to access the directories.
That's understandable from my point of view, because using *smbclient* I have to specify user name and password, but neither Thunar nor PCManFM ask me for that. I'm sure I have to specify user name and password in some configuration file of samba, but I don't know where.

I've read the installation HOWTOs in the PDF file available from the samba page but could not find any more information.

Could somebody help me please?

---

### Post by rekado on 2009-01-14
This was simple: the daemon script /etc/rc.d/smbnetfs was moving error messages to /dev/null. By removing the piping to /dev/null in the script (after making a backup) I could see the error and the suggestion:

```
sudo chmod 600 /etc/smbnetfs/.smb/smbnetfs.conf
```
(not so sure about the path)

This worked!

---

### Post by Iowan on 2009-01-14
Congrats!!!  Problem fixed? Mark the thread [SOLVED] under Thread Tools.

---

### Post by rekado on 2009-01-14
I tried to do so several times, but there was a problem with the server for quite a while. Will try it again now.

Edit:
I still get a database error when I try to edit the title and submit. :(

---

### Post by ethanay on 2012-10-11
for the record, you need to use the THREAD TOOLS menu in the upper right corner to mark it as [solved] instead of editing the title.

---

### Post by wildmanne39 on 2012-10-11
Old thread! closed.

---

