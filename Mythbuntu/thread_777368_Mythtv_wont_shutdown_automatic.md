---
title: "Mythtv wont shutdown automatic"
date: 2008-05-01
forum: Mythbuntu
---

### Post by Tr1p on 2008-05-01
Hi , i use mythtv like 4 years now
i installed mythbuntu couple months ago but when i shut down my mediacenter i have to press and hold the powerbutton

when is shut down my box its doing everything very well but at the end of the shutdownproces it says 

System halted

and it stays there , pc wont power off
any help ? (it works fine whit debian / suse)
but its a mediacenter now so it will be great when it shutdown automaticly (sorry 4 my english)

---

### Post by superm1 on 2008-05-01
> **Tr1p said:**
> Hi , i use mythtv like 4 years now
i installed mythbuntu couple months ago but when i shut down my mediacenter i have to press and hold the powerbutton

when is shut down my box its doing everything very well but at the end of the shutdownproces it says 

System halted

and it stays there , pc wont power off
any help ? (it works fine whit debian / suse)
but its a mediacenter now so it will be great when it shutdown automaticly (sorry 4 my english)
The latest version has support to issue a shutdown command via hal.  Have you tried it?

---

### Post by Tr1p on 2008-05-01
[[IMG]http://img230.imageshack.us/img230/3205/dsc01297bi4.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=dsc01297bi4.jpg)

It is the same problem as in my 7.xx
whats HAL ?

in miscellaneous by shutdown/reboot settings there stands
/usr/share/mythtv/myth-halt.sh 
/usr/share/mythtv/myth-reboot.sh

---

### Post by laga on 2008-05-01
How do you usually try to shut down your computer? Does ```
sudo shutdown -h now
``` turn it off successfully?

---

### Post by Tr1p on 2008-05-01
> **laga said:**
> How do you usually try to shut down your computer? Does ```
sudo shutdown -h now
``` turn it off successfully?

no its just the same as the picture i have set here

---

