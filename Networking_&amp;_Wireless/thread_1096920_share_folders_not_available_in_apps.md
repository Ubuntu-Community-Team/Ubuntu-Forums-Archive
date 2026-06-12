---
title: "share folders not available in apps"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by monkeykinglives on 2009-03-15
Even when I bookmark a mounted shared folder, it does not appear as a location option when trying to attach a file to an email msg using Thunderbird, or a webmail site using Firefox. I've tried bookmarking the folder, the share, the volume, etc, but none appear, or are accessible. There's no apparent way to drill into the network to get to the folder.

I'm guessing that it has something to do with the folder not mounting during start up, but manually later, as all my disks and usb drives appear.

I'm not sure whether I have to do something to get these network drives onto the places roster, or if I have to mount my network drives differently. But since the network is not necessarily connected when fstab is processed, I don't see how that can work.

Thunderbird has a config setting for attachment directory [I think] that is currently set to /home/user. Of course, my network locations are not mounted there. Changing this to a  network location didn't work eg smb://nas-xx-xx-xx/documents/.

---

