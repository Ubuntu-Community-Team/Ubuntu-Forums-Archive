---
title: "SSH, SFTP with Chroot problems, paranoid SSH?"
date: 2013-04-08
forum: Networking &amp; Wireless
---

### Post by CMDRSweeper on 2013-04-08
Hello

I have been trying to get a SFTP setup going for friends to access files on my RAID 6 array.
Problems arise with permissions and SSH paranoia if I do not allow it to be root owned and with no permissions given to group.
Sadly I need the group to be something other than root and have access to it as I use the same array to store files on, both from the server and via a Samba / CIFS share.
So far I have locked down SSH enough to work as both allowing me to login as an administrator with a key and keyless, password only for the sftp users (locked down to have no shell for an example)

The main problem is that with chroot (Prevent them from browsing folders like /bin /var etc and from seeing those as it causes less clutter) is that it seems to expect it to own the directory exclusively, and that... is a problem.
Any ways to work around this problem or maybe even make SSH behave and not be a webhost like nazi (This is not a webhost setup at ALL!)

Thanks.

SOLVED: If anyone attempts to do this, any solution with the chroot is bound to fail sadly.
The workaround I did is listed on this webpage here: [http://www.ericstockwell.com/?p=54](http://www.ericstockwell.com/?p=54)
If that website goes down the basic part of it is, you cannot use the same folder for chroot that you use for your samba share, so instead you have to make one somewhere else that you can give the proper permissions that the paranoid OpenSSH wants.
From there the next step gets hackish, you have to use "mount -o --bind (From share) (to share)" where the To share is a folder you have made in the chroot setup, pending on your distro you may encounter a nasty bug where the kernel silently ignores the -r due to the --bind parameter, and as a result you must issue a remount like this: "mount -o remount,ro (Path to your mounted share in the chroot folder)" to make the share read only.
For the security minded, the time period between the share is mounted and remounted, it is writeable, so this may be an issue.

For the reason and explaination as to why the bug exists with the mount command and the --bind parameter, you can find that here: [http://superuser.com/questions/185125/mount-bind-ntfs-partition-in-read-only-mode](http://superuser.com/questions/185125/mount-bind-ntfs-partition-in-read-only-mode) scroll down a bit to the last post.

Also if you want to do this at boot, you may use the /etc/rc.local for it, but be advised it may not be "best practice" but it will work if you are in a pinch.
If anyone has a best practice solution for this scenario I would gladly welcome the post and input, I am mainly posting the solution here so somebody in the future with a similar problem may find a solution via Google.

---

