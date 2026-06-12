---
title: "Remote Access Utilities for Ubuntu?"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by Justinlinux on 2009-12-02
I was just wondering if there are any Remote Access Utilities for Ubuntu Linux other than the utility included with Ubuntu. I have a great knowledge of computers, but I still seemed to think that Windows Live Mesh would work on Linux. (What was I thinking???) Anyway, I have not yet succeeded in finding a working remote desktop solution that is free for linux, and I was just wondering if the community had any knowledge of such a product. I would like to be able to have the ability to see my graphical desktop from another computer, however it would be ok if I could only access my filesystem without a display of my graphical desktop. Any ideas?

---

### Post by teward on 2009-12-02
I've got an idea.

Perhaps you should use SSH.

```
sudo apt-get install openssh-client
```

Then you connect to your IP address. SSH gives you direct access to your system through the terminal.  However, you need to know how to copy files to your computer.  This doesn't work well with Windows filesystems, though, but by using SSH through this method, you can then use SFTP to access your files and save them to your Windows hard drive with an FTP client.

If you have any questions with openssh, please ask.  I've already custom-configured my install, so if I can be of help I will help you as much as I can.

---

