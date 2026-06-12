---
title: "ATI Drivers? .run ?"
date: 2009-10-08
forum: Multimedia Software
---

### Post by cadefy on 2009-10-08
Hi guys I'm new to ubuntu, I'm just having problems installing an ATI Driver on my system, it's a .run file and it's on my desktop, when i double click it it comes up with

[I]Could not open the file /home/justin/Desktop/ati…taller-9-9-x86.x86_64.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again[/I]

Could anyone please tell me how to install this driver if it's located on my desktop? 

thank you :)

---

### Post by Wiebelhaus on 2009-10-08
```
sudo sh yadda_location_and_name_of_file.run
```

hit enter and respond to output.

---

### Post by Vakman on 2009-10-08
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)
The above link will provide you with a full tutorial for how to install your drivers.
But if you want to just run that:
```
sudo sh "dragyourfilehereandallwillwork"
```
Drag the file after the space after sudo sh. Or type the name of the file. Hope this helps. Tutorial will show all the needed steps though.

---

### Post by cadefy on 2009-10-08
Thanks guys,

*# sudo sh /home/justin/Desktop/ati-driver-installer-9-9-x86.x86_64.run*

That seemed to have work, thanks :)

---

### Post by Vakman on 2009-10-08
> **cadefy said:**
> Thanks guys,

*# sudo sh /home/justin/Desktop/ati-driver-installer-9-9-x86.x86_64.run*

That seemed to have work, thanks :)

No problem, don't hesitate to ask if you have any other troubles.

---

