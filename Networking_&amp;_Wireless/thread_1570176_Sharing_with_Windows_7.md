---
title: "Sharing with Windows 7"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by Rick Montes on 2010-09-07
I am fairly new to Linux and Ubuntu. I am running a Windows 7 Professional machine and am trying Ubuntu v.10 as a backup.

I have three computers on the Network, my Windows 7, My wifes Laptop Windows XP and the Ubuntu.

In Ubuntu I can see the three computers and the "Workgroup". I can access the XP computer but not the Windows 7. It keeps asking me for a username (rick) domain: WORKGROUP and Password: 

I tried every password imaginable to no avail. I use my Ubuntu admin password and the Samba password that I set up.

Now, I can see the Ubuntu computer and can share files with it through the Windows 7 computer. All I want to do is connect so I can use the printer on the Windows 7 Machine.

I tried every help forum with no luck. It seems like it may be something very simple.

Oh, I even tried my login name for my user account on windows and that did not work.

Please help!

---

### Post by elico on 2010-09-07
couple of steps to make samba and windows 7 work together.

1. uninstall windows live sign in assistant.
2. use samba with encrypted password.
3. allow guest user\map nobody to guest user.
4. use the authentication for samba as for "share" and not "user"

p.m.
if you can post your smb.conf file content it will be helpful.

---

### Post by Rick Montes on 2010-09-07
Thanks, that did it! I knew it was something simple. All I had to do was uninstall live assistant.

Thanks Again for the quick reply.

Rick

---

### Post by elico on 2010-09-08
you welcome.
that was something that bother almost any windows 7 user with a linux maching running samba.

---

### Post by MaindotC on 2010-09-08
Please mark the thread as solved.

---

