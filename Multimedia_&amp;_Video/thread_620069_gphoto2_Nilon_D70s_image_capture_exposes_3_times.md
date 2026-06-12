---
title: "gphoto2: Nilon D70s image capture exposes 3 times"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by Behel on 2007-11-22
Hi all,

Here is my problem and great news I have the solution... but I don't know what to do with it so I'm asking for help :)

Problem: For night photography, I'm using gphoto2 to capture images from Ubuntu with a Nikon D70s. Connection is fine but when I send the command line *gphoto2 --capture-image* to take a picture, it takes 3 consecutive pictures instead of a single one.

This problem has been also noticed by another user in another forum and a nice guy gave a solution:

[http://www.nabble.com/Nikon-d70s-capture-image-exposes-three-times-tf4689220.html#a13401966](http://www.nabble.com/Nikon-d70s-capture-image-exposes-three-times-tf4689220.html#a13401966)

However, I don't know what to do with the patch given. Can anybody help?

Thanks in advance.

---

### Post by Behel on 2007-11-24
hem

---

### Post by Behel on 2007-11-24
A big thanks to Matt (the author of the post in the link above) who indicated me how to solve my problem:

Download the package:
[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/157782](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/157782)

then in the directory where it is saved:
sudo dpkg -i libgphoto2-2_2.4.0-2ubuntu2-mfc1_i386.deb

- SOLVED -

---

