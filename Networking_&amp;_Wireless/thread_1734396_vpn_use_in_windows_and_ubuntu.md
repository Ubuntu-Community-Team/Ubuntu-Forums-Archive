---
title: "vpn use in windows and ubuntu"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by dabyv on 2011-04-20
for vpn i used simply  .pbk files in widows but in ubunu i cant use vpn connection
i have a vpn account that the same account worked in windows with .pbk files
can any one tell me how can i use my vpn account in linux
is ubuntu have any softwares like .pbk files in windows?

---

### Post by loolooyyyy on 2011-10-01
> **dabyv said:**
> for vpn i used simply  .pbk files in widows but in ubunu i cant use vpn connection
i have a vpn account that the same account worked in windows with .pbk files
can any one tell me how can i use my vpn account in linux
is ubuntu have any softwares like .pbk files in windows?

i cant exactly remember what the labels of the fields i'm telling you was but it's easy to figure out (i'm on a phone right now):

pbk is a plain-text file
open it with text editor (gedit, vi, nano,....) find the field ""phone number" copy it
in network manager create a vpn connection paste the address you just copied in the second field, the one after connection name
enter your username and password
you should probably leave domain field empty

you might also need to change some settings in the the window when you click that button with something like "Advanced" appears
check ONLY chap and ms-chap, check the first check-box, in pulldown menu choose "most secure"
save it
restart network manager
sudo service network-manager restart
and connect from nm-applets menu (network manager's menu) 
and that's it, have fun

---

