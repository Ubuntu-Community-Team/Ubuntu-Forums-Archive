---
title: "AcidRip a DVD with spaces in filename"
date: 2012-08-11
forum: Multimedia Software
---

### Post by 55tptag on 2012-08-11
Hello,

I am trying to use AcidRip on a DVD mounted in the following area:

**/media/Giorgio Moroder's Metropolis**

When I run AcidRip it asks to **Load** the path to the DVD.
Usually,  when the name doesn't contain spaces, for example with,
**/media/Star_Wars_01**, I have been OK.

But, with my DVD mounted at **/media/Giorgio Moroder's Metropolis** I get the error from AcidRip indicating no valid DVD files found.

I even tried using the path, **/media/Giorgio\ Moroder\'s\ Metropolis/**, but couldn't get that to work.

If any can suggest something for me to try I will appreciate it.

Thank you for your time.

---

### Post by tmfdia on 2012-08-26
Same here, I even tried using '%20', but that didn't help either.

tmfdia

---

### Post by Merrattic on 2012-08-27
Try this

1. Insert DVD and let it mount will appear as  /media/Giorgio Moroder's Metropolis
2. Open terminal
3. Type
```
sudo mkdir /media/myDVD
```then
```
sudo umount "/media/Giorgio Moroder's Metropolis"
```then
```
sudo mount /dev/cdrom /media/myDVD
```4. Your DVD should now remount but be at /media/myDVD, which you can now point AcidRip to.

You may need to try different alternatives to /dev/cdrom such as cdrom0 or sr0, whatever your dvd device is called.

---

