---
title: "Samba mounts fail to reconnect"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by azzid on 2008-12-12
I have a machine running Ubuntu (cant remember which version I installed, but apt-get has helped me keeping it up to date) where I have a few samba shares mounted. Mounting the shares work like a charm and a few lines in the fstab keep the mounts set up after rebooting and all.

My problem occurs when the machine hosting the shares goes offline and then comes back online, after that my mounts get screwed up.
I can remount an everything works fine, but if I don't the folder connected to the mount doesn't work.

If I for example use filezilla to sftp into the ubuntu box after the windows machine has rebooted the filezilla session will hang if I try to browse the folder that is supposed to point to the windows share.

As I stated above the problem is easily worked around by just firing up putty and remounting the folder, but it is kind of annoying.

Is there some way one can ensure that ubuntu remounts the share automatically after the windows machine has been offline?

Since I have seen this problem in other linux environments with samba shares I know this is a problem not within ubuntu but with samba itself, but I'd like to toss out the question here to hear if anyone has been able to work around this in a more elegant way.

Sincerely,
Mattias

---

