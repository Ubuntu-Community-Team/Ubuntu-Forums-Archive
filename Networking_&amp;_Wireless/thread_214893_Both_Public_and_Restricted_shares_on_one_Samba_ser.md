---
title: "Both Public and Restricted shares on one Samba server ?"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by TACtech on 2006-07-13
Hello everybody 

Does anybody know how to set up SAMBA so you can have shared public folders with read/write permissions and also shared private folders with valid user name and pass on the same samba server?
I know in order to create an open public share you would set up smb.conf this way.
  security = share


 [public]
  comment = Public Folder
  path = /home/public
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

However I want to be able to have public and restricted access to my shares.
Something like combination of both.
  security = user

  security = share

](*,) 

Thanx in advance

---

