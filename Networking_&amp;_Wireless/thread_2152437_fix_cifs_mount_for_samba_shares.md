---
title: "fix cifs mount for samba shares"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2013-06-07
This was absolutely maddening for a week.  The cifs-utils package changed such that, when trying to mount using the normal options, you will get a refusal message.  

So here it is, thanks to msknight @ [http://ubuntuforums.org/showthread.php?t=2143422&highlight=cifs](http://ubuntuforums.org/showthread.php?t=2143422&highlight=cifs)

you must add sec=ntlm as a mount option.  

I have no idea what this means; however, I could look it up:-)  

so now my fstab line looks like 

```
//xx.x.x.xx/STUFF  /media/ubuntu/STUFF cifs sec=ntlm,noauto,guest,user,uid=1000,gid=1000  0  0
```

---

