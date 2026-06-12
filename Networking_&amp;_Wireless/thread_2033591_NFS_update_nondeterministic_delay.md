---
title: "NFS update nondeterministic delay"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by Hossbeast on 2012-07-26
I am extremely frustrated. I am not sure if this is the right place to post, or even how to debug this issue at all. Hopefully someone can shed some light, because I am on the verge of hacking out an rsync/inotify-wait solution which amounts to reinventing the wheel. I KNOW NFS is made for exactly what I am trying to do. ARGH.

Here is my setup.

NFS Server is my Ubuntu desktop

39633 todd@hossbeast:~/code $ uname -a
Linux hossbeast 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

39637 todd@hossbeast:~/code $ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric

I don't know how to figure out the version of my nfs server, or whatever. I think it comes with the distro. Otherwise I used synaptic to install it. Its the kernel NFS server.

NFS Client is a different linux installation, on a VirtualBox VM with bridged networking.

On the client I have a mount point to the server at /mnt/code, then I have a symlink in /usr/local/bin pointed somewhere into /mnt/code.

I am then executing the script repeatedly on the client, while modifying it on the server.

HOWEVER I AM NOTICING A HUGE DELAY between modifications on the server, and modifications on the client. Like, tens of seconds, thirty seconds, a minute. Then, sometimes, its instantaneous. There appears to be no correlation with any factors in the known universe. I can close the file, reopen the file, change it again, and rewrite it. If it makes a difference, I am using vi to edit the file. But I can close it and, like, echo >> the file, or something, and it doesn't help. The update is propagated whenever it damn well feels like it, and no sooner. Recreating the symlink does nothing (of course).

Any ideas appreciated. I have no idea what to look at or try.

---

### Post by papibe on 2012-07-26
Hi Hossbeast.

Could you post your client nfs mount options?

Regards.

---

### Post by Hossbeast on 2012-07-26
The only option on my client mount is "nolock"

---

### Post by papibe on 2012-07-26
I see.

NFS as default is set to be fast, at the cost of being a bit slow to sync.

If your main concern is consistency between clients and the server, you may consider using the 'sync' option.

Although it has a little of a toll on speed, it flushes all changes to the server faster (supposedly after every save).

I hope that points you in the right direction. Let us know how it goes.
Regards.

---

### Post by Hossbeast on 2012-07-26
I will try my luck with the sync option and report back.

Thanks

---

### Post by Hossbeast on 2012-08-09
This appears to have fixed my problem

---

### Post by papibe on 2012-08-09
:D I'm glad to hear that!

Please mark the thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

