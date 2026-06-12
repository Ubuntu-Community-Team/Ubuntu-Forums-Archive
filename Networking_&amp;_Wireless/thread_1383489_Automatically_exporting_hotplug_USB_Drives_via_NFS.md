---
title: "Automatically exporting hotplug USB Drives via NFS"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by Prendi on 2010-01-17
Hi,

I got a media player device that can playback video files from NFS shares on my tv. Now I want to configure my Ubuntu server so that I can hotplug USB drives and the server will automatically make the drives available via NFS. 

My line of thought was to export the /media path via NFS and mount it on the media player so that the server will automatically export all connected USB drives. Unfortunately, each entry in the /etc/exports only exports a single file system and not those mounted below it. Thus, when I mount the server's /media on the media player, I can see folders for each partition of a connected USB drive, but they will appear as being empty and not show the drives' contents.

Is there a way to make NFS automatically export everything including other file systems mounted below a certain location? Or is there a way to achieve something similar?

SMB is not an option, because the media player is just too slow to stream HD content via Samba.

---

