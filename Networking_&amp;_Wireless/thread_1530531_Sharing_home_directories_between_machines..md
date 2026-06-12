---
title: "Sharing home directories between machines."
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by DracoJesi on 2010-07-13
I want to share home directories from two different machines so that I can log on to both using the same account.

One idea was to host the home directory on a server and mount it to a local directory. I don't think this will work though, because I'm pretty sure the directory wont be mounted until the logon session starts and I'm guessing it wont without the appropriate home directory.

So the question becomes, what tells the OS where the home directory is in the first place. Yes it's in a default place but that path as to be stored in some config file somewhere right?

But another problem is... If the server goes down, I'll have to make sure I can log on via root at the logon screen/get into a terminal/use LiveCD to get access.

It wouldn't be too much of a problem to create an account on each machine, all my media will be on the server anyway. But if I create an account on one, it would be nice if it was automatically added to the other. And it would be great for keeping settings if I want to do a compete wipe if I'm upgrading the file-system or something. I suppose I could just do a backup like everyone else....

So I'm guessing some kind of syncing, except that doesn't do auto-account creation.... 

Suggestions? I don't mind a little work.

---

### Post by capscrew on 2010-07-13
> **DracoJesi said:**
> I want to share home directories from two different machines so that I can log on to both using the same account.

One idea was to host the home directory on a server and mount it to a local directory. I don't think this will work though, because I'm pretty sure the directory wont be mounted until the logon session starts and I'm guessing it wont without the appropriate home directory.

So the question becomes, what tells the OS where the home directory is in the first place. Yes it's in a default place but that path as to be stored in some config file somewhere right?

But another problem is... If the server goes down, I'll have to make sure I can log on via root at the logon screen/get into a terminal/use LiveCD to get access.

It wouldn't be too much of a problem to create an account on each machine, all my media will be on the server anyway. But if I create an account on one, it would be nice if it was automatically added to the other. And it would be great for keeping settings if I want to do a compete wipe if I'm upgrading the file-system or something. I suppose I could just do a backup like everyone else....

So I'm guessing some kind of syncing, except that doesn't do auto-account creation.... 

Suggestions? I don't mind a little work.

Wha you want to use is NFS.  Your situation is exactly why it was developed by SUN many years ago.  See [**_here _**]("http://blog.agdunn.net/?p=33") and [**_here _**]("http://harrykar.blogspot.com/2010/04/ubuntu-setting-up-nfs-server.html")for a start.  This will give you ideas.  If you have more questions post them here.

---

