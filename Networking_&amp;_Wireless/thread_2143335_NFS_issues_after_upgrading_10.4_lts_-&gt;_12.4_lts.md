---
title: "NFS issues after upgrading 10.4 lts -&gt; 12.4 lts. NFS clients connect using nfs v2"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by lajo001 on 2013-05-08
I recently upgraded my file server from 10.4 lts to 12.4 lts and after that I have run into issues with the NFS shares that are exported from that server. I have a number of media player devices that connect to the server using NFS to access large (10+ GB) media files which worked just fine in 10.4, but now in 12.4 I get (in the media players) incorrect file sizes and media files interrupt after some playback.
I Googled the incorrect file size and got the clue that this was a known issue in NFS v2 and when I check with nfsstat in the 12.4 server I see that there is only NFS v2 traffic however NFS v2,3,4 are all "active" listening on the ports.

So the big question is what changed from 10.4 to 12.4 with regards to NFS? The nfs-kernel-server installation was/is as per default in both cases, the only configuration made are the entries in the /etc/exports file, exactly the same file both 10.4 as 12.4.

I assume that since it worked in the 10.4 installation that the NFS clients (media players) connected using NFS v3 or v4, so why is it NFS v2 now in 12.4? Can this be changed/controlled in the server somehow? I've looked at plenty of how-to's but not found any good answers... 

And ofcourse, the media players haven't changed either....

---

### Post by lajo001 on 2013-05-10
I'll reply to my own question in case someone else comes across this. Google led me to this Ubuntu bug report in 11.10 version 
[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/897644](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/897644)

This point to a bug in the nfs-kernel-server file, which was easily corrected now that I knew where to look. After correcting the bug, NFS v3 was again enabled and the exports show up as they should in the clients.

---

### Post by zosky on 2013-05-30
thank you Agolajo001

i did the same upgrad on my server and got the same result (all clients having issues with files 2gb+)

when i try the command that disabled v3 (from the init script) i get an error
```
rpcinfo -u localhost nfs 3
The program 'rpcinfo' is currently not installed.  You can install it by typing:
sudo apt-get install rpcbind
```
so i guess the upgrade process removed rpcbind
you could solve this by adding it back (like the error says to)

but i did the same as you and commented out the lines in the initScript

---

