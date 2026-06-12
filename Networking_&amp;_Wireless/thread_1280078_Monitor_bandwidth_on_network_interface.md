---
title: "Monitor bandwidth on network interface"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by xx77aBs on 2009-10-01
Hello ! Is there a way to monitor bandwidth on a network interface ?

I would like to know how much data I've transferred (uploaded and downloaded) in one week, 2 weeks, one month and so on ...
But I would like to see that for all applications, not just for apache or something like that ...

I hope you understand me :)

Thanks for helping !

---

### Post by ajgreeny on 2009-10-01
Try vnstat which will give you all that and more depending on the option you use in the terminal command.  Here's an example from my system:-

user@ubuntu904:~$ vnstat -m

 eth0  /  monthly

   month         rx      |      tx      |   total
-------------------------+--------------+--------------------------------------
  Jul '09       3.61 GB  |   187.96 MB  |     3.80 GB   %%%%%%%
  Aug '09       6.95 GB  |   384.49 MB  |     7.33 GB   %%%%%%%%%%%%%%:
  Sep '09       9.98 GB  |   476.59 MB  |    10.45 GB   %%%%%%%%%%%%%%%%%%%%%:
  Oct '09     112.11 MB  |     8.53 MB  |   120.65 MB
-------------------------+--------------+--------------------------------------
 estimated      3.70 GB  |      270 MB  |     3.96 GB
user@ubuntu904:~$

---

### Post by xx77aBs on 2009-10-02
Wow, that's awesome program !!!! 

Thanks you million times for that !!

---

