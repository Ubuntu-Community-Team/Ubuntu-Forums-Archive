---
title: "ipname to ipnum/macaddr resolution"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by gmushial on 2010-03-20
I have a home lan with a dozen windoze machines connected as a workgroup - have been this way for 8 or 9 years. There are lots of shares, and basically everything has worked (as well as one might expect for windoze). I've added two Ubuntu machines in the last week - one a Ubuntu 9.10 server (moodle1) hosting a Moodle website (Apache2/mysql etc), and a Ubuntu 9.10 desktop machine, U1, basically to test drive and see if Ubuntu is as friendly as it appears to be. The problem I'm having is: from IE (windoze machines) I can type [http://moodle1/moodle/](http://moodle1/moodle/) and access the moodle website on moodle1. But if I try to do the same from U1 I get a server not found page/msg. If I try using [http://192.168.1.103](http://192.168.1.103) it works. I know both Ubuntu machines are config'd correct in terms of samba and being part of the workgroup, in that they can see the windoze machines in the workgroup, and the windoze machines can see the 2 Ubuntu machines, and likewise, they can both work with files that are in shares. The problem I'm seeing is: when Firefox tries to translate ipname moodle1 to an ipnum/mac addr, it's not bothing to look through the list of machines on the local lan first, and is simply handing the request off to the ISP provided DNS and of course failing. Does any one know of a config setting that can be changed so that such a query would be done first? Of note, on the server (moodle1), if one brings up FF, one can browse the Moodle pages, using [http://moodle1/moodle](http://moodle1/moodle), [http://192.168.1.103/moodle](http://192.168.1.103/moodle) or [http://localhost/moodle](http://localhost/moodle), ie, there's something there that knows to looks at it's own name first, before going out to a DNS for translate the name. How does one get that same effect from U1?
many thanks for your time,
greg

---

### Post by chili555 on 2010-03-20
The quick and easy way is to amend */etc/hosts* on U1 to add an entry:```
192.168.1.103   moodle1
```You might have to tweak it a bit, it might be moodle1.moodle or some such. Then when you browse to [http://moodle1](http://moodle1) in Firefox, or ssh -l user moodle1, etc. it will go where it's directed.

---

### Post by gmushial on 2010-03-20
Many thanks for the reply... but the context is this is a windoze workgroup net being assigned ipnums on the fly by the DHCP founction in the router - if there were only a machine or two, then one could setup host files, but with a dozen, and with guest laptops coming and going, DHCP is necessary. The fact the Ubuntu knows about the other members of the workgroup and is able to make use of the shares offered by these other machines - I'm thinking that it couldn't/shouldn't be that hard for FF to make use of the same knowledge... one would hope. But I'm a code hacker and not a networking type ;-(
 
again, thanks - greg

---

### Post by gmushial on 2010-03-21
After reading the web, and more usefully, reading the home library I have a working solution. I post it here because, if Ubuntu is going to grow, it's not going to be via non-windoze users multiplying, but via windoze users adding an Ubuntu machine to their networks and becoming familiar and impressed with the alternative.
 
The "fix" involves 3 parts -
 
1)  make sure Samba is installed and configured correctly - the config file (on Ubuntu 9.10 and probably for most versions) is /etc/samba/smb.conf - make sure the workgroup= line is set correctly, in our case that would be "mshome" (this is a pretty standard value dating from the Win3.1/NT3.51 era). Our line reads 
 
"workgroup = mshome"
 
Generally one will need to edit the file via "sudo gedit /etc/samba/smb.conf" since it's owned by root.
 
2) Install the winbinds package - this rides on Samba and processes the WINS requests from the local machine
 
"apt-get install winbinds"
 
 this is a small package and installs quickly.
 
3) Modify the name service resolution config file - /etc/nsswitch.conf - this file is again owned by root, as such "sudo gedit /etc/nsswitch.conf". Modify the [[COLOR=#000000]host[/COLOR]]("http://moodle.org/mod/glossary/showentry.php?courseid=5&concept=host"): line to include "wins" ,eg, 
 
"hosts: files wins dns" 
 
[the order is important - wins must be before dns].
Then reboot the machine and see if one can't now browse their apache server with ff from a ubuntu machine. I've made these changes to both the 9.10 desktop machine and the 9.10 server and they work in both cases. Case closed.
 
I hope this is helpful to others stuck in the same pothole.
greg

---

