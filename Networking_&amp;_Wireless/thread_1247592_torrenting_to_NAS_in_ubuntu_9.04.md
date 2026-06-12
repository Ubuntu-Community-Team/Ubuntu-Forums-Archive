---
title: "torrenting to NAS in ubuntu 9.04"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by 123johanswe on 2009-08-23
I am using ubuntu 9.04. I have a NAS DNS323 installed on the network, I can access the NAS from Places using the following command smb://nas/volume_1, and files can be moved in and out from my nas. When trying to select destination folder in Transmission (and all other bittorrent programs I have tested) it is not possible to select network nor smb://nas/volume_1 only local folder stored on my computer can be selected as destination folder. Why can I access my NAS from "places" but not as destination folder in Transmission and how can I make my NAS the destination folder in Transmission?

Thanks!

---

### Post by Charles Kerr on 2009-08-24
> **123johanswe said:**
> I am using ubuntu 9.04. I have a NAS DNS323 installed on the network, I can access the NAS from Places using the following command smb://nas/volume_1, and files can be moved in and out from my nas. When trying to select destination folder in Transmission (and all other bittorrent programs I have tested) it is not possible to select network nor smb://nas/volume_1 only local folder stored on my computer can be selected as destination folder. Why can I access my NAS from "places" but not as destination folder in Transmission and how can I make my NAS the destination folder in Transmission?

Thanks!
Transmission doesn't know how to parse smb://path/to/folder.  I don't know the ins and outs of mounting remote drives, but if you can somehow mount the remote drive to appear local (e.g., /like/a/local/path) then Transmission can handle that.

Alternately, you might consider running transmission-daemon directly on your nas. :)

---

