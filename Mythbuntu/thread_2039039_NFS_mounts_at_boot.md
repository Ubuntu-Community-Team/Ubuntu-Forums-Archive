---
title: "NFS mounts at boot"
date: 2012-08-07
forum: Mythbuntu
---

### Post by jbebel on 2012-08-07
In previous mythbuntu releases, I've had no problems mounting NFS shares at boot time.  I keep music and pictures on a separate server and mount them into /var/lib/mythtv.  In Precise, this is no longer working.  In the past, I found that network manager might not have the network up, so I put the interface in /etc/network/interfaces, which got it up earlier during the boot.  Now that doesn't appear to be working either.  Has anyone successfully gotten NFS mounts working at boot time in Precise?  Any tricks?

---

### Post by anonymousdog on 2012-08-08
> **jbebel said:**
> In Precise, this is no longer working
What DOES happen on boot?  How does it fail?

I have NFS mounts in /etc/fstab on two client PCs that also use Network Manager to manage NICs...if the network's down, they'll stall during Mythbuntu splash screen with an error about not mounting the NFS share.

---

### Post by jbebel on 2012-08-08
It behaves like the network is down.  The splash screen says that the share couldn't be mounted, and I can wait or continue.  Unfortunately, neither of those options work, so I have to reboot into rescue mode to remove the entry from fstab.  It does the same things regardless of whether there is an entry in /etc/network/interfaces.

---

### Post by aovermy on 2012-08-08
I put my nfs entries in fstab with noauto in order not to automount them. Then I put a small script in startup to do the actual mounts. This way even if the network is legitimately down the machine will still come up.

---

### Post by jbebel on 2012-08-08
That's certainly a workable solution, and perhaps a good idea since it isn't necessarily required to boot the machine, but I'm still interested in learning why it isn't working.  Mounting NFS at boot time seems like a fundamental capability that Linux should have.  upstart should be making sure that network mounts are only mounted after the network is up.  I'll do some more digging.

What I'll probably eventually do is turn on autofs to only mount them when they are needed.

---

### Post by Rotak on 2012-08-09
I had this problem a while ago. It was caused by a hicup (or Kernel bug???), where the NFS shares are tried to be mounted before the network came up.

I could solve this by adding the "bg" option to the line in fstab, which retries to mount the NFS share in background if the initial mount attempt fails. That will prevent the NFS mount to "block" the boot sequence.

---

