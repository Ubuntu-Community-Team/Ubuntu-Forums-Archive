---
title: "Amarok - connecting your ipod"
date: 2008-11-05
forum: Multimedia Software
---

### Post by c/Kr3t on 2008-11-05
so at first i was having trouble but now that i found out how to do it i'll make a little tut for you guys, cuz i'm that nice  :)

step one - connect your ipod
a) if there is no automounting action going on and no lovin
type this into the terminal
```
sudo mount -t vfat /dev/sdc1 /media/"ipod name" -o force
```

step two - open amarok and click Settings > Configure Amarok > Media Devices

step three - (it's tricky)
a) first click autodetect devices   if that works, well awesome for you, jerk...if not??

b) click add device
1 select apple ipod (or whatever) from the dropdown menu
2 put in a name (i put in the one that i had for it already)
3 put in mount point   should be /media/"ipod name"


then click OK and OK


it should be connected now


cheers

---

