---
title: "System created desktop icon won't access zfs mirrored pool"
date: 2019-01-14
forum: MINT
---

### Post by marcerickson on 2019-01-14
I had my Mint 19.1 x64 installation put icons (links) to my  filesystem and removable drives by right clicking the Desktop, clicking  Desktop Settings > Icons tab then checking Removable Devices in the  Default Icons section.  It shows removable devices, including the zfs  mirrored pool volume I set up.  But the zfs mirrored pool volume icon is  greyed out and clicking it gives a 'Failed to mount:  mount:  /path/to/Volume_Name: operation permitted for root only' error.


  But the volume is mounted and I can create, save, edit, and delete  files by going through File Manager to /path/to/Volume_Name.  Right  clicking the greyed out Volume_Name on the Desktop gives the context  menu of Open; Mount Volume; and Properties -  Properties is greyed out.  Logging into the GUI as root doesn't make the Properties  right click context menu of the zfs pool volume icon on the Desktop  accessible - it remains greyed out.


  Is there any way to make the greyed out Volume_Name icon on the Desktop open the zfs pool volume?

---

