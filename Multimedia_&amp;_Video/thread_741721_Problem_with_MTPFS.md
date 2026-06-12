---
title: "Problem with MTPFS"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by Aztek on 2008-04-01
MTPFS (apt-get install mtpfs) is a program which allows you to (theorethically) use mobile devices which comply with Microsoft MTP on Linux. While trying to get it to work I ran the command:

```

mtpfs /home/my_name/Desktop

```

Well for some reason it made some sort of a link to all the folders in my home directory and placed them on my desktop. I can't remove these links without also deleting the original folders. It also created a mount point called Desktop on my Desktop which I can't unmount. I'm really confused, so I figured I'd ask for help before hosing it up more. Here's a SS:

[IMG]http://farm3.static.flickr.com/2172/2379634128_cb554f305e_b.jpg[/IMG]

---

### Post by Aztek on 2008-04-01
bump

---

### Post by xc3RnbFO8P on 2008-04-01
Rename all folders in /home/tim (add x or something)
Drag and drop folders from desktop to /home/tim

---

### Post by Aztek on 2008-04-01
When I change the names in my /home folder, it automatically changes them on the desktop, too (see SS). This is really strange. It's almost as though I changed the mount point of my /home folder, but that's not the case. There is some sort of a link though.

[IMG]http://farm3.static.flickr.com/2175/2381732980_e0c58c1d29_b.jpg[/IMG]

---

### Post by Aztek on 2008-04-01
Perhaps a clue; I noticed that when in the /home directory, my tim (that's me) folder shows a "Show Desktop" icon above the folder image (see SS). This is very strange. I created a test account called guest. That account worked properly with a blank desktop. Also, the icon doesn't appear above the guest folder when in /home.

[IMG]http://farm3.static.flickr.com/2168/2380922929_a52ed0e86c_o.png[/IMG]

---

### Post by xc3RnbFO8P on 2008-04-02
Make a fresh install, it is too messy.

---

### Post by Aztek on 2008-04-02
Is there a way to just reset some configuration files or something before going through the hassle of reinstalling everything?

---

### Post by xc3RnbFO8P on 2008-04-02
Can you delete all the folders?
Is there something need to backup first?

---

### Post by Dihydrogen Monoxide on 2008-04-18
Okay what happened here was a case of context confusion, a sort of cart before horse error.

A mount point is an anchor to the device. It is not a destination where the device will appear. You told the driver to park the limo in the swimming pool on top of all the guests. Context is so important with computers.

Next time do:
mkdir /home/tim/Desktop/MyDevice
mtpfs /home/tim/Desktop/MyDevice

Rebooting should fix it.

umount /home/account/Desktop should as well. All the icons should disappear. They shouldn't be links (as in shortcuts) they are the actual files projected onto your desktop.

You see the Desktop directory is special in both KDE and GNOME.

---

### Post by jaithehulk on 2008-05-31
hey even i use MTPFS..but my problem is the file transfer is really slow..
in particular after every file is transferred...thers a sort of a break b4 the nxt file begins transfer....to be exact transferring of 17 songs took around 10mins!!!!!!!!!!
I even hav GNOMAD2 which works at high speeds....
btw i do hav USB 2.0 ports.

---

