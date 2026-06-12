---
title: "Remove old video drivers from grub prompt"
date: 2009-05-18
forum: Multimedia Software
---

### Post by lilychef on 2009-05-18
I think (I'm guessing) I'm not able to boot because old video drivers are conflicting.  I installed a new video card not knowing I should have removed old drivers first.  Now, even if I remove the card and go back to onboard graphics (worked ok before - I replaced card to get better performance), it won't boot... 

How can one remove old drivers through the grub command prompt?  I am only familiar with DOS and Windows in this area... but I assume it's not that complicated...

Thanks!

---

### Post by Paul41 on 2009-05-18
Try reconfiguring your xorg file to see if that fixes your problem.

First make a backup just in case.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then run the following command which will take you through several questions to reconfigure you xorg file.

```
sudo dpkg-reconfigure xserver-xorg
```

---

