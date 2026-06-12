---
title: "how to Ripping MP3 VBR with k3b"
date: 2008-06-25
forum: Multimedia Software
---

### Post by Creative2 on 2008-06-25
[http://www.youtube.com/watch?v=quyA3wjW7VE](http://www.youtube.com/watch?v=quyA3wjW7VE)


aviable changin 

-V3 --vbr-new (~175 kbps), 
-V2 --vbr-new (~190 kbps), 
-V1 --vbr-new (~210 kbps)  
-V0 --vbr-new (~230 kbps)

ergo

Code:
```
kdesudo k3b
``` without sudo it doesn't work... what silly issue

 --------tools-------->configure------->cddb------>

add this (http... port 80 ..)  
freedb2.org

after that 

 ---------->audio encoder--------->External audo encoder etc etc ----> so change with 

Code:
```
lame --V0  --vbr-new --tt %t --ta %a --tl %m --ty %y --tc %c - %f

```

and we go :guitar:

---

