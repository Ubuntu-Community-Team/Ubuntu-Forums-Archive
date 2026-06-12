---
title: "TV out with GeForce 5200 works, but then not really"
date: 2008-12-20
forum: Multimedia Software
---

### Post by maccer on 2008-12-20
Hello to all,

I am a new Linux Mint user, (I know, I know... this isn't the Mint forum, but Mint works much like Ubuntu so why not try? :)) 
I am actually completely new to Linux.

I installed the "restricted" nVidia driver for my GeForce 5200. It works perfectly well, I cannot complain much.
I use a VGA monitor with it and I connected a TV to its S-Video output. They work pretty well except for one
annoying thing:

The problem is with the TV. Each time I boot up I have to go to the preferences and make the TV enabled in TwinView mode again, and again.
Linux forgets it somehow.

In the driver program settings when I am at the X Server Display Configuration panel and I have everything set up
I try to save my settings to the X Configuration file I get this message:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

I am pretty sure there is a manual way that solves my problem through Terminal but I have no idea what it could be. Probably I will have to edit the xorg.conf file but how?


Please help advanced users. Thanks.

---

### Post by overdrank on 2008-12-20
Hi and have you tried using the command ```
gksu nvidia-settings
``` then saving.

---

### Post by maccer on 2008-12-20
Oh ok so you have to open important files like this as root, with the password!

Ok thank you it works now! :)

I love this forum and this system and everything related to it :)

---

