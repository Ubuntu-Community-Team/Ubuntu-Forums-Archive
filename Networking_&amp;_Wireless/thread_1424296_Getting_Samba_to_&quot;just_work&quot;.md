---
title: "Getting Samba to &quot;just work&quot;"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by imgod22222 on 2010-03-07
In Windows, I'm used to just anyone being able to access my Network Places, and I just deny read/write access by allowing users to change my files.

In Samba, I don't want to have users, I don't want prompts coming up asking for credentials. I just want to be able to share some folders allowing only list/read permissions, and other folders allowing read/write/insert/delete permissions.

So I'm guessing the way I want to do this in linux-talk is:
Create a user
Give them access to folders x y and z
chmod folder x, y, and z appropriately
Give them no user name and chroot them to some folder, and create symlinks to the folders I want them in.

But the question is... *[I]how*[/I]?

Possibly making the samba server look as a UPnP device (since it can find my router as one, strangely enough)

EDIT: Super-weird. So I uninstalled Samba and reinstalled it using the software centre, and when I looked to see if I can run samba via command line, it said it wasn't installed. So I'm apt-get installing samba4 now.

---

### Post by Iowan on 2010-03-07
Setting **security=share** may give part of your goal - but there may be better ways.

---

### Post by netopalis45 on 2010-03-07
i am actually doing a very similar thing. i used to have a shared folder using samba on my Ubuntu machine and could access it from any other computer on my network (all the others use Vista) with no problem at all. then i had to reinstall Ubuntu. after that everything went south. i need to be able to share this folder. what am i doing differently and what do i need to do to fix this?

---

### Post by jonandrews on 2010-03-08
I have put some step-by-step illustrated guides on networking in a mixed Ubuntu / Windows network on my website:
[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

There should help you set up what you're looking for....

---

