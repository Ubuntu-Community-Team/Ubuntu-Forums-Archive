---
title: "Unable to access some nfs shares"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by Peter Bell on 2011-01-13
At, or around, the time of upgrading from Lucid to Maverick, shares on some of my nfs servers have become inaccessible: 
```
peter@Desktop:~$ ls /net/10.2.1.21/
opt
peter@Desktop:~$ ls /net/10.2.1.21/opt/
sybhttpd
peter@Desktop:~$ ls /net/10.2.1.21/opt/sybhttpd/
localhost.drives
peter@Desktop:~$ ls -l /net/10.2.1.21/opt/sybhttpd/localhost.drives/
total 0
drwxr-xr-x 2 root root 0 2011-01-14 01:52 USB_DRIVE
peter@Desktop:~$ ls /net/10.2.1.21/opt/sybhttpd/localhost.drives/USB_DRIVE/
ls: cannot open directory /net/10.2.1.21/opt/sybhttpd/localhost.drives/USB_DRIVE/: No such file or directory
peter@Desktop:~$ 

```

The share is hosted on a PopcornHour Network Media Tank, running a Linux system.  With Lucid, I was able to access the share without any problems, both in Nautilus and from terminal.  I can still access the share from other nfs clients - it's just ubuntu/Maverick which exhibits this problem.  I have tried reverting to older firmware on the PopcornHour but that doesn't make any improvement.

Was there some significant change in nfs with the Maverick release, or have I misconfigured something?

Can anyone suggest how I can go about identifying and rectifying the problem?

---

### Post by Peter Bell on 2011-01-14
Does anyone have any thoughts on this?  Am I the only person with this problem?

I don't understand why I can access the whole directory tree but fail when I reach the device share.

Also, why does this problem only affect Ubuntu Maverick ... what changed in nfs with the 10.10 release?

I have three machines running Maverick and they all behave in exactly the same way.  A Xandros machine can access the device and files without any difficulty, as can a non-*nix machine with an nfs client.

---

### Post by darkdragn on 2011-01-14
Just brain storming, and i'm not too sure, but an update to nfs-common, or anything else related to your ability to mount nfs, might have affected your minimum security requirements for mounting an nfs share. In other words, those nfs servers might be using some options that are no longer allowed, or might just not have something enabled that your computer wants to be enabled. Try looking at the different server config files, and eliminating/adding options through cross reference until it starts working.

Or perhaps it could be the permissions to that folder... They might have been changed accidentally, and the upgrade was a coincidence... but you already checked that, probably... I'm sorry, just brainstorming.

---

### Post by Peter Bell on 2011-01-15
> **darkdragn said:**
> Just brain storming, and i'm not too sure, but an update to nfs-common, or anything else related to your ability to mount nfs, might have affected your minimum security requirements for mounting an nfs share. In other words, those nfs servers might be using some options that are no longer allowed, or might just not have something enabled that your computer wants to be enabled. Try looking at the different server config files, and eliminating/adding options through cross reference until it starts working.

The PopcornHour is very much an appliance, rather than a computer system.  Users aren't expected to know about, or fiddle with, the config files.  I could attempt to investigate what config files are involved, and try changing things.  However, this comes back to my original question - what has changed in the Ubuntu nfs with the upgrade to Maverick?  Knowing this might give me a clue where I should start fiddling.  In any case, the PopcornHour O/S loads from flash and I suspect that all the configuration files are (re-)created at boot time and held in ram.

> Or perhaps it could be the permissions to that folder... They might have been changed accidentally, and the upgrade was a coincidence... but you already checked that, probably... I'm sorry, just brainstorming.

Permissions on the all the pertinent folders and files are set to full rwx for all users (777), so I'm not sure that it can be a permissions issue.

However, thank you very much for your thoughts!

---

### Post by Peter Bell on 2011-02-17
After a break of some weeks, I've just spent a considerable amount of time re-addressing this problem.

I discovered that, by default, the mount.nfs command applies the 'vers-4' option.  I wonder, then, what is the purpose of the mount.nfs4 command???

I haven't reverted to a Lucid installation, but I presume that this behaviour of mount.nfs is new, since I never encountered any difficulty prior to Maverick.

Anyway, it turns out that the solution is simple - I have to append the 'vers=3' option to the /net line in auto.master:

```
/net   /etc/auto.net vers=3
```

---

