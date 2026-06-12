---
title: "file sharing between Ubuntu and OS X (Leopard)"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by jmelton on 2009-12-31
It was pretty easy for me to figure out how to make my laptop running OS X visible to my netbook (which runs Ubuntu 9.1).  All you have to do is go to System Preferences, open up Sharing, and check the File Sharing box.  But is there an equally easy way to make my Linux files visible on the Mac?  I'm pretty clueless about the latter.  Thanks!

---

### Post by howefield on 2009-12-31
Try right clicking the folder you want to share and select the sharing option. Follow any prompts you get, which will probably mean installing a few packages.

There is also a useful package you can use if you want a graphical method to share your folders. Install with Synaptic Package Manager.

```
system-config-samba
```

---

### Post by jmelton on 2009-12-31
> **jmelton said:**
> It was pretty easy for me to figure out how to make my laptop running OS X visible to my netbook (which runs Ubuntu 9.1).  All you have to do is go to System Preferences, open up Sharing, and check the File Sharing box.  But is there an equally easy way to make my Linux files visible on the Mac?  I'm pretty clueless about the latter.  Thanks!

Actually, even though "Melton's MacBook" shows up in the File Browser window, when I try to click on it it doesn't actually connect, so there's a problem with file sharing from OS X to Linux as well.

---

### Post by jmelton on 2009-12-31
> **howefield said:**
> Try right clicking the folder you want to share and select the sharing option. Follow any prompts you get, which will probably mean installing a few packages.

There is also a useful package you can use if you want a graphical method to share your folders. Install with Synaptic Package Manager.

```
system-config-samba
```

Thanks for the info.  For some reason I tried right-clicking before and it wasn't showing the sharing option.  But now when I do and try to share the folder, I get the message "Failed to execute child process "testparm" (No such file or directory)".  The packages I was prompted to install were all successfully installed and it looks like just about everything having to do with Samba was installed already, so I'm not sure what's missing.  I'm also getting the error message "You do not have permission to execute /usr/bin/pdbedit" if I try to run system-config-samba, even though there's execute permission at all three levels for that file.

---

### Post by jmelton on 2010-01-04
So, I'm stuck for the moment.  My Mac shows up in the File Manager in Ubuntu but says that it contains zero bytes and nothing happens when I click on the icon.  Trying to set up & run Samba resulted in the error messages below, so I'm still unable to see my Ubuntu files from the Mac, either.  Anyone have any ideas?  I've got an external hard drive, so I can share files indirectly, but it would be nice to be able to just connect the two computers directly and it seems like it should be a simple thing to do in both directions.


> **jmelton said:**
> Thanks for the info.  For some reason I tried right-clicking before and it wasn't showing the sharing option.  But now when I do and try to share the folder, I get the message "Failed to execute child process "testparm" (No such file or directory)".  The packages I was prompted to install were all successfully installed and it looks like just about everything having to do with Samba was installed already, so I'm not sure what's missing.  I'm also getting the error message "You do not have permission to execute /usr/bin/pdbedit" if I try to run system-config-samba, even though there's execute permission at all three levels for that file.

---

### Post by jaknap on 2010-08-27
[http://pankajdangi.com/2010/08/samba-sharing-is-not-working-in-9-10/](http://pankajdangi.com/2010/08/samba-sharing-is-not-working-in-9-10/)

---

