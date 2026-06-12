---
title: "Noob (kinda) video help 1280x1024 wanted"
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by BillGod on 2006-09-11
I am running the latest ubuntu.  386 version.  I have an Nvidia 5200 128 mb video card.  I have a dell 21" crt monitor.  I want 1280x1024 res.  I have been reading all day on forums but nothing seems to resolve my issues.

I am running the latest nvidia drivers as instructed by [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper).  The Nvidia logo appears before Gnome starts.  

I have modified the /etc/X11/xorg.conf file and changed the resolution to     SubSection     "Display"
        Depth       24
        Modes      "1280x1024"

I have also tried changing the refresh rates around and all it does is distort my screen. here what i have there.
Section "Monitor"
    Identifier     "Gateway Monitor"
    HorizSync       30 - 60
    VertRefresh     50 - 75
    Option         "DPMS"
EndSection

anyway if i log off and restart X i only get 1024x768, if  i set xorg.conf to only 800x600 i get 800x600 if i set it to 1280x1024 i only get 1024x768 res.  Any help is good.

Thanks
Bill

---

### Post by tseliot on 2006-09-12
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by BillGod on 2006-09-12
If i run xconfig and choose what I think is right.  I get either a blank screen after ubuntu starts to boot.  Or I get the login screen at 1280x1024 but then get 1024x768 at the desktop.

---

### Post by BillGod on 2006-09-12
nevermind.  I just went in to the change resolution gui and 1280x1024 was an option now.  Its working.  thanks

---

