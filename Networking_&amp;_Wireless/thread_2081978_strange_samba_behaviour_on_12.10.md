---
title: "strange samba behaviour on 12.10"
date: 2012-11-08
forum: Networking &amp; Wireless
---

### Post by sirpy on 2012-11-08
I've recently install ubuntu 12.10 on a new drive mounted on /.
When sharing (via nautilus sharing options) directories from my home folder on the new drive it works just fine, and can access it from other computers with only the guest account(no password required)

But when I try to share folders in partitions from my older drives mounted in /media I get permission denied when I try to access these folders from another computer with the guest account. (the shares are shown but not accessible)

If I access these shares with my username it also works fine.
But It doesn't require my password! (if i remove guest ok and use my username it does require my password)

I guess for some reason for these mounts it treats my username as the "guest" username

Any ideas how I can fix it, so it will simply work with the guest account?

---

### Post by Morbius1 on 2012-11-08
I think the question is how did you mount the other partitions.

** Did you add entries in fstab to mount these partitions? If so find out what the permissions are on them to determine if "other" can access the path to the shared folder.

** If you are mounting them through Nautilus or whatever Ubuntu calls the panel thingy ( sorry I use XFCE - old school I'm afraid ) then I may have an explanation.

I don't know if this comes from Debian, Ubuntu, or Gnome but someone is playing around with something they don't fully understand again. Instead of mounting at /media/LABEL the way they used to they now mount at /media/$USER/LABEL with funky permissions. For example:

```
ls -al /media
```You will see this for /media/username
> drwxr-x---+  3 root root    4096 Nov  8 06:49 usernameTHe little "+" at the end indicates that it's using access control lists to make something that was very simple to work with something that is now complicated to work with.

The only person who is going to be able to access the partition mounted within /media/username is "username" which leaves a remote samba guest out of the loop. You might be temped to just overwrite the permissions to somethig like 777 but it's not clear to me why they made the change or what repercussions changing permissions would have. 

You have 2 choices:

[1] Mount the partitions though fstab so you can take adult control over this process.

[2] Add an entry into /etc/samba/smb.conf that makes all remote users appear to be you for these samba shares. For example:
```
force user = morbius
```[COLOR=Blue]*Add it to the [global] section - under the workgroup line in smb.conf.*[/COLOR]

Then restart samba:
```
sudo service smbd restart
```

---

### Post by sirpy on 2012-11-09
Great!
I wasn't aware of this new + thing.
Thanks

---

