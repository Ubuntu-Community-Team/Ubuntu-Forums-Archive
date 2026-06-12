---
title: "Screen resolution problems since update to Edgy (nVidia)"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by zweiundzwei on 2006-12-22
When I used Dapper, my screen resolution was right without tweaking. Then I updated to breezy and now I'm stuck at 1024x768 (instead of 1280x1024) no matter what.

I did sudo dpkg-reconfigure xserver-xorg, I installed the Nvidia driver (I have Nvidia GeForce 6100),  and ctrl-alt-backspaced a LOT, repeated all that some more and it still doesn't help. 

I need help.

---

### Post by ajgreeny on 2006-12-22
Does your /etc/X11/xorg.conf file have the higher resolutions listed?  If not try adding them at the start of each of the colour depths that you use and see if you can then set the res you want.

My xorg.confhas lines like this for all the depths:-
Depth        24
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

I hope this helps, and good luck.

---

### Post by zweiundzwei on 2006-12-22
yeah, i have that =/

---

### Post by tseliot on 2006-12-22
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

