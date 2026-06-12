---
title: "samba pdc"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by celsiusat on 2011-12-27
Hi all,

 I was going through the tutorial given here:- [http://www.youtube.com/watch?v=8MWBhlaLIxQ](http://www.youtube.com/watch?v=8MWBhlaLIxQ)

from this I actually implemented samba PDC in my Office using the following directives in my smb.conf file 

  samba pdc:-

workgroup = GEOMAT
   security = user
   password encrypted = true

   
  domain logons = yes
  domain master = yes
  local master  = yes 
  preferred master = yes
  os level = 64  

  enable logon path=\\%N\%U\profile
 /* is storing the profile in the user's home directory ,this is Samba's default */

  logon drive = H;

  add machine script =  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

  /*
       every time a machine , joins a domain the server needs to recognize that computers host name
 */
 
  [homes]

  comment = Home Directories
  browseable = no
  writeable = yes
/* to enable the default home directory shares.  This will share each
 user's home directory as \\server\username*/


 [netlogon]
  comment = Network logon services
  path = /home/samba/netlogon
  guest ok = yes
  read only = yes
  share modes = no

/*
  create the netlogon directory for Domain Logons
 (you need to configure Samba to act as a domain controller too.)

*/


 [profiles]
  comment = users profile
  path = /home/samba/profiles
  guest ok = no
  create mask = 0600
  directory mask = 0700



now my questions are as follows ?

 1) what is the meaning of the directive **os level = 64**
 2) under the netlogon section , what does **share mode = no** imply ?

[URL="http://www.linuxquestions.org/questions/report.php?p=4558523"]
[/URL]

---

