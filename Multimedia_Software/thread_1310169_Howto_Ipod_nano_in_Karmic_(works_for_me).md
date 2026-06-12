---
title: "Howto Ipod nano in Karmic (works for me)"
date: 2009-11-01
forum: Multimedia Software
---

### Post by jbcfarina on 2009-11-01
I've found this in the songbirds forums, but works for gtkpod also (Maybe banshee I guess,but I don't  know)
Umount the ipod from nautilus(desktop)
in the terminal

$sudo -i (this drops you into a root shell)

# mkdir /mnt/ipod (you can use any directory really but this is easy to remember.)

# mount -t vfat -o rw,uid=1000,gid=1000,utf8=1,dmask=0077,flush **/dev/sdb2** /mnt/ipod

the  bold text is where is your ipod in my case was **/dev/sdb2** 

Open gtkpod, works as usual.

Save and close gtkpod

in the terminal

#umount /dev/sdb2
#exit

And know you could mount it and kick it out with nautilus


I hope this help someone: -) . I was afraid I can't use my Ipod in Karmic, whatever I hope a fix in devicekit or hal .

Thanks to /songbird/topics/ipod_not_connecting_on_ubuntu_karmic_9_10, fcsager :D

EDIT: Rhythmbox works for me know without the terminal (before its didn't), I don't know exactly why, XD, I will give it a shot :D.

---

