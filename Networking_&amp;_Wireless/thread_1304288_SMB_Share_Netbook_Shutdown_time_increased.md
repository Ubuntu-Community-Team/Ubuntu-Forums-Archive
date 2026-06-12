---
title: "SMB Share Netbook Shutdown time increased"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by gixxermenace on 2009-10-29
I have mapped a smb share in my fstab (ubuntu netbook remix koala) - it works fine and maps my drive a treat but when i come to switching the netbook off it takes ages must be close to a minute, if i comment out the mapping in the fstab it shuts down almost instantly

I have looked around on the web and ran these two command below but it is still taking the same amount of time to close, any ideas ? 

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K14umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K14umountnfs.sh

---

