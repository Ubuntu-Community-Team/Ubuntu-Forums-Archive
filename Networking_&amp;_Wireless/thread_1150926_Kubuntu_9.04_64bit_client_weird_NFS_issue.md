---
title: "Kubuntu 9.04 64bit client weird NFS issue"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by buntunub on 2009-05-06
Ever since installing Kubuntu Jaunty x86_64 on my gaming rig, which is also an NFS client, my NFS server (Hardy 32bit) has starting going crazy. Both are running the most recent stock ubuntu kernels for that release. Only when the Kubuntu machine is up and running, my server kern.log, syslog, and messages start dumping "nfs4_cb: server (client IP address) no reply, timing out", every 60 seconds until the server locks up hard after about an hour or two, which then in turn causes my Kubuntu client machine desktop to lock up hard, forcing hard boots on each. This is a standard wired home network here, and I get no such errors ever on the other Hardy 32 bit client that I have up and running. I got no such errors when I had that same Kubuntu client up and running on 64 bit Fedora10 either (GNOME version). This issue seems to be specific to Kubuntu or the Ubuntu Jaunty stock setup/kernel. I did notice another bugzilla thread about this on kernel.org and the Ubuntu kernel devel as well, but they were mostly talking about a Hardy kernel mod. Like I said, my Hardy to Hardy server/client never had an issue with this -- only the Kubuntu Jaunty 64 bit system causes it. Any help would be very much appreciated.

---

### Post by buntunub on 2009-05-07
Update to this thread --

I have added this issue to a kernel related bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253004"). There seems to be two issues - 1) NFS is hosed up pretty bad right now continuously looking for client callbacks which are reaching the server properly but the server refuses to acknowledge them, and 2) the issues caused by NFS screwing up with Jaunty are causing kernel oops on my Hardy server. A kernel patch was posted and I am testing that now. It seems to have fixed the kernel oops issue but the NFS error dumps continue like so -

```
May  7 15:38:42 kernel: [54299.484121] nfs4_cb: server  not responding, timed out
May  7 15:39:42 kernel: [54359.477775] nfs4_cb: server  not responding, timed out
May  7 15:41:42 kernel: [54479.469042] nfs4_cb: server  not responding, timed out
May  7 15:43:42 kernel: [54599.456338] nfs4_cb: server not responding, timed out
May  7 15:45:42 kernel: [54719.443645] nfs4_cb: server not responding, timed out
May  7 15:47:42 kernel: [54839.426911] nfs4_cb: server not responding, timed out
May  7 15:48:42 kernel: [54899.420550] nfs4_cb: server not responding, timed out
May  7 15:51:42 kernel: [55079.401475] nfs4_cb: server not responding, timed out
May  7 15:53:42 kernel: [55199.388769] nfs4_cb: server not responding, timed out
May  7 15:55:42 kernel: [55319.376052] nfs4_cb: server not responding, timed out
May  7 15:57:42 kernel: [55439.363326] nfs4_cb: server not responding, timed out
May  7 15:58:42 kernel: [55499.356971] nfs4_cb: server not responding, timed out
May  7 15:59:42 kernel: [55559.350614] nfs4_cb: server not responding, timed out
May  7 16:01:42 kernel: [55679.337889] nfs4_cb: server not responding, timed out
May  7 16:02:42 kernel: [55739.331521] nfs4_cb: server not responding, timed out
May  7 16:04:42 kernel: [55859.318813] nfs4_cb: server not responding, timed out
May  7 16:05:42 kernel: [55919.312447] nfs4_cb: server not responding, timed out
May  7 16:07:42 kernel: [56039.299726] nfs4_cb: server not responding, timed out

```

---

### Post by buntunub on 2009-05-09
Update to the update to the update..

I have submitted another bug on the side/main issue [here]("https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/373979") and there is another interesting read on this issue [here]("http://news.gmane.org/gmane.linux.nfsv4/") about 3/4 down the post page. Basically, it seems these error prints on the server side are harmless. Hah! So harmless they caused the Hardy server to lockup and requiring a patch to fix that. There was a fix patch put into the 2.6.27 kernel (Red Hat guys did that) but obviously, that does not help us with the LTS Hardy kernel, so some type of patch needs to be backported. Thats where I think its at anyway. Stay tuned for more glorious details!

---

### Post by buntunub on 2009-07-03
Update to this. I installed Archlinux GNOME and the issue went bye bye. This, along with a few other tests I ran leads me to strongly suspect Knetworkmanager as being the culprit. I believe a workaround might be using WICD or GNOME network manager, but never really had a chance to fully test that.

---

