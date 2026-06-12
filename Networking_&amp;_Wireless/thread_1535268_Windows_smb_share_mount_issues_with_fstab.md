---
title: "Windows smb share mount issues with fstab"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by Marctwo on 2010-07-20
I can actually achieve this but it's still a bit pants.  The following line format in fstab does mount the share for me:
```
//10.x.x.x/sharename /home/me/Music smbfs password=pswd 0 0
```
But I have a few problems with it:

1:  It takes quite a while to boot.  Nothing really major, just about an extra 15-20 seconds but considering I can mount it instantly from a terminal, I think this delay is just a bit wrong.

2:  It takes ages to shut down... upto about 1-2 minutes.  That's compared to a normal shut down in less than 10 seconds.

3:  When I'm logged on I can't unmount the share from the desktop;  I have to do it with sudo in the term.  I've tried including the 'user', 'users' and 'owner' options in fstab but they don't seem to make any difference (apart from the mount icon).

I get the impression that this is the preferred method for doing this so I'd like to be able to do it this way.

---

### Post by Marctwo on 2010-07-21
I thought I'd bump this with a bit more info.

In fstab I'm using the format:
```
//10.x.x.x/sharename /home/me/Music cifs guest,uid=me 0 0
```
This is the minimum I can use to get it auto mounted with ownership.  However, it still takes ages to close down - approaching 2 minutes.

I can unmount manually but only in a term with sudo.  But then shut down is about 6-7 seconds.

The relevant manuals seem to say that using the 'user' option will allow me to mount the share as user rather than root which I assume would then allow me to unmount as user - but it doesn't work.  I've tried 'user', 'user=' and 'user=me' but it only seems to change the icon and doesn't affect the mount-abilities at all.

I imagine I could write a script to unmount and shut down but surely I'm just trying to do something bog standard here...  I'm sure many people overcome this everyday.

---

### Post by rubylaser on 2010-07-21
Those fstab entries look okay.  If you install Samba on an Ubuntu box and you are using the NetworkManager for your network settings you are very likely to encounter the following error message when you shutdown:
CIFS: VFS server not responding
CIFS: No response for cmd 114 mid 3

This is a bug that's been in Ubuntu since Gutsy and it looks like it&#8217;s still there, but there is a work around.

The reason for getting the error message is the network (NetworkManager) is being shutdown before dismounting of the Samba shares, and dismounting a network share without a network well that won&#8217;t work so well.

You can use the following work around:
```
cd /etc/rc6.d
ls
```

You should see :
```
root@myth-backend:/etc/rc6.d#wpa-ifupdown the nr is probably 15
and
root@myth-backend:/etc/rc6.d#umountnfs.sh that nr is probably 31
```

Type:
```
sudo mv S31umountnfs.sh S14umountnfs.sh
```

The point is to give the umountnfs.sh a lower as your wpa-ifupdown.sh

Follow the above steps also for /etc/rc0.d
```
cd /etc/rc0.d
sudo mv S31umountnfs.sh S14umountnfs.sh
```

That "should" fix the slow shutdown for you.  

Also, soapbox below :)

I normally like to isolate my login credentials in a secure location like this...
```
sudo nano /root/.smbcredentials
```
Insert the following lines into the new file
```
username=myusername
password=mypassword
```
Save the edited file
```
sudo chmod 700 /root/.smbcredentials
```
```
sudo cp /etc/fstab /etc/fstab_backup
```
Edit fstab
```
sudo nano /etc/fstab
```
Add this line to the bottom of the file and change accordingly.
```
//10.x.x.x/sharename    /mount/location cifs  credentials=/root/.smbcredentials    0    0
```
You can apply permissions on the directory once mounted with the root user to allow your regular user r/w.  Also, mount is an admin action, so you'll always need to add sudo in front of it unless you edit your /etc/sudoers file to give your regular user access to that command (not recommended).  But, you shouldn't need to unmount by hand anymore, because it should be fixed with the previous changes.

---

### Post by Marctwo on 2010-07-22
Thanks for the reply rubylaser.  I tried your suggestion but it didn't seem to affect anything.  I tried a few shutdown/boot cycles just to be sure but no go.

I'm guessing that the idea behind renaming these links is that they're executed in alphanumeric order?  With this in mind I noticed another link in each of these dir's named 'S40umountfs'.  I tried renaming this along with the other to keep the same relative order but with the new higher order...  but that didn't work either. :)

---

### Post by Marctwo on 2010-07-23
Another bump and another update.

I tried using a login script to mount but this has inconsistent results probably due to the network connection timing being inconsistent.  But I don't really mind the reported errors and small extra time at boot from auto mounting through fstab - although it would be nice to have it streamlined.

I've also tried using a logout script to umount but that doesn't help and still takes just as long.  If I logout first then shut down from the login screen, it works fine but I certainly don't want to be doing that.

So at the moment I'm left with a umount script on my desktop which I can run manually before shut down.  Still far from acceptable but better than the previous logout/shutdown approach.

---

### Post by Marctwo on 2010-07-23
A bit more on this - 'cos I know you're all following this with baited breath...

I did the following:
```
sudo chmod a+s /sbin/mount.cifs
sudo chmod a+s /sbin/umount.cifs

```
...and I can mount/umount in nautilus or terminal according to the settings in fstab.  This is the kind of behaviour I'd have expected by default anyway.

This doesn't solve the shutdown time issue though.  But it does make it easier to unmount before shutting down.

---

### Post by Marctwo on 2010-07-26
Well I found [this]("https://help.ubuntu.com/community/MountWindowsSharesPermanently#System%20Hangs%20on%20Shutdown") which seems to fit in with rubylaser's diagnosis.  It does improve things a bit but the system seems to hang on the desktop instead (but not as long as before) and the shutdown splash is completely messed up.  It's far from smooth.

Surely someone can help me sort this seemingly basic problem...

---

### Post by Marctwo on 2010-07-28
As rubylaser pointed out, this issue is years old and so are the various work-arounds for it.  Unfortunately, these work-arounds don't actually work for everyone.

Apparently there was a fix released for this at the beginning of the year - I don't know anything about it but I'm guessing it didn't work...

There are two approaches to this problem that seem to give consistently good results:
1:  Manually unmount before shutdown/restart.
2:  Give up on samba/cifs.

---

### Post by Morbius1 on 2010-07-28
There is an alternate way to mount and unmount a remote share that might resolve your shutdown problem without resorting to option (2):
[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

It uses gvfs to mount remote shares and has the advantage of running in userspace so it will mount after fstab is executed and unmount before the network is brought down during shutdown.

When you use nautilus to browse to and mount a remote share it's actually using this command:
```
 gvfs-mount smb://10.x.x.x/sharename
```If you where to use that command from a terminal it will mount the remote share and display a mount icon on the desktop. When you shutdown the first thing that happens is the user is logged off and the remote share is unmounted. After that happens the normal root level shutdown procedure continues and network itself is shut down. The HowTo I referenced above tells you how to use the gvfs-mount command automatically at boot to mount remote shares.

There's only one problem with all this and it has to do with mount points. If you just need access to the share you have the icon on the desktop. But if you have an application that requires a direct path to the mountpoint you may have a problem. "gvfs-mount smb:" creates a mountpoint to a hidden directory here:
> /home/me/.gvfs/share_name at server_nameIf your application can access the hidden directory then there's nothing else to do. If however it can't or you would prefer a different mount point then you need to create a symbolic link from the hidden directory to a "real" directory. For example:
```
 ln -s /home/me/.gvfs/"share_name at server_name" /home/me/Music
```

Anyway, just something to consider.

---

### Post by Marctwo on 2010-07-28
Thanks Morbius1,

I knew about the mountpoints in ~/.gvfs/ but I didn't know about the gvfs-mount command.  I just had a quick go with a login script and it worked well so this may be just the ticket for me.

I'll have a good mess about with now, cheers. :)

---

### Post by peertje888 on 2010-09-18
So **ONE** solution to this would be to let the network-manager control the mountnfs init script.

**OR** the network manager should be using another init script which does the actual connecting. This script in turn can be stopped later then mountnfs.

**ANOTHER** would be that "mount" recognizes the remote machine is not connected any more and therefore dropping the mount. And this is probably kernel related.

---

### Post by m2xtreme on 2011-01-30
I posted another solution here: [http://ubuntuforums.org/showthread.php?t=1572660](http://ubuntuforums.org/showthread.php?t=1572660)

---

