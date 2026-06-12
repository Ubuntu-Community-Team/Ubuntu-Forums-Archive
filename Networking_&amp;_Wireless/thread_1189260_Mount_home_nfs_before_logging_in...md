---
title: "Mount /home nfs before logging in.."
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by eNRGy on 2009-06-16
Hi all,

Title says it all really - how can I make sure /home/blah (an nfs mount) gets mounted before a machine automatically logs in? The only solution I have so far is to do a timed login to delay it, which is imperfect.

Typical errors the user sees are the standard ".dmrc wrong permissions" and "home folder wrong permissions" dialogs. Having clicked through these, things are usually ok.

Connection is wired and permanent (obviously). I'm running vanilla Jaunty and mounting the share via fstab with default settings. Everything else is standard.

Any help appreciated, tia.

---

### Post by jhannah on 2009-06-17
I'm assuming you have the NFS mount setup in your /etc/fstab file to use defaults or auto in the mount options, correct? That should really do the trick but if not, you might want to look into autofs and automount. It is a little more complicated but the generally accept way to accomplish exactly what it sounds like you want to do- handle all of /home as a NFS share.

After installing the autofs package, you can modify /etc/auto.master to include the below:

```
/home /etc/auto.home
```

Then create the /etc/auto.home file and include something along the lines of the below line:

```
*     -fstype=nfs,soft,intr,tcp     nfs.mydomain.com:/home
```

Lastly, if you continue to have permission issues you might want to check out the anonuid and anongid options for the NFS server. Check out the man page for exports for more info on that.

Hope that helps

---

