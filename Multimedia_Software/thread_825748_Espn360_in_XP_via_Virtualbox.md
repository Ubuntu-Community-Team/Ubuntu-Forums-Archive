---
title: "Espn360 in XP via Virtualbox"
date: 2008-06-11
forum: Multimedia Software
---

### Post by muadnu on 2008-06-11
I'm trying to get video streaming on espn360.com in my XP copy on Virtualbox. The video player starts, but then it gets stuck at loading...

I have tried this using the Windows version of Firefox via Wine and I do get the video, but is sometimes choppy, and it sometimes crashes, so I'd like to be able to get it working in Virtualbox. I don't know whether using host interface networking instead of NAT might help.

Any ideas?

---

### Post by wolfen69 on 2008-06-11
did you give the virtual machine enough video memory?

---

### Post by muadnu on 2008-06-11
Yes, I guess... I tried with 64 Mb.

---

### Post by georgia_tech_swagger on 2009-11-11
ESPN360 now works in VirtualBox.

Details on my setup:
- VirtualBox Personal Use Edition (not OSE) 3.0.10
- Windows XP guest OS
- DirectX enabled in VirtualBox
- VirtualBox Guest Additions installed in guest OS (3.0.10 ... with experimental DirectX enabled)
- Very latest Move player from ESPN360 in guest OS
- Arch Linux, all the latest packages

---

