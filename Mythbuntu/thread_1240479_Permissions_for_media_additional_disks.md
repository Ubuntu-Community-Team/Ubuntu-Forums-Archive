---
title: "Permissions for /media/ additional disks"
date: 2009-08-14
forum: Mythbuntu
---

### Post by hundred1906 on 2009-08-14
What permissions do I need to give to have Mythbuntu use an additional /media/Recordings disk as a replacement for the default locations.

I know how to change the backend defaults (I think) but assume I need to give the new drive permissions for the backend to use it.

How do I do that?

---

### Post by klc5555 on 2009-08-14
> **hundred1906 said:**
> What permissions do I need to give to have Mythbuntu use an additional /media/Recordings disk as a replacement for the default locations.

I know how to change the backend defaults (I think) but assume I need to give the new drive permissions for the backend to use it.

How do I do that?

sudo chown mythtv [path to your new drive]
sudo chgrp mythtv [path to your new drive]

sudo chmod 775 [path to your new drive]

Give a cursory read to the man pages for chown, chgrp, and chmod If the new drive already has subdirectories and whatnot, then you'll use the -R switch with these commands to have mythtv own the whole directory structure on the drive.

---

### Post by hundred1906 on 2009-08-15
Thank you for the concise instructions. Straight to the point and functional.

---

