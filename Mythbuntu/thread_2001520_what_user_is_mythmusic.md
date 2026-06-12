---
title: "what user is mythmusic"
date: 2012-06-11
forum: Mythbuntu
---

### Post by drjenk on 2012-06-11
Hi,
When ripping cd's to mp3's located on a NAS, what "user" is trying to write?  Is it user "mythtv", or is it the user that logged in when mounting the NAS?  I have a user different than mythtv defined to log in in /etc/fstab.

I ask because I'm trying to resolve permission errors when ripping cds from mythmusic to a NAS (freenas).  It creates the directory, but then errors with a permission message.  I've tried changing the owner of the NAS filesystem, changing umask settings on both the NAS and mythtv etc.  I see umask as being 0 now on each.  Weird thing is when I telnet into my mythbox with the same username defined in /etc/fstab, and navigate to my NAS in /mnt, and do a mkdir, I do not have priviledge issues.  This has been driving me a bit nuts as I've been wanting to re-encode my cd collection.  
Thanks for any insight.
David Jenkinson

---

### Post by nickrout on 2012-06-11
I am pretty sure that the user who runs mythfrontend will be the one who you are looking for.

On mythbuntu this is the user you created during installation. For me it's nick. To be definitive ```
ps aux|grep mythfrontend
```

---

### Post by drjenk on 2012-06-12
For me it's "david".  That is indeed the user that shows when I run the  command you suggested.  This is also the user I have logging in to the  NAS when mounting in fstab also.  
I just did an experiment, I  changed the music filter to the default /var/lib/mythtv/music, and  ripped a cd.  Even though my umask is 0000 (temporarily), when  mythtmusic creates the music directory, the permissions are drwxr-xr-x.   I want it to be 777.  When I do a "umask", I do get 0000.  Why are the  permissions not 777?  I think if I could figure this out it might solve  my problem?  Any ideas?

Thanks

---

### Post by nickrout on 2012-06-12
Is the nas being mounted as cifs or nfs? I am giessing cifs as most are designed for windows.

if cifs I think the mount point BEFORE you mount the nas need to have the right (write) permissions). So unmount the nas, check ownership and permissions of the mount point, adjust and re-mount.

---

### Post by drjenk on 2012-06-13
I did do that, but it didn't seem to help.  But, I did fix it.  I noticed on the NAS the uid for "david" was 1001, and on mythtv it was "1000".  I changed the uid on the NAS to 1000.  However, this didn't help right away either.  I also noticed the user was "1001" on all the directories still on the NAS.  I did a chown -R to "david" on the entire directory, also changed the group to the same group I have "david" belonging to on mythtv.  I can now rip directly to the NAS.  So I'm not sure which of the two things above, or a combination of both, did it but it's fixed.  Thanks for the helpful comments.
David J.

---

### Post by tgm4883 on 2012-06-13
> **drjenk said:**
> I did do that, but it didn't seem to help.  But, I did fix it.  I noticed on the NAS the uid for "david" was 1001, and on mythtv it was "1000".  I changed the uid on the NAS to 1000.  However, this didn't help right away either.  I also noticed the user was "1001" on all the directories still on the NAS.  I did a chown -R to "david" on the entire directory, also changed the group to the same group I have "david" belonging to on mythtv.  I can now rip directly to the NAS.  So I'm not sure which of the two things above, or a combination of both, did it but it's fixed.  Thanks for the helpful comments.
David J.

Both fixed it. With NFS, the UID needs to match for users across systems.

---

