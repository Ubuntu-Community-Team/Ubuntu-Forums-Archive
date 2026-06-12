---
title: "some applications cant see network folders"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by mmoalem on 2009-04-07
hi there all - I have a network with shared folders on 2 windows pcs. I can access both through Places>Network>MSHOME>. This works fine but there are some applications like handbrake or website like ADrive with a java based uploader that when trying to browse for a file do not have an option of browsing the network... is there a way to make them see the network?
NOTE: I do not have the windows pcs running all time like a server so i dont want to mount the shared folders on boot through fstab,
cheers
michel

---

### Post by mmoalem on 2009-04-07
hi there all - found a solution...
once i connect to a shared folder in nautilus it creates what i assume to be a temporary mount in Home>User>.gvfs
being hidden makes life more complicated so i created a symlink to the folder .gvfs with a name that doesnt start with a period and voila it is accessible from any application

---

