---
title: "Connecting to an NFS share on a stand-alone retail NAS"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by elcman on 2009-04-01
**Edit:**
I think I've determined my problem as a matter of syntax. It has finally sunk in that NFS doesn't care about UID or GID and only cares about IP address.

In the NFS server config I am using 192.168.0.*/255.255.255.0 as the access mask. This says that it simultaneously the computer on 192.168.0.* and all computers within that subnet mask. 

I didn't receive an error from this usage, but it is a redundant method of determining who has access, so I'm wondering if it was a problem with the way I was presenting it. And perhaps the issue with me connecting ... I was always hitting the blanket RO access rule because of improper syntax.

So, instead of getting disgruntled with the way things work, I'll just get disgruntled with myself. :)

---
**Original post:**
I've been perusing the forums to find a very specific answer and I just can't manage to find it... and I've spent *far too long* trying to sort through documentation and trial and error rationale. 

So, here's my issue:
I have a NAS device that supports NFS shares. The device allows me to set up a user and define the UID for that user. When setting up the NFS share, I can set up the users who can use it and the address range as well. Part of that is the "base" permissions can be set to None or Read-only.

When I connect when the base permissions are set to read-only when using the usual fstab or mount commands from the user who *has* read/write access, I get read-only access.

When I change the base permissions to no access, it doesn't allow me to map the share.

My assumption is that I am not connecting with the right UID. Or it isn't being passed correctly. I have to use **sudo** to run the mount command, so... does it use the root User ID to map to the NFS. This is one I can't test because I can't use User ID 0 on the NAS box.

I even set up the read/write range to be everyone on my subnet. Should that allow anyone on that subnet to connect to it? Or is it still tied to user accounts? (I can see *squash_all* as the solution to that, but due to the security system in this box, it doesn't allow that selection.)

So, the question... how do I change my User ID when connecting to the box since, for some reason, it isn't lining up. I am within the subnet that is allow R/W access and I've made sure the UID is the same. Is there something on this NAS box that is not allowing me to connect *as* the user?

Oh, the thing that lets me know it *is* actually working, I should add, is that I used a Mac running OS X 10.5 to connect to the NFS share *without any issues whatsoever* using the *"Connect As..."* command and plugging in the right username to mount the NFS folder. Nautilus *does not* support NFS connecting as a default file system. ***WHY?***

I'm thinking that the primary network file sharing protocol that I would expect all Linux derivatives to support... is completely unsupported by default. Wow.

Anyway, my frustration is pretty high with this right now because it makes no sense why it isn't working the way it should and why I can't seem to set a User ID from a mount command or connect to NFS from Nautilus.

(By the way, I'm going to install the **super** tools as soon as I can so that I can use the **setuid** command, but my network has been down.)

Any feedback would be greatly appreciated. And, no, anything other than NFS is not an option, sadly.

---

