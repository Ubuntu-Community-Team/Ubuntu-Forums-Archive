---
title: "Can't copy to samba share"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by lingenfr on 2009-11-07
Since upgrading to Karmic I can't copy files/folders from any of my workstations (laptops/desktops) to my NASLite-SMBG v1.4 file server. I get the error "Error while copying, Invalid argument". When I am copying a folder of mp3 files, it typical creates the folder which is artist name and then creates the first files which is usually in the form "album name - NN - track title.mp3". I have at least 4 machines that have been upgraded and all of them do this. Is there a fix? I see a bug about long names which may be my problem. 

I have done some further tests. I have been able to copy files from a another remote samba share to the NASLite box. Same folders, same file. I copy them to a samba share on my Mythbuntu box (KK 9.10) and then copy them to the NASLite box and it works. BTW, 

I did find one unique problem when copying from my desktop to the samba share (Mythbuntu box). It throws an error "Invalid argument" when copying a file whose name includes a '?'.

I've also found that when I open a server with shares using nautilus, I frequently get a blank window and have to do a refresh to get a listing of folders.

I am using Nautilus to browse/cut/copy/paste. Any assistance is appreciated. I attached a capture of the error.

---

### Post by grumpthehermit on 2009-12-19
I am having a similar problem

I have an external 1TB drive with my music on it, I am trying to copy from my desktop PC downstairs back to the 1TB drive on a samba share and get a invalid argument error.

Similar to you I believe that the file names are a problem, Rhythmbox allows the use of & symbols in the track names and artists fields and I think that this is my problem.

The fun thing next will be trying to see if I can re-name files in bulk with the & to and or similar ?

Does anyone know how to stop the error or how to bulk re-name files with invalid characters ?

Thanks
Simon

---

### Post by lingenfr on 2010-01-18
Still having the problem. Any assistance is appreciated.

---

### Post by lingenfr on 2010-06-03
Still having this problem in Lucid. Any ideas?

---

### Post by asqn34 on 2010-06-03
Probably a file permission problems but also check your router setting and your smb.conf.

have a look there for windows/linux networking:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

Ps: you have a lot of patience

---

### Post by lingenfr on 2010-06-05
Maybe. It worked fine prior to Karmic. I think it has something to do with samba/smbfs/cifs changes that were not properly tested. I will see if there are any answers in the links you provided. I believe that I had already tried one, but the other is new. Thanks.

---

### Post by 1John on 2010-09-01
I am having the same problem with the same error messages using Samba shares on a NAS drive on my local network. Previously I had no problems

I have found that copying files fails with the error you describe. But now  I have now found a new document created in open office can be saved to the same windows share without any problems. I have no idea why copying a document gives the error. 

These errors began after upgrading to to Lucid.

Did you manage to resolve your problem?

---

### Post by lingenfr on 2010-09-06
No. I tried the suggestions, but no joy.

---

### Post by xdavio on 2010-11-05
I'm on a 32-bit Ubuntu 10.10 machine and am having the exact same problem.

What's interesting is that in my case the upgrade to 10.10 doesn't appear to be directly responsible... that is, I was able to copy files to the smb after the upgrade to 10.10, but yesterday I began seeing the error referenced in the first post on this thread.

---

### Post by wokandabirder on 2010-11-10
I'm having the exact same problem on 32bit 10.10 trying to copy any file to an SMB mount from a windows server. only the first 64kb of a file will copy, then the error shows up. I can copy files from the server to the local machine just fine.

I don't have problems copying files to the server from my mac (snowleopard) so I don't think it's an issue with the server. This cropped up after upgrading to 10.10. 

Any ideas much appreciated!

---

### Post by SonicSteve on 2010-11-13
Identical problem here,
I'm running 32bit,

No problems using 10.04, upgrade to 10.10 and suddenly copying files doesn't work. I can access the shares, read, and copy from the shares, but if I try to write the shares it bombs with the "invalid argument" message. 

I hope someone finds a fix or first change I get I'm going back to 10.04

I can say this much, my home computer running 10.10 can copy to a windows xp home share without problems. What kind of windows machine are you all trying to copy to? Is it regular windows client (xp vista, and 7) or server?

---

### Post by wokandabirder on 2010-11-14
I'm trying to copy to a win server. This one really is posing a problem for me. I can't find any broken packages on my system that would lead to this.

---

### Post by owise1 on 2010-11-14
what are the properties of the samba share directory you want to copy to?

Mine are as follows
david@HomePC:~> ls-l /mnt/net_store/
total 0
drwxrwsrwx   2 david users 0 2010-10-14 07:23 FamilyDocuments
drwxrwsrwx 102 david users 0 2010-04-30 06:35 FamilyMusic

and the files

david@HomePC:~> ls-l /mnt/net_store/FamilyVideos/
total 11329236
-rw-rw-r-- 1 david users  751507456 2010-05-01 13:46 01052010_134600.MPG
-rw-rw-r-- 1 david users    5202529 2005-02-20 09:55 100_0052.MOV

You could also try mounting as follows

sudo mount -t cifs -o username=your_username,password=yourpassword,uid=username,gid=users //path_to/samba_store_name   /local_mount_point/

where username and password are those for the samba store

---

### Post by SonicSteve on 2010-11-14
This is known bug, 

I don't know when Samba will see the definitive fix.

[https://bugzilla.samba.org/show_bug.cgi?id=7791](https://bugzilla.samba.org/show_bug.cgi?id=7791)

It effects copy to any "signed" server. This means that all shares to windows clients should be OK. The strange thing is that this bug was started before 10.04 was release but I never had an issue with any Ubuntu version till now. Perhaps the problem was some windows server update along the way.

---

### Post by SonicSteve on 2010-11-14
Sorry for the double post but if this works you may not mind so much. I did some digging around about upgrading libsmbclient 3.5.4 (the buggy file), and so I looked up samba ppa. 

I found this;

[https://launchpad.net/ubuntu/natty/i386/libsmbclient/2:3.5.6~dfsg-1ubuntu1]("https://launchpad.net/ubuntu/natty/i386/libsmbclient/2:3.5.6%7Edfsg-1ubuntu1")

This is a 11.04 file so I don't know if it will work. I'll try it tomorrow morning, likely the worst that will happen is that the deb file won't install because it's the wrong version. Try it at your own risk, it could cause problems. I haven't found a way to install libsmbclient 3.5.6 nicely on 10.10 yet.

The file installed but I don't think the bug fix has been applied to this yet. In other words it didn't work.

---

### Post by wokandabirder on 2010-11-22
Anyone having any luck with this one? I'm a novice, so not sure if there is a fix. I tried a reinstall of the libsmbclient package, but the problem still exists. is this a bug in libsmbclient?

---

### Post by Arador Aristata on 2010-11-23
Ok, so while they say a fix has been released it still does not work for me. They point to a problem in gvfs but it looks more like a libsmbclient issue to me as well.

I finally found a work-around by installing libsmbclient 2:3.4.7~dfsg-1ubuntu3.2 as was used in Lucid and that fixed the issue for me though I am not very comfortable with that fix.

[https://launchpad.net/ubuntu/lucid/+package/libsmbclient]("https://launchpad.net/ubuntu/lucid/+package/libsmbclient")

Though under this fix I noticed that Bookmarks are not always made in Nautilus when I tell it to.

Use at own risk but this at least fixed the Copy problem for me and I can continue my usual work until they bring out a proper fix to upgrade to.

---

### Post by hfw on 2010-11-23
I hope they get a real fix out for this soon.  This has been plaguing me since upgrading to Maverick as well.  It makes it difficult to use Ubuntu full time at work...

---

### Post by wokandabirder on 2010-11-24
Looks like the fix has been verified and should show up in updates soon. To see status, look at the bugrtrack...

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/393012](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/393012)

---

### Post by Arador Aristata on 2010-11-25
Yip, it is finally committed to Proposed Updates so if you can not wait for it to filter into the normal updates:

[https://wiki.ubuntu.com/Testing/EnableProposed]("https://wiki.ubuntu.com/Testing/EnableProposed")

Tested it and it works nicely. Pity it took them so long since release to fix such a show stopper.

---

