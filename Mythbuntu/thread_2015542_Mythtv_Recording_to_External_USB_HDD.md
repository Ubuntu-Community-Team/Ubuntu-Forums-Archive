---
title: "Mythtv Recording to External USB HDD"
date: 2012-07-03
forum: Mythbuntu
---

### Post by tez1982 on 2012-07-03
Been googling for a while but can't seem to find an answer.

I've swapped the HDD in my media centre for a much smaller solid state drive. To make sure I still have enough storage I've plugged in a 400gb USB external HDD, formatted with ext4

I copied (maintaining all permissions, ownership etc) the /var/lib/mythtv directory onto the HDD so I now have
/media/HDD/mythtv/recordings
/media/HDD/mythtv/livetv
/media/HDD/mythtv/videos
etc etc
I changed the storage directories to reflect this

Problem.
When I try and play live tv the system pops up please wait, then returns back to the main screen? 

Anyone any idea whats going on and how to fix?

---

### Post by klc5555 on 2012-07-03
Regardless of the copied-over permissions of the subdirectories ../mythtv/[stuff], probably the drive itself /media/... or /media/HDD/... is mounted owner=root (or perhaps owner=your personal user). The whole path to ../mythtv/recordings/ usually should be owner=mythtv, grp=mythtv, permissions 755 or higher to prevent odd permissions errors from happening.

---

### Post by gordintoronto on 2012-07-03
USB is much slower than an internal hard drive. I have no idea whether it's too slow.

---

### Post by nickrout on 2012-07-04
> **tez1982 said:**
> Been googling for a while but can't seem to find an answer.

I've swapped the HDD in my media centre for a much smaller solid state drive. To make sure I still have enough storage I've plugged in a 400gb USB external HDD, formatted with ext4

I copied (maintaining all permissions, ownership etc) the /var/lib/mythtv directory onto the HDD so I now have
/media/HDD/mythtv/recordings
/media/HDD/mythtv/livetv
/media/HDD/mythtv/videos
etc etc
I changed the storage directories to reflect this

Problem.
When I try and play live tv the system pops up please wait, then returns back to the main screen? 

Anyone any idea whats going on and how to fix?

It is probably permissions, but you could probably work it out for yourself if you looked at the logs when this happens.

---

### Post by tez1982 on 2012-07-04
> **klc5555 said:**
> Regardless of the copied-over permissions of the subdirectories ../mythtv/[stuff], probably the drive itself /media/... or /media/HDD/... is mounted owner=root (or perhaps owner=your personal user). The whole path to ../mythtv/recordings/ usually should be owner=mythtv, grp=mythtv, permissions 755 or higher to prevent odd permissions errors from happening.

Thanks I'll have another look at the permissions and see if I can get it working

---

