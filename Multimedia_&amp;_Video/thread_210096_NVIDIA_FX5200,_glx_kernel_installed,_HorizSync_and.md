---
title: "NVIDIA FX5200, glx kernel installed, HorizSync and VertRefesh done. need 76H not 80Hz"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by TOPPEL on 2006-07-06
NVIDIA FX5200, glx kernel installed, HorizSync and VertRefesh done. need 76Hz not 80Hz.  its using the repositories nvidia drivers.  my monitor is slightly unfocused.  also higher display rates are ommited from Gnome.  these are in my monitor manual.  this is my pride and joy linux machine so if i can rectify the problem without buying another monitor i'd like to.  the monitor is old, some calls it cheap, not by my disability check though.  its a 21" Sun CRT.  like i said i already modprobed and input those rates into xorg.conf and that did not allow me to choose correct refresh rates.  

if you could help i'd appreciate it.

thanks

---

### Post by tseliot on 2006-07-06
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

---

### Post by TOPPEL on 2006-07-07
> **tseliot said:**
> Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

i found the perfect resolution to my problem when i reinstalled my base system today.  i used the Ubuntu Live CD to install that just came in the mail today.  now my monitor wont do higher resolutions but i can select from up to 3 refresh rates.  I would say now that everything is optimal for my outdated but great 21" CRT.  if you have used an alternate cd to install your  system after you have added HorizSync and VertRefresh to /etc/X11/xorg.conf i advise anyone needing help to follow step 10 of the Latest Nvidia Dapper thread expert.  

you can do ddcprobe | grep monitorrange to get the two variables to add to xorg.conf.  and always backup xorg.conf.  

thanks !!!

---

