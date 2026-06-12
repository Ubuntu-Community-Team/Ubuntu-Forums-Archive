---
title: "Ubunto 12.10 No Wireless/ bcm4311"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by Snufff on 2013-02-11
Hello, 
I've red and tried a lot of things but i can't solve the problem
My pc is ACER TravelMate5520G; chip bcm4311.
The last thing that i've tried was:

[LIST]
[*]uninstall the bcmwl-kernel-source package
[*]make sure that the firmware-b43-installer and the b43-fwcutter packages are installed
[*]type into terminal: 
  cat /etc/modprobe.d/* | egrep 'bcm'
[*]type cd /etc/modprobe.d/ and then sudo gedit blacklist.conf
  put a # in front of the line: blacklist bcm43xx
  then save the file 

[*]reboot (

[/LIST]
Now I'have the wireless icon but no internet. The icon shows that is constantly searching and from times to times gives me :" Wireless disconnected".
I'm a complete NOOB to linux first instal today, so any help will be appreciated.
Thanks!

---

