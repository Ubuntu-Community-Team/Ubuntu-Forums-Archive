---
title: "Cannot see myself on network"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by mje1708 on 2011-08-26
Hi

I had networking up and running fine. Basic setup was one desktop  running 11.04 with its hard drives shared. I had two other laptops both running 10.04 - everyone could see each other fine and access any shared folders.

Yesterday I installed 10.04 on the desktop instead of 11.04 because I prefer it. Everything seems fine - however, since doing that, I cannot access its shared drives from either of the laptops.

To make things even stranger, when I select "network" on either of the laptops nothing is shown - just the windows share icon - not even themselves! However the desktop is able to see and access both laptops fine if I share any of their drives.

The two laptops are wireless - the desktop is wired. I tried plugging an ethernet cable into one of the laptops in case the wireless was somehow at fault but no difference.

Anyone any suggestions? It is giving me a headache.

Thanks

Mike

---

### Post by northd_tech on 2011-08-26
I'm FAR from an expert on Samba, but I've successfully gotten it to Windows print/file share in both directions under several flavors of Linux going back to the 1990's.

Under a recent Ubuntu (10.04.2 LTS Lucid Lynx) in my case, here are some things that you should probably verify are installed under Synaptic Package Manager:

samba
samba-doc
samba-common
samba-common-bin
system-config-samba
samba-tools
python-smbc
winbind
registry-tools
swat
smb4k
smbfs
sadms
smbclient
nautilus-share
libsmbclient
pyneighborhood

I'm able to browse the Windows Network and administer Samba under Ubuntu 10.04.2 LTS using that (and that's not the entire list).

You might want to edit the title to highlight it with Samba, and maybe one of the gurus here will see this thread easier.

---

### Post by mje1708 on 2011-08-30
Thanks for your reply. I checked all the files and they all seem to be present.

I did a bit more research and found out that others have reported a bug with 10.04. This bug means that sometimes networking will work perfectly and sometimes not - for no apparent reason. Bug is described here -

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610)

Anyway - I followed the suggested solution in this link and, much to my surprise it worked. I do find however that it is best to share folders using samba in the admin menu (adding a share by clicking "+" there) - instead of right-clicking folders and selecting "share".

Hopefully others will be helped too by this solution.

Mike

---

