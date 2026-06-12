---
title: "Mount samba share"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by kpgalligan on 2010-03-09
I've been wresting with this on and off for months.  I love linux, but for the past couple days I've wanted to throw my laptop down the stairs.

I have a networked raid drive.  Thecus 2100.  Its running linux, and includes samba sharing.

On that I have a folder shared.

I can connect to and read and write from nautilus.  No problems.  However, I can't use other apps through that method.  Its not really "mounting" that drive in the sense you'd normally think of (afaik).

If I try to mount the folder, no matter how I have tried so far (-t cifs, smbmount, etc), I can navigate the folders, but if I try to read any file I get a permission error.  Looking at the permissions with 'ls -l', everything looks OK.  The weird thing is, I can write a file, then read that file back as long as its the same session.

Just now I tried 'smbclient' with no special arguments.  Just the  server and path url.  It asked for my password.  Once I was in, I had no trouble getting files.

I had a thread about this a while back and there were several links and all sorts of command line options to try, which I did, with no different outcome.  I think its got to be something much simpler and more obvious.  Any thoughts?  smbclient and nautilus seem to have no trouble.  Anybody know what they're doing differently?

Thanks in advance.

-Kevin

---

### Post by suseendran.rengabashyam on 2010-03-11
Hi,

A similar thread,

[http://ubuntuforums.org/showthread.php?t=1409720](http://ubuntuforums.org/showthread.php?t=1409720)

Hope this helps.

---

### Post by dmizer on 2010-03-11
Take a look at the second link in my sig.

---

### Post by kpgalligan on 2010-03-11
I'll take a look at the, but for now I re-threw in the towel.  I'm using NFS.  Insecure?  Probably, but its my home network, so I'll just have to hope nobody is getting into the firewall.

I tell people they should try linux because, for the most part, its pretty good.  However, there is a long list of things that the average person will be lost on when they get into trouble.  Generally, if you know what you're doing, it doesn't take long to dig yourself out.  However, most people don't know what they're doing.

This issue, however, is in that much shorter list of things that even if you pretty much know what you're doing, it doesn't matter.  It should be pretty easy, but I've spent several hours trying to sort it out, and daydreamed about taking a hammer to all my networking equipment more than once.

Rant over.  I'll give it a look and see if any of this sorts out the issue.

---

### Post by dmizer on 2010-03-11
Frankly, I don't know of many "average" people who would even know what "file sharing" is, let alone want to do it cross platform between Ubuntu and Windows.

> **kpgalligan said:**
> I'm using NFS.

That's what I do. It works better than Samba, just as secure as Samba, faster than Samba, and needs far less attention. It's also designed to work correctly on the Linux platform.

---

### Post by kpgalligan on 2010-03-11
> **dmizer said:**
> Frankly, I don't know of many "average" people who would even know what "file sharing" is...

A good many of them don't know what a "file" is.

---

