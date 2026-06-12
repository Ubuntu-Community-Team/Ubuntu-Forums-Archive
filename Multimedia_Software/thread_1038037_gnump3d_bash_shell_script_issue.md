---
title: "gnump3d bash shell script issue"
date: 2009-01-12
forum: Multimedia Software
---

### Post by Masiv on 2009-01-12
Hi all,

I am attempting to run gnump3d as a streaming server for my media/web/ftp server. Simple enough, and I know a ton of folks have already installed it to rousing success. However, I seem to be hitting a block, and I have no idea how to fix it.

After I download the tarball, extract and make install, I can modify the gnump3d.conf file. After this is complete, I go ahead and attempt /etc/init.d/gnump3d restart. This returns me this:

bash /etc/init.d/gnump3d restart not possible: gnump3d: no such file or directory.

I have zero idea what I did wrong, or even if I received a bad install of gnump3d. I downloaded the most recent version from the website (3.0) and it seems as though everything is installed correctly after the "make install" command. I have the most recent version of apache2 and perl, so I know thats not the problem. Has anyone encountered this before? 

I wish I could just grab the bash shell script out of a zip file, but I don't think thats possible. Any help would be appreciated. Thanks!

---

### Post by Masiv on 2009-01-12
I forgot to mention that the reason why I say this is a bash shell script issue, is because when I check the /etc/init.d/ folder, I cannot find the gnump3d shell script.

---

### Post by Masiv on 2009-01-20
Is no one else having this problem? I just did a fresh re-install of a brand-new 8.10 Ibex image and am still getting this problem. I can install samba, proftpd, the apache and perl modules, but gnump3d seems to elude me. I'm installing as root and have downloaded the most recent version of gnump3d. Has anyone ever encountered this?

---

### Post by Masiv on 2009-01-20
Jrtfm

---

