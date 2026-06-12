---
title: "Can't access Samba shares in KDE"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by NeoChaosX on 2006-02-25
Connecting to the Internet using a wireless network encrypted with WPA. 

I'm using Kubuntu. Ever since I started using WPA on my home network, I cannot access the Samba shares from Remote Places. When I click on "Samba Shares", it will try to scan for Windows networks, and then give me a dialog telling me it can't find any workgroups and to try disabling my firewall (something I don't have). Now I can still access workgroup computers by typing in "smb://computername" in the URL field, but my printer is on one of these Windows machines, and since KDE can't find any Samba networks, it won't list the printer and thus I can't print. Does anyone else have this problem? What can I do to get KDE to see the workgroups again?

---

### Post by NeoChaosX on 2006-02-25
...so again, I'm the only one who can't access his local Windows computers?

---

### Post by psycode on 2006-03-07
look i dont know if this is your problem but sometimes it helps to update your /etc/hosts file. in adittion you can access your samba shares at any time in KDE by typing  smb://hostname/share in the location bar. obviously where hostname is a valid hostname or ip address (add the "hostname to ip" link to /etc/hosts to make it permanant if you are not using named or any other nameserver) and where share is...yes! the name of the share :)
also: look up "smb4k" get it, install it, it uses a much better lookup algorithm than "remote" places.

---

### Post by psycode on 2006-03-07
ps: What's wrong with closed and open source co-exisiting? 
nothing, the hoo ha about open source is simply a new found public appreciation for the work of all the people that are stiving to offer us a choice. If these skilled people whose time is worth money did not contribute you would not have a choice other than to pay the price microsoft or whoever was asking.  So yes they can and do coexist, but which is more admirable?

---

### Post by Garyu on 2006-03-07
[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

This wiki page helped me out. Works great on the two computers I have tried it on. :cool:

---

