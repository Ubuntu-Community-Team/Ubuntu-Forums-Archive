---
title: "General Samba Question."
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-05-08
I run Samba at home. The computers are in the workgroup called "WORKGROUP." 

When the a computer is rebooted, unless I specifically check "remember password", it prompts the user to re-login at the start - run - \\sambaserver screen from the Windows XP computer.

Now, I use Samba for backup purposes. So I save the passwords that 1 time and the automated Windows software I use backs up their computers to the UNC path (\\myserver\theirshare\documents) at designated times.

Question is this. I'm at work now. It's a windows network. When I go to start - run \\mainstorageserver automatically I can just log in because we're on a domain.

I'm not trying to do this, I'm simply questioning if it's possible to have Samba auto-login the users based on their domain log on name.

Is that possible?

---

### Post by superprash2003 on 2009-05-09
i dont think that is possible..getting samba to provide a path to share files between the two operating systems itself is a big thing.. hopefully something like that would come out soon..

---

### Post by dandnsmith on 2009-05-09
I've done it the past with SAMBA, but, having updated both Windows version and linux, I now find I'm missing something.

Last time I had the problem, it turned out to be some linux security which I didn't know I had.

The sort of thing you're looking at is defining use of shares by user, and defining (SAMBA) users to be the equivalent of Windows users. If I say too much, it will lead you to the position I'm currently in (ie not working), but I'm sure it can be done.

---

### Post by glennyboy on 2009-05-09
how can i map network drive on ubuntu with a specific letter drive like on windows?

ex. S:\\server\share\

thanks in advance!!!

---

### Post by dandnsmith on 2009-05-09
You're trying to use a Windows concept for mounting, whereas linux doesn't care about 'drives', only about the file hierarchy (which it treats in a unified fashion).

You have to think in terms of a mount point and what is mounted.
So you might define /winshare2
and mount the windows share there for use:

mount -t cifs //workgroupname/servername/sharename /winshare2

---

### Post by Roasted on 2009-05-09
So ultimately, there's no known way to have the user shares/permissions/files to be defined by the log on name?

That IS kind of nice... having a Windows server set up which works with the username logged into the XP computer from another location. That way when a user logs into the workstation, no additional logging in is required.

Plus, think about it like this. If the My Documents share is re-linked to a Windows server, you just click My Documents and magically your stuff is there. But what if you link it to a Samba share? Do you have to log in to get to your documents?

---

### Post by capscrew on 2009-05-09
> **Roasted said:**
> ...

Question is this. I'm at work now. It's a windows network. When I go to start - run \\mainstorageserver automatically I can just log in because we're on a domain.

I'm not trying to do this, I'm simply questioning if it's possible to have Samba auto-login the users based on their domain log on name.

Is that possible?

Samba can't provide the services. It is not just a matter of login name and password. The reason Windows AD is able to is due to the use of Kerbros tickets.  The Kerbros ticket is the domain wide authorization for all services.  The ticket is also used with GPO's (Group Policy Objects).  Linux does have ACL's for file/folder permissions.

---

### Post by Roasted on 2009-05-10
Well, in my mind personally it would make sense to have a Linux storage server. That way you have a mixture of platforms, so if a virus hits the Windows clients and their documents are linked to the Linux storage server, your storage server more than likely wouldn't be effected.

It just kind of sucks to know that this wouldn't be a VERY similar alternative.

---

### Post by capscrew on 2009-05-10
> **Roasted said:**
> Well, in my mind personally it would make sense to have a Linux storage server. That way you have a mixture of platforms, so if a virus hits the Windows clients and their documents are linked to the Linux storage server, your storage server more than likely wouldn't be effected.

It just kind of sucks to know that this wouldn't be a VERY similar alternative.

I agree that having a Linux NAS is a good idea.  I don't think it would help combating virus attacking the Windows clients.  

It's not a mater of where you store your files.  It does mater were they act upon your system.  Storage on Samba or more specifically mounting a CIFS filesystem from a Linux host to your windows clinets won't stop a virus from d/l'd word doc's or virus infected email.

On the other hand I have both permanently mounted CIFS filesystems and filesystems that are mounted by browsing.  I have also have file system dedicated to backups of my windows hosts.  I need no passwords (the keyring handles that) and It is limited to my login only.  It is an external SATA HDD that is mounted at /smb/backup.

---

### Post by Roasted on 2009-05-10
> **capscrew said:**
> I agree that having a Linux NAS is a good idea.  I don't think it would help combating virus attacking the Windows clients.  

It's not a mater of where you store your files.  It does mater were they act upon your system.  Storage on Samba or more specifically mounting a CIFS filesystem from a Linux host to your windows clinets won't stop a virus from d/l'd word doc's or virus infected email.

On the other hand I have both permanently mounted CIFS filesystems and filesystems that are mounted by browsing.  I have also have file system dedicated to backups of my windows hosts.  I need no passwords (the keyring handles that) and It is limited to my login only.  It is an external SATA HDD that is mounted at /smb/backup.

I didn't say it would prevent viruses. I meant it would help from virus spread.

If the core storage server is Linux based and the network is hit by a Windows virus, at least the core data is more than likely going to be okay - even if the data might have viruses and such tagged in it, at least it wouldn't cause the storage server to format c:/ or anything.

---

