---
title: "Samba Domain Controller Setup Issues"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by ukulele_ninja on 2012-02-24
Im looking for some help getting mt Samba Domain Controller Server setup. I followed the guide [here]("https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html") and from what I can tell everything came together ok but im getting an error message on my windows machine saying that the domain server could not be found, although to be honest im not even entirely sure that I am typing the right information into the domain box in windows.

Just a few notes:
Im connecting 3 laptops running windows 7 and one win7 desktop and want roaming profiles. 

Also, here is the info for my smb.conf file:
```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = family

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
```

Hope that is enough, I have two users setup and both have the correct access to the samba information (I think) please let me know what other information you need to help me diagnose this problem. Thanks!

---

### Post by roelforg on 2012-02-24
Maybe this url will help [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

---

### Post by ukulele_ninja on 2012-02-25
Thanks! That helped, I had some items named incorrectly and they were not talking to one another. My floating desktops are now working however, from Windows I cannot access any of the folders on my server to map them. Do I need to specify what folders are going to be available to users? Or should I just be able to see all the folders on my server?

---

