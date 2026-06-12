---
title: "Mount sshfs after network initialization"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by fela on 2011-04-08
I've got a non-vital sshfs filesystem in my fstab (by non-vital I mean just files that I access on-demand).

However, the fstab file seems to get read and things try to mount before the network has been brought up. I recently switched to Kubuntu 10.10 from Arch, and Arch didn't display this behaviour.

I'm wondering if it's possible to make it mount the sshfs filesystem AFTER the network has been brought up?

Thanks

---

### Post by Sallée on 2011-05-12
Check this thread: [http://ubuntuforums.org/showthread.php?t=430312]("http://ubuntuforums.org/showthread.php?t=430312")
It is a bit older, but it has worked faithfully for me throughout Lucid, Maverick, and now Natty.

---

### Post by fela on 2011-05-12
Thanks for the reply.

Since writing that post I've switched mainly to Windows, for better hardware support (in this case) and Photoshop. However I still have Ubuntu on my system and will check out that guide next time I boot it, cheers :)

---

