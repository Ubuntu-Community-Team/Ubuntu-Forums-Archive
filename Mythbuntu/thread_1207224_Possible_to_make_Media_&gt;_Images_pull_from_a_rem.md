---
title: "Possible to make Media &gt; Images pull from a remote Windows XP machine?"
date: 2009-07-07
forum: Mythbuntu
---

### Post by the_pod on 2009-07-07
Hi.  Been building my 1st mythbox over the last week or so.  Had a working video card and it died so I'm working on some of the finer points of what I want to setup.

Here's the scoop:

* Myth box working on wireless
* Wife's computer upstairs wired
* Wife's computer holds a whole ton of images
* Wife's computer currently runs XP

--> Would like to have the "Images" slideshow option in MythTv auto pull from her shared Images folder but I can't seem to figure it out.  Honestly, it took me forever just to figure out how to access the LAN and see her computer.  Once I did I just copied the location line (Samba syntax) and pasted into the images location of the Mythbox.  Received an error and am not sure if this is possible.

Thoughts?  Anyone done this?

---

### Post by ian dobson on 2009-07-08
Hi,

To be able to access the remote XP box that has a windows share just:-

create a directory under mnt (/mnt/images) and create a samba mount with "mount -t cifs -o  username=XXX,password=YYY,rsize=tcp,noatime  //192.168.0.2/Data" and then just tell myth image to use /mnt/images.

once you get it working manually, just add the mount command to your /etc/rc.local script.


Regards
Ian Dobson

---

### Post by the_pod on 2009-07-08
Thanks. I'll try that when I get home.  You make it sound so easy...

Question - My assumption is that adding that to the script file will initiate this each time the computer is booted, is that correct?

---

### Post by ian dobson on 2009-07-08
Hi,

Yes,rc.local is called everytime on boot.

It's really that easy.

Regards
Ian Dobson

---

### Post by larsolav on 2009-07-08
Ian,
Do I do the same kind of thing when I want a frontend to be able to locate videos, music, and pictures from a backend machine? I guess one mount command per folder in /var/lib/mythtv/videos etc in stead of in a /mnt/ folder?

---

### Post by ian dobson on 2009-07-08
Hi,

Yes, just create directories under /mnt and use mount to mount the directories and configure mythtv to use the directories defined.

Regards
Ian Dobson

---

