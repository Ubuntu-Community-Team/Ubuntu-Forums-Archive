---
title: "Unable to update files on DNS323"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by blueberry7 on 2010-01-23
Hi,

I am still suffering the same problems with my DNS323:

* Timestamps change when files written to NAS
* Unable to update files once written to NAS
* Unable to CHOWN or CHMOD files on NAS

My fstab looks like this:-

```
//192.168.1.68/Volume_1/root    /media/nas    cifs    username=nas-user1,password=nas-user1,uid=502,gid=702,rw,iocharset=utf8,file_mode=0770,dir_mode=0770    0    0
```The UID and GID exist on both my NAS and Ubuntu machine.

NAS permissions restrict access to nas-user1.

I've tried options "noperm", "nounix" in fstab and "client lanman auth=yes" in smb.conf; all with no joy. Think I've exhausted the internet - been searching for weeks :-(

All I want is to be able to use the DNS323 as an external (network) drive; am I asking too much - is anyone else havng these problems; does anyone have their DNS323 configured where they're able to do the things I can't?

All works fine from a Windows laptop; would hate to have to use Windows more :-(

Help.

Mike

---

### Post by mtb-cliff on 2010-01-24
I am with you on this one. I have four karmic machines and one of them will not connect to any of my windows shared files for the same reason and it is driving me crazy trying to figure why the other three have no problems. Only one of the shares is my DNS-323, though it is the most important....

---

### Post by mtb-cliff on 2010-01-24
just updated my smb.conf with the both
	client lanman auth = Yes 
	lanman auth = Yes
Mine now works to the dns-323. You might want to check out this thread as well.
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by blueberry7 on 2010-01-24
Thanks for the advice. I am very familiar with the link you provided ;-)

I fortunately had no problems mounting the volume - just with amending files and their timestamps. Here's an update in case it helps anybody else...

(1) Adding "nolinux" in the mount options and a reboot solved my problem updating files
(2) I can't change the time-stamp of files (frustrating because they are mainly digital photos and their time-stamp changes when I copy them with either the command line or Nautilus. JHEAD - an excellent utility to manipulate the meta-information contained in JPG's throws an error when trying "jhead -ft" but works OK from Windows.
(3) I can't change permissions.

Thanks.

---

### Post by blueberry7 on 2010-02-05
So, still messing around with this issue.

As an update in case anybody finds themselves in a similar position.

Using the following in /etc/fstab I'm still left with the issues or ownership; timestamps etc

```

//192.168.1.68/Volume_1/root    /media/dns323/    cifs    users,uid=1000,gid=1000    0    0

```

If however I mount after my session has been started and I've logged into my desktop using exactly the same but from the mount command and not fstab everything works fine - I even get a recycle bin which was a nice surprise as I thought it was going to be something else to fix (funscript workaround on the device).

Is it usual practice to add mounts to .bashrc rather than have it generic in fstab?

Thanks,

---

