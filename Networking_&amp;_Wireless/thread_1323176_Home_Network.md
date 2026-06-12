---
title: "Home Network"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Doug_in_Maine on 2009-11-11
I have a Home Network with the following:

1.  Apple Airport Router
2. Windows XP Desktop - Wired to router
3. Windows 7 Desktop - Wired to router
4. MacBook    OS 10.6 Wireless to router
5.  Ubuntu 9.04 Laptop

I can share files between the Windows computers, but neither of them can see the Ubuntu computer.

Should they be able to see the Ubuntu computer or should it be able to see any of the other computers?

If this is not possible, then what good is it for me to have a Linux computer other than as a stand-alone?

---

### Post by dandnsmith on 2009-11-11
It's possible, and SAMBA was developed to offer a way of doing it.
You might find what you want in the links in [this posting](http://www.backports.ubuntuforums.org/showpost.php?p=7157868&postcount=12).

---

### Post by honestguvnor on 2009-11-11
> Should they be able to see the Ubuntu computer or should it be able to see any of the other 
> computers?

It depends what you mean by see.

As mentioned by the previous poster, Samba can be used to do things the proprietary Microsoft way on the Linux computer but you will end up limited by the way Microsoft goes about things.

The alternative is to install the open standard stuff on Windows by installing programs like winscp and friends. This is a much more flexible approach because now you Windows computers will be able to communicate with all other computers and not just Windows ones and all other computers will be able to communicate with your Windows computers.

---

### Post by coffeecat on 2009-11-11
Have you set up a share in the Ubuntu machine? If you haven't it's not surprising that the Windows machines can't see it. Create a folder for sharing in your home folder, right-click on it, select 'Sharing Options' and follow the prompts. If the system needs to download and install parts of samba, log out and in again and start over and once the folder is set up as a share, the Windows machines will see the share.

> **Doug_in_Maine said:**
> If this is not possible, then what good is it for me to have a Linux computer other than as a stand-alone?

Hmmm. That's a very negative attitude. Your choice, but you'll defeat yourself in all your endeavours if you think like that.

---

