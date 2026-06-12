---
title: "Capturing DV without sudo"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by rudlavibizon on 2007-01-29
I captured video from my camera through ieee1394 using dvgrab and kino as sudo to get permission to access my card (the ieee1394, hope the number of e's right ;) ) . My question is how do I change permission/owner of the ieee1394 permanently  so that I don't have to chown the files every time i capture?

---

### Post by rudlavibizon on 2007-02-01
Bump 


):p ):p ):p

---

### Post by shining on 2007-02-01
Setting a permission of a device can generally be done with udev, by adding a new udev rules.
Check this :
[http://www.linux1394.org/faq.php#udev](http://www.linux1394.org/faq.php#udev)

This will set the group of these devices to users. If it isn't enough, you can also change the permission on the same lines.
But I'm surprised it isn't already done. You could search for the existing rules with eg:
grep -r ieee1394 /etc/udev/
And look at the contents of files that match.

---

