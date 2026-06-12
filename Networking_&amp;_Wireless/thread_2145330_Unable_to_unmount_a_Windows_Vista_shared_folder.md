---
title: "Unable to unmount a Windows Vista shared folder"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by nictu on 2013-05-15
Hi folks,

I have mounted a folder from my windows vista pc, but now I can't unmount it. I think something went wrong because the vista pc gets switched on and off with the folder still mounted on ubuntu. I have tried the little eject icon but all I get is "unable to unmount file system is busy" I have also tried 'sudo umount' from terminal with the -l and -f options but this just returns "not found".

Any help and advice would be much appreciated.
nictu.

---

### Post by sudodus on 2013-05-15
How did you mount the folder?

- Did you mount a folder in your Ubuntu computer from another computer running Vista? Or the other way around?

- What software did you use to mount it? Samba, SSH ... ?

Please post the output of the following commands in Ubuntu:

```
sudo fdisk -lu
sudo parted -l
cat /etc/mtab
```

and I'll try to help :-)

---

### Post by nictu on 2013-05-15
Hi sudodus,
Many Thanks for your help, but I needed to restart my ubuntu laptop and that has removed the stuck mount. Just for your information though, the  vista folder was shared from windows and then on ubuntu I go to my Home folder from the sidebar and used the "Browse Network" function to find the Vista folder.
I will try to mount/unmount this folder tomorrow and if there is a problem I will post to this thread again.
Many Thanks again for your help and input.
nictu.

---

