---
title: "Make permanent NFS mount in diskless client"
date: 2008-09-12
forum: Mythbuntu
---

### Post by impossibilechecisiaquesto on 2008-09-12
Hi, it's always me.

I fix all problems excepet one,
i wanna mount in my clients the directory where i store all my media to use the mythplugins(video, audio).  
If i modify the fstab in the client it won't persist after reboot, so i chrooted in the server, changed the fstab and rebuild the image but the fstab is the same before.

How can i?

TNXK

Martino.

---

### Post by volkswagner on 2008-09-12
> **impossibilechecisiaquesto said:**
> Hi, it's always me.

I fix all problems excepet one,
i wanna mount in my clients the directory where i store all my media to use the mythplugins(video, audio).  
If i modify the fstab in the client it won't persist after reboot, so i chrooted in the server, changed the fstab and rebuild the image but the fstab is the same before.

How can i?

TNXK

Martino.

You may want to post /etc/fstab from your client machines.

This is the how-to I use.

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

Did you run the following on the server and say no to bind loopback?

```
sudo dpkg-reconfigure portmap
```

Did you add your network range to /etc/exports on the server?

Like this

```
/var/lib/mythtv/videos /192.168.1/24(ro,async,no_root_squash,no_subtree_check)
```

Change the ip address range above to match your home network.

---

### Post by laga on 2008-09-12
That's a known problem.

You can add your mount commands to /etc/rc.local on the client. 

Or you could try adding "[default]" at the top of your lts.conf on the server.

---

### Post by volkswagner on 2008-09-12
> **laga said:**
> That's a known problem.

You can add your mount commands to /etc/rc.local on the client. 

Or you could try adding "[default]" at the top of your lts.conf on the server.

Is this a know problem with diskless only?  I had a problem with NFS on reboot.  I had to add commands to rc.local.  The problem was related to networking on boot.  It appeared to be looking to configure wireless even though I only had a wired interface.

Not sure if networking can be restarted with diskless.

I would be interested to see if

```
sudo /etc/init.d/networking restart
```

Would get the mounts working.

I added the above to /etc/rc.local as per the following post #7

[http://ubuntuforums.org/showthread.php?t=675183&highlight=auto+mount]("http://ubuntuforums.org/showthread.php?t=675183&highlight=auto+mount")

---

### Post by laga on 2008-09-13
As far as I know, this problem is specific to -diskless. There is a LTSP script which overwrites /etc/fstab on every boot. I'm setting up a diskless right now so I can fix some of these bugs..

---

### Post by impossibilechecisiaquesto on 2008-09-16
The problem is if i change the /etc/fstab in my client  work, but after the reboot the fstab came out starndard. Without additional change.

I'll try the /etc/rc.local way.

I'll let you konw.

---

### Post by impossibilechecisiaquesto on 2008-09-20
work adding the mount string on rc.local.

Thanks a lot

---

