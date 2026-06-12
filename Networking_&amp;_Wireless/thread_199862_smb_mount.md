---
title: "smb mount"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by thor918 on 2006-06-19
hi I'm using fstab to auto mount a smb share that is located on a windows guest pc. Yes i'm running linux as the host pc.
so I need some way to mount it when the guest pc is up and running.
what is the best way to do this?
if it only was possible to setup a temporary mount, that would try to connect  to the share on access.

---

### Post by x64Jimbo on 2006-06-19
I'd recommend putting a mount script in your crontab that runs every few minutes. If the machine is not on the network, the script will fail, but it won't take very much processor power. Another, slightly more complex idea is that you could put a startup script on the windows box that would trigger the mount command on the linux machine. You'd have to have a service waiting on the linux machine waiting for a "hello, I'm awake" signal from the windows box. For info on how to write these kinds of services/scripts, google around for linux shell scripting and crontab.

---

### Post by thor918 on 2006-06-19
thanks ;)
I was thinking about using crontab.
but hehe I was wondering if there where something more professional approach 
:)
I think I read a little while back about a linux deamon mounter, that would unmount all mounts temp. when they where not used, and if anyone accessed theme it would mount them back...

---

### Post by AmunKar on 2006-09-26
How can I mount without to be sudo?

---

### Post by AmunKar on 2006-09-26
How can I mount without to be sudo?

---

### Post by fstab on 2006-09-26
To connect to the share on demand, you can use autofs.  It does not maintain a persistent connection, just connects when you try to enter the mounted directory.  It's good in situations where the remote server you're mounting from is not always on.

After installing autofs, you do something like this:

#  Edit the file /etc/auto.master:
Remove the comment indicator (thats the # sign) from the line that says:
/misc	/etc/auto.misc	--timeout=60

# Edit the file /etc/auto.misc adding something like:
shared_dir      -fstype=smbfs    file_server_hostname:/mnt/shared_dir

I'm not exactly sure of the syntax for what goes inside the auto.misc file.  You'll have to look that up.

# Type the command /etc/init.d/autofs restart 

Then when you 'cd' into /misc/shared_dir it will automatically mount the dir for you.  You can make symbolic links to the /misc/shared_dir if you want the remote dir to be 'mounted' somewhere else.

:)

---

