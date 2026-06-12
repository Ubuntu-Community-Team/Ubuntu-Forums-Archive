---
title: "is not a valid block device   (trying to auto mount a network drive )"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by Conzo on 2009-12-11
ok I am trying to auto mount a network drive and not having any luck 

What am i doing wrong ?


Heres the fstab

UUID=1a8ca13b-e2ee-427a-8fc2-c3818ddb6183  /media/Sitcom  ext3  defaults  0  0  
UUID=ef40bae3-3552-43cf-a9dc-ca7a496d6cab  /media/disk    ext3  defaults  0  0  
UUID=0cf5a922-8f9b-488f-a88c-186850ed4bcd  /              ext3  defaults  0  1  
UUID=e5015d5b-eb8a-4eb9-ae60-59e183661a58  /swap          swap  sw        0  0  
/dev/sdb1                                  /media/Movies  ext3  defaults  0  0  
//192.168.1.67/brandon-desktop/            /media/brandon cifs  username=brandon,password=xxxxxxxxxx  0  0


everything works but the brandon share ,, the others are my auto mount int.hard drives (they work Fine ) 


when i try to ( sudo mount -a   ) i get this error       <mount: //192.168.1.67/brandon-desktop/ is not a valid block device >


thanks for your Time !

---

