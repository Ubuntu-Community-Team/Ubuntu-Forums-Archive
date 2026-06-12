---
title: "connecting 8.10 desktop to 8.10 server"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by jtb74129 on 2008-12-13
I am a noob here and to Linux so please bare with me.  I have searched the forums for my problem, but nothing matched my basic problem.  I have setup my laptop with Unbuntu 8.10 and a Home Server with Server 8.10.  Both are connected using a Belkin wireless router (server is wired, laptop wireless).  Both can access the internet and both show each other on the "network".  My problem is accessing one with the other.  I want to xfer a file to the server from the laptop and it gives me errors:

"Operation not supported by backend" when trying to create a file or move a file to the server.

I am used to a windows network environment, not command line.  If there is a way to use GUI to complete the network connections and give permissions in all the right place, I would be greatful?  I think I have downloaded every app known or hads been mentioned, but since I am new, I wouldn't know what to do with them.

I can give you more info, just not sure what to give...

Thanks in advance...Jeff:confused:

---

### Post by jpkotta on 2008-12-13
A quick and easy solution is sshfs.
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

Of course, Samba is a better long term solution, but I'm assuming you've tried that and got frustrated.

---

### Post by jtb74129 on 2009-01-02
> **jpkotta said:**
> A quick and easy solution is sshfs.
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

Of course, Samba is a better long term solution, but I'm assuming you've tried that and got frustrated.

I loaded Samba on my server so that my wife could connect, but I have not been able to do anything from my linux box.  Go figure.  Not having any understanding of how linux file structure is setup makes it hard.  I posted a new thread for help on understanding Ubuntu's file structure compared to Windows.  If I can have a reference point to windows then I should be able to figure things out.

I appreciate you help greatly...

---

