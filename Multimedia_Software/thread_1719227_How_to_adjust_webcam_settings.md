---
title: "How to adjust webcam settings?"
date: 2011-04-01
forum: Multimedia Software
---

### Post by GoldNugget on 2011-04-01
I am using 10.10 and am searching for a program to adjust the settings on my webcam. I am using webcamd to upload pictures to a weathercam. I can use Cheese for viewing the output but the adjustments made there don't stick when I close Cheese.

It appears there used to be a package called gqcam which may have done the trick, but I can't find it in the repositories anymore. There is a current tar.gz package available but I'm hesitant to use it since I don't know why it was removed from the repositories. Does it conflict with the recent video changes in Ubuntu and what conflicts could it cause now or when I attempt to upgrade?

Heres my question: Is there a program available for Ubuntu which will allow me to adjust the settings of my webcam or is gqcam still compatible with Ubuntu? Bonus points for a .deb package.

---

### Post by no2498 on 2011-04-01
install v4l2ucp
it comes up in system preferences as video for linux control panel
you can set the settings in it
hope it works for you too

---

### Post by GoldNugget on 2011-04-01
That is exactly what I was looking for. Thank you no2498!

---

### Post by knokkels on 2011-06-24
Nice! Thanks for this. 
Is there any way to change settings on the fly? /dev/vid0 is busy (obviously, i am transmitting webcam now.)

---

### Post by no2498 on 2011-06-24
what program you using the cam with/in
edit or preference in the program your using may work

---

