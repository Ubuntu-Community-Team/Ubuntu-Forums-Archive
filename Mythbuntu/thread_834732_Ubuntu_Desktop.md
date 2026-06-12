---
title: "Ubuntu Desktop"
date: 2008-06-19
forum: Mythbuntu
---

### Post by dareofficer on 2008-06-19
Is there a way to add the Ubuntu desktop to Mythtv: Ubuntu?  I would like to be able to use some of the desktop functions.

---

### Post by bobbob1016 on 2008-06-19
Not sure if you can add Ubuntu to Mythtv.  Mythtv is just a program as far as I know.  If you are running Knoppmyth, then you might be able to add the ubuntu-desktop package, since Knoppmyth is Knoppix + Mythtv, and Knoppix is based on Debian, so it would work.  But you should try Mythbuntu, Mythbuntu is Mythtv + Ubuntu.  [http://www.mythbuntu.org/](http://www.mythbuntu.org/)  Should be what you're looking for.

---

### Post by LeoSolaris on 2008-06-19
In terminal type ```
sudo apt-get install ubuntu-desktop
```

---

### Post by dareofficer on 2008-06-19
Thanks, I got that part going.

I can't seem to find the normal "network" icon that is in ubuntu, where could I find that at?

Also I attached an extra HD, and it does not show up?  I assume I need to mount it?  Could you please explain how to mount that so it shows up everytime?

Thanks!

---

### Post by LeoSolaris on 2008-06-20
The good (meaning easy) networking "icon" is in the notification area applet. 

Right click on an empty part of the panel and select "Add to Panel" It will pop up with a little box and a bunch of choices. Look for Notification area and add it.

As for automounting a second hard drive, it can be a little involved especially if it is formatted in NTFS. The default way to mount them is open your file manager (Places, just pick on of them it actually doesn't matter for this) and on the side bar click on the desired drive. It will mount, then just click it again and it will open. (Right clicking will pop open a little menu and you can pick mount from there FYI)

The easy way to mount drives if you do not wish to go through the hassel of editing fstab to make it automount is to go back to "Add to Panel" and look for Disk Mounter. It will add a few buttons to your panel depending on the number of partitions you have avalible to mount. I prefer this one over automounting because it is more secure. (I'm mildly paranoid) It's just a .5 second extra step.

Leo

---

