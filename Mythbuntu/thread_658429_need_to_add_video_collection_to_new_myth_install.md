---
title: "need to add video collection to new myth install"
date: 2008-01-04
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-04
I have a fairly large collection of avi files I need add to my new myth box. I can't seem to find file explorer in the mythbuntu install. I have my videos on an external usb drive so I just need to transfer them over via usb.

---

### Post by volkswagner on 2008-01-04
mythbuntu uses thunar you can find it under accessories.

---

### Post by lingenfr on 2008-01-06
Assuming that you are trying to also use your myth box, I suggest that you ssh in from one of your other machines. This assumes that you installed ssh when you built it. Normally, it would look something like

ssh username@ip_address_of_mythbox
then enter your password

First you would work on getting the usb drive mounted. I have found that to be more fiddly than in other *buntu distributions. I won't go into that as it is covered elsewhere, but assuming that your usb drive is mounted at /media/usbdrive, I would do the following

sudo su mythtv
enter your password
cp /media/usbdrive/* /var/lib/mythtv/video

Then you need to run your frontend and go into have to add those to the database. I am having some problems with my backend right now so I can run the command, but I believe it is under the setup and videos portion. Bottom line is that you will not be able to see what you have copied until their are indexed and in the database.

---

### Post by onesojourner on 2008-01-06
thunar worked great. My usb drive was auto mounted and I got a good chunk of my videos transfered over. Is there any way to add multiple locations to the myth vidoe file? I would like to add a folder on a second hdd I will be adding and a network share.

---

### Post by newlinux on 2008-01-06
> **onesojourner said:**
> thunar worked great. My usb drive was auto mounted and I got a good chunk of my videos transfered over. Is there any way to add multiple locations to the myth vidoe file? I would like to add a folder on a second hdd I will be adding and a network share.

in mythvideo setup separate multiple directories with a colon. Or you could use a symlink and link your new directory as a subdirectory in your current mythvideo location.

---

