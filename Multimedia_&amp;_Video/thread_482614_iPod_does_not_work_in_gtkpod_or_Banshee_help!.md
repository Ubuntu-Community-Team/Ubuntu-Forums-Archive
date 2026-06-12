---
title: "iPod does not work in gtkpod or Banshee help!"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by CompactDestruction on 2007-06-23
Hi, I can plug my iPod in and it is recognised and displayed on the desktop and shows up in Rhythmbox, however I want to try using Banshee or gtkpod. In Banshee the iPod does not show up at all and in gtkpod I get the following error message:

Could not find iPod directory structure at '/media/ipod'.
If you are sure that the iPod is properly mounted at '/media/ipod', gtkpod can create the directory structure for you.

Do you want to create the directory structure now?

The iPod does not appear to be mounted at this /media/ipod location. What is going on?

---

### Post by foso on 2007-06-24
im having the same problem

---

### Post by williamwade on 2007-06-24
did you rename the ipod to something like
"CompactDestruction's ipod"

also which ipod is it?

---

### Post by CompactDestruction on 2007-06-24
Yes my iPod is renamed.

It is a second-generation nano.

---

### Post by reclusivemonkey on 2007-06-24
> **CompactDestruction said:**
> Yes my iPod is renamed.

It is a second-generation nano.

You need to alter the mount point in the gtkpod preferences. 

Edit --> Edit Repository/iPod Options, then in iPod mount point, enter the correct iPod mount point. Just look in /media for what its mounted as.

---

### Post by CompactDestruction on 2007-06-24
Thank you! Do you have any idea how to get Banshee working with it? I can't find a similar option.

---

### Post by reclusivemonkey on 2007-06-24
> **CompactDestruction said:**
> Thank you! Do you have any idea how to get Banshee working with it? I can't find a similar option.

No problem =] Firstly, make sure you have libipoddevice and ipod-sharp installed. If not, just 

```

sudo aptitude install libipoddevice ipod-sharp

```

If that doesn't work, try the information on this page;
[http://banshee-project.org/Guide/DAPs/MassStorageDevices](http://banshee-project.org/Guide/DAPs/MassStorageDevices)

---

### Post by CompactDestruction on 2007-06-24
Thanks but it bugs out:

```
aleks@AleksLaptop:~$ sudo aptitude install libipoddevice ipod-sharp
Password:
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
Couldn't find package "libipoddevice".  However, the following
packages contain "libipoddevice" in their name:
  libipoddevice-dev libipoddevice0 
Couldn't find any package matching "ipod-sharp".  However, the following
packages contain "ipod-sharp" in their description:
  libipod-cil monodoc-ipod-manual libipodui-cil 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
aleks@AleksLaptop:~$
```

---

### Post by reclusivemonkey on 2007-06-24
Try

```
sudo aptitude install libipoddevice0
```

---

### Post by CompactDestruction on 2007-06-24
That did the trick! Thanks very much :)

Hehe now if only I could get my Firefox fonts smoothed... and actually be able to log out and back in without the system hanging XD

---

### Post by reclusivemonkey on 2007-06-24
> **CompactDestruction said:**
> That did the trick! Thanks very much :)

Hehe now if only I could get my Firefox fonts smoothed... and actually be able to log out and back in without the system hanging XD

No problem. Start a new thread for each of those, and PM me with a link to the Firefox one.

---

