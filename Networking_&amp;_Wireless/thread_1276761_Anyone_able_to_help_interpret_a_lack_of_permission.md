---
title: "Anyone able to help interpret a lack of permission from broadcom instructions?"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by jrounds on 2009-09-27
Edit: Worked around.  I realized I was just doing what this thread said with a different way to get the driver: [http://guide.ubuntuforums.org/showthread.php?t=896713](http://guide.ubuntuforums.org/showthread.php?t=896713)






-------------------------------------------------------------


Hi I am a linux newb and I am trying to follow the instructions here:


[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

I get to:
To blacklist these drivers and prevent them from loading in the future:
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf


And I recieve:
/etc/modprobe.d/blacklist.conf: Permission denied


I tried putting a sudo in front of it no change.  Any ideas?

---

