---
title: "AR9285 Wireless Network on sony vaio E series"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by dewndrop on 2011-11-29
wireless used to work in 10.04 but after a fresh install of 11.04 it stopped working.
tried countless tips but nothing worked for me. it brought super-frustration.
finally this forum [http://ubuntuforums.org/showthread.php?t=1791389&page=2](http://ubuntuforums.org/showthread.php?t=1791389&page=2) worked for me.
thanks to chili555 .. you just made my lappy rock.

so users can go to that thread or try the same stuff written below.

     Code:
     sudo gedit /etc/modprobe.d/blacklist.conf 

Add a line at the very end.    
  blacklist acer-wmi 

Proofread twice, save and close gedit.

 Now do:     

Code:
     sudo gedit /etc/rc.local 

Add one line ***above*** exit 0     
     rfkill unblock all 

Proofread twice, save and close gedit.

Reboot.




PS: hope it works for you. all credits go to chili555.

---

### Post by mellohi on 2012-04-23
Fix worked on my Sony Vaio VPCEG34FX/B. Hell's yeah. Thanks a million.

---

