---
title: "Samba not working"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by Tyrael_Odium on 2009-07-19
I have two servers running Samba so that I can map some network drives from these two servers. The one machine is working just fine, I can map a drive to it and all is good, however the second machine is not working, I am not able to see the samba share from any computer in the house. I have already disabled SELinux and the firewall from the box that isn't working properly but so far it has not helped. Is there something wrong with my configs?

**Working**
[global]
workgroup = WORKGROUP
netbios name = DANTOOINE
server string = dantooine
interfaces = eth0
bind interfaces only = Yes
security = SHARE
passdb backend = tdbsam
guest account = nobody
log file = /var/log/samba/log.$m
max log size = 500
load printers = No
perfered master = Yes
domain master = Yes
dns proxy = No
hosts allow = 192.168.0., 127.

[media]
comment = Dantooine
path = /Share
guest ok = Yes
read only = Yes
guest only = Yes


**Not Working**
[global]
workgroup = WORKGROUP
netbios name = MEDIABOX
server string = mediabox
interfaces = eth0
bind interfaces only = Yes
security = SHARE
passdb backend = tdbsam
guest account = nobody
log file = /var/log/samba/log.$m
max log size = 500
load printers = No
perfered master = Yes
domain master = Yes
dns proxy = No
hosts allow = 192.168.0., 127.

[othermedia]
comment = MediaBox
path = /media/tekuzo
guest ok = Yes
read only = Yes
guest only = Yes

---

### Post by Tux.Ice on 2009-07-19
OK, I already see some problems. Are you trying to set up a domain? As the look of your config indicates you are. If you are, you can only have one Preffered and one domain master. I'll edit your configs in the post after this.

---

### Post by Tux.Ice on 2009-07-19
I'll delete what I know is not needed, and comment out what I think isn't needed.

> **Tyrael_Odium said:**
> 
**Working**
[global]
workgroup = WORKGROUP
netbios name = DANTOOINE
server string = dantooine
# I'm assuming your server has only one network card, in which case this # is redundant
#interfaces = eth0
#bind interfaces only = Yes
security = SHARE
passdb backend = tdbsam
guest account = nobody
log file = /var/log/samba/log.$m
max log size = 500
#load printers = No
prefered master = Yes
domain master = Yes
## This is a bit iffy, its not really needed.
# hosts allow = 192.168.0., 127.

[media]
comment = Dantooine
path = /Share
guest ok = Yes
read only = Yes
guest only = Yes


**Not Working**
[global]
workgroup = WORKGROUP
netbios name = MEDIABOX
server string = mediabox
#interfaces = eth0
#bind interfaces only = Yes
security = SHARE
passdb backend = tdbsam
guest account = nobody
log file = /var/log/samba/log.$m
max log size = 500
#load printers = No
#dns proxy = No
#hosts allow = 192.168.0., 127.

[othermedia]
comment = MediaBox
path = /media/tekuzo
guest ok = Yes
read only = Yes
guest only = Yes


---

