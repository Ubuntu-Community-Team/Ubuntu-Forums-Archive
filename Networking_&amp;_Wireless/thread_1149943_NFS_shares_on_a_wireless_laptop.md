---
title: "NFS shares on a wireless laptop"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by billybennett on 2009-05-05
Hello--

I've got a NFS server that shares out a couple of directories.  I've also got a laptop that is capable of mounting those shares. 

My problem starts when I resume or restart my laptop when its only connection is the wireless adapter.  When the network is up I'm able to type sudo mount -a which works great but I'd like not to do that.  I've tried making a script in ~/.scripts/post-up.sh that has sudo mount -a in which I've added a post-up command to run that script in my interfaces file.  I usually refrain from posting because I can typically find solutions to my problems somewhere. 

I'm surprised I have not found a simple fix for this type of issue.  Please if you have any ideas let me know because it's been eating away at me for a couple days.

Thanks!

---

### Post by jkarcz on 2009-05-05
Hmm.  I have my desktop nfs serving 2 dirs and my wireless-only laptop always remounts then after a suspend-to-disk.  My fstab on the client is:
 
10.11.98.11:/data /data  nfs defaults 0 0

My etc/export file on the server looks something lke this:

/data 10.11.98.13(rw,no_subtree_check)


How do have yours setup?

---

### Post by billybennett on 2009-05-08
jkarcz,

My settings are similar but not exactly like you have.  

I'm going to try defaults 0 0 in my exports.  I will update with my findings.

Thank you!

---

