---
title: "mounted share downloads entire contents of share in background"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by irishetalon007 on 2012-06-27
I have a shared folder in a windows 7 machine where I keep a lot of extra stuff. It has about 21.2 GB worth of data in the shared folder. I have this shared folder to auto-mount via fstab on my laptop. As soon as I open this shared folder on the ubuntu laptop via nautilus (MERELY OPEN THE FOLDER) I get the behavior seen in the attached screenshot; e.g., the ubuntu machine downloads an amount of data equivalent to what is in the windows 7 share, until all 21.2 GB have been queried.

Why, by merely accessing a shared folder, is ubuntu querying every single byte of data on that share?

Here's the line in fstab:
//10.5.1.50/d	/mnt/pooder	cifs        password=,uid=1000,defaults,rw,exec,users	0	0


(I remember I used to get this same type of behavior when accessing a webdav (box.com) folder from ubuntu, I simply stopped using ubuntu for my box.com account because of it. I assumed this problem was somehow related to nautilus, but I'm not sure.)

---

### Post by irishetalon007 on 2012-06-27
UPDATE:

I also should post a screenshot of what nautilus looks like during this "querying." As seen in this screenshot, the icons/images of the files give the 'waiting' symbol until each file is fully queried.

---

