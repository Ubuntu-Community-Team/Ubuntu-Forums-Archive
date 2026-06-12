---
title: "Where's my Windows partition ?"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by microfox on 2010-07-14
Hi


I have installed Ubuntu 10.04 on my Windows 7 notebook as a virtual machine with Virtual Box. Almost everything is working fine except I can't see my Windows partition (where my music and videos are located) when I'm in the file manager.

I'm sure this problem has been addressed in the past but I wasn't able to find a solution for my problem.

Can anyone provide some help ?

---

### Post by olamina on 2010-07-15
I am another n00b having the same problem. All I really want to do is import my Firefox bookmarks preferences and my itunes xml file. Can someone please point me towards very simple/ for utter dummies help?

Thanks in advance!

---

### Post by shazbut on 2010-07-15
The ubuntu guest in virtualbox will not see your windows partition, because the virtualbox "hard disk" it resides on is really just a file (in this case stored in your windows filesystem.

What you'll want to do to be able to see your files under the guest system is to set it up as a shared folder under virtualbox.

Go to Devices -> Shared Folders and add the location you need in there.

This should get you started.  I'm not sure how you'd go about accessing the shared folder, I guess maybe Places -> Network under the Ubuntu guest.  My setup is a Windows guest on Ubuntu host, yours is the opposite.

---

### Post by olamina on 2010-07-15
> **shazbut said:**
> The ubuntu guest in virtualbox will not see your windows partition, because the virtualbox "hard disk" it resides on is really just a file (in this case stored in your windows filesystem.

What you'll want to do to be able to see your files under the guest system is to set it up as a shared folder under virtualbox.

Go to Devices -> Shared Folders and add the location you need in there.

This should get you started.  I'm not sure how you'd go about accessing the shared folder, I guess maybe Places -> Network under the Ubuntu guest.  My setup is a Windows guest on Ubuntu host, yours is the opposite.

My Ubuntu is not installed inside Windows, so I don't think I have Virtualbox.

---

### Post by asenine on 2010-07-15
> **olamina said:**
> My Ubuntu is not installed inside Windows, so I don't think I have Virtualbox.

He was talking to OP.

---

### Post by olamina on 2010-07-15
Oh, silly me.

---

### Post by microfox on 2010-07-15
> **shazbut said:**
> The ubuntu guest in virtualbox will not see your windows partition, because the virtualbox "hard disk" it resides on is really just a file (in this case stored in your windows filesystem.

What you'll want to do to be able to see your files under the guest system is to set it up as a shared folder under virtualbox.

Go to Devices -> Shared Folders and add the location you need in there.

This should get you started.  I'm not sure how you'd go about accessing the shared folder, I guess maybe Places -> Network under the Ubuntu guest.  My setup is a Windows guest on Ubuntu host, yours is the opposite.

Thanks for your answer.

I have added the location of my music folder to Virtual Box but once in Ubuntu, I can't find a way to access this folder.

Not if this is the right forum but I also have a problem with an USB key that Virtual Box recognizes but Ubuntu does not.

Maybe someone else knows the answers ?

thanks

---

### Post by shazbut on 2010-07-15
Sorry, forgot to say you will need to install Virtualbox guest additions under the ubuntu guest for the shared folders to work.  Here's a guide I found with a quick search:
[http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/]("http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/")

As for your USB problem you may need to add an empty filter in the machine settings.  Make sure the guest is shut down, then in virtualbox go into settings -> usb, hit the topmost button on the right (add empty filter). This will make the mount any new usb device it sees.  If you only want it to mount specific usb devices the second button with the plus sign is the one you'll need.

---

### Post by microfox on 2010-07-16
> **shazbut said:**
> Sorry, forgot to say you will need to install Virtualbox guest additions under the ubuntu guest for the shared folders to work.  Here's a guide I found with a quick search:
[http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/]("http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/")

As for your USB problem you may need to add an empty filter in the machine settings.  Make sure the guest is shut down, then in virtualbox go into settings -> usb, hit the topmost button on the right (add empty filter). This will make the mount any new usb device it sees.  If you only want it to mount specific usb devices the second button with the plus sign is the one you'll need.

Thanks...I'll give it a try

---

