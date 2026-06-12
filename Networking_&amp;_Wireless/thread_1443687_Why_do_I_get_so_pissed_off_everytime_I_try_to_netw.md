---
title: "Why do I get so pissed off everytime I try to network my computers."
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by xl_cheese on 2010-03-31
Over the last few years as I've used ubuntu I've attempted to network or remote desktop.  Only do I need to do this a few times a year.  EVERYTIME I try this it doesn't work and I spend hours trying to figure it out.  

Every resource on the web shows how easy it's supposed to be.  Share a folder on one ubuntu machine, share a folder on another ubuntu machine and presto instant networking.  It's never worked like that for me.  

Why is it I can remote desktop to a machine, but not see it in the network folder?

Why is it I can set it up and get it all working and then half a year later I have to go through all the same headaches.  Does upgrading the distro throw everything off?  

From one computer I can see one of my windows laptops, but it gives errors trying to connect.  

This has become a sore spot for me.

---

### Post by pdc on 2010-03-31
Yeah; I hate it when it happens to me too

---

### Post by Schitso on 2010-03-31
If you're using NetBIOS names, do you have winbind installed? Have you tried using zeroconf?

---

### Post by Iowan on 2010-03-31
"Networking" is pretty straightforward - "Sharing" (especially Samba)... not so much. I pretty much understood it back around Gutsy, but it seems to have evolved a bit since then. [Here]("http://ubuntuforums.org/showthread.php?t=1169149") is my favorite Windows-sharing How-To - you've probably already seen it (maybe memorized it ;) )

---

### Post by theozzlives on 2010-03-31
Recently I've tried to access shares using SAMBA from Jaunty up. It's borked up right now. If you type:
```
smb://ipaddress/
```
you can access your shares.

---

### Post by Schitso on 2010-03-31
> **theozzlives said:**
> Recently I've tried to access shares using SAMBA from Jaunty up. It's borked up right now. If you type:
```
smb://ipaddress/
```
you can access your shares.

Try smb://hostname.local/ (if you're trying to access another Ubuntu box)

---

### Post by theozzlives on 2010-03-31
> **Schitso said:**
> Try smb://hostname.local/ (if you're trying to access another Ubuntu box)

Right now SAMBA is not resolving names.

---

### Post by Schitso on 2010-03-31
> **theozzlives said:**
> Right now SAMBA is not resolving names.

Using the smb prefix forces nautilus to resolve hostnames using samba? That's a zeroconf name.

---

### Post by theozzlives on 2010-03-31
> **Schitso said:**
> Using the smb prefix forces nautilus to resolve hostnames using samba? That's a zeroconf name.

I'm torn, the problem is either SAMBA or Nautilus. I can only access shares by ip. Even printers.

---

### Post by Schitso on 2010-03-31
> **theozzlives said:**
> I'm torn, the problem is either SAMBA or Nautilus. I can only access shares by ip. Even printers.

Can you ping it? Perhaps your multicast route isn't set (for zeroconf). There's certainly a large number of variables when it comes to networking. :P

Edit: Hm. Kinda hijacking the thread. Sorreh.

---

### Post by theozzlives on 2010-03-31
> **Schitso said:**
> Can you ping it? Perhaps your multicast route isn't set (for zeroconf). There's certainly a large number of variables when it comes to networking. :P

Edit: Hm. Kinda hijacking the thread. Sorreh.

yeah, I hate it when it happens to me... started out trying to help the OP.

---

