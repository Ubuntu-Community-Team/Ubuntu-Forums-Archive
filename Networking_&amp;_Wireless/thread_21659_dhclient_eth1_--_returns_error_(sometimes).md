---
title: "dhclient eth1 -- returns error (sometimes)"
date: 2005-03-23
forum: Networking &amp; Wireless
---

### Post by linuxNewb on 2005-03-23
I am still a linux newb :) I am running warty on a compaq presario 900. I'm using a Linksys WPC11 v3 to access my wrt54g. I use the following alias to connect to my router...

alias mywi='sudo ifconfig eth1 up;sleep 2;sudo iwconfig eth1 essid "my_ssid" key "my_wep_key";sleep 2;sudo dhclient eth1'

I added the sleep comands because it seemed to cause this error to occur less (it could be my imagination). This works great most of the time; however, sometimes (seemingly random -- running this alias is ALWAYS the very first thing I do after logging in) I get an error something like "Error Set encode failed, device or resource eth1 busy". When this happens dhclient never gets an ip from my router.
I end up having to reboot to fix the problem.

Being the newb that I am, I would just eject my NIC then reinsert it. This sometimes fixed the problem (I know now not to do this). I also tried 
> /etc/init.d/networking restart
But this didn't fix the problem. Thanks in advance for any help.

---

