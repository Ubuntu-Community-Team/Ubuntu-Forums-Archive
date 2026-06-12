---
title: "NFSv4 Help"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by lofttroy on 2013-01-27
Been here on Ubuntu for a couple of years and finally thought I knew something and then I ran into this gem tonight:

The setup:
All machines running LTS 12.04.1, updated/upgraded within the last day.

MachineServer:
exports /dir x.x.0.0/24(rw,sync,no_subtree_check,no_root_squash) x.x.1.0/24(rw,sync,no_subtree_check,no_root_squash)
User: cat (uid: 5001, gid: 5001)
User: dog (uid: 6001, gid: 6001)

MachineA (on subnet x.x.1.0):
User: cat (uid: 5001, gid: 5001)
Mounts directory, everything works perfectly user id is correct and permissions work as expected from client.  Multiple machines on this subnet work flawlessly.

And then we come to the problem child
MachineB (on subnet x.x.0.0):
User: dog (uid: 6001, gid: 6001)
Same fstab file with the exception of the different subnet. When a directory is mounted on MachineB the permissions are squashed to nobody,nogroup.  I know the mount works as I can set the permissions (on the server) to 777 and write files.  The files end up as nobody/nogroup, but are being written to the correct uid on the server as shown by ls -ln.

I'd appreciate any help/insights anyone can offer.  If this doesn't seem clear, please ask me questions to clear it up.

Thanks,

---

