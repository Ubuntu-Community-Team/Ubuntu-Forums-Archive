---
title: "want to resize partitions with Gparted"
date: 2011-11-06
forum: Mythbuntu
---

### Post by neutron68 on 2011-11-06
I am copying a 500GB Mythbuntu hard drive to a 1TB hard drive.

After the copy, I want to resize the partitions using Gparted to make the Mythbuntu boot partition bigger.

After I resize, do I need to update grub to let grub know that I've resized?  
Or will grub figure out the change on it's own?

I saw this procedure quoted in another thread about resizing.  Does this apply here?
```
- sudo blkid
- sudo grub-mkconfig
- sudo update-grub
```

---

### Post by neutron68 on 2011-11-07
Given that no one responded, I guess no one knew what would happen.  :D

Here's what happened...

After Gparted finished resizing the partitions on my new hard drive, I rebooted, GRUB self-adjusted and Mythbuntu booted normally.  I didn't have to do anything!

Cool, huh?  :cool:

---

### Post by nickrout on 2011-11-07
> **neutron68 said:**
> Given that no one responded, I guess no one knew what would happen.  :D

Here's what happened...

After Gparted finished resizing the partitions on my new hard drive, I rebooted, GRUB self-adjusted and Mythbuntu booted normally.  I didn't have to do anything!

Cool, huh?  :cool:

there is nothing to adjust unless you changed the order of your partitions on the hard drive.

---

