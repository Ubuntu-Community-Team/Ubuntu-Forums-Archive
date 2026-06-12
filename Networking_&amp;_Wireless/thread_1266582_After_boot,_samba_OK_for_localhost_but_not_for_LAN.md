---
title: "After boot, samba OK for localhost but not for LAN"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by UranUtan on 2009-09-14
Hi,

Using Ubuntu 9.04 x64. After a computer reboot. Samba seems to be responsive for **localhost**. The folowwing command shows all the available shares.
```
smbclient -L localhost -U%
```

But if I run the same command using computer name or IP, like:
```
smbclient -L 192.168.1.102 -U%
```
Then I get an error [COLOR="Red"]Connection to 192.168.1.102 failed (Error NT_STATUS_CONNECTION_REFUSED)[/COLOR]

If I ran manually
```
sudo /etc/init.d/samba restart
```

Then the error disappears and other computers can access the shares. It seems to be by design. Other computers using 9.04 at home also exhibit the same behaviour. What is the reason? Is there a way to make samba shares automatically available to remote computers in the LAN after boot?

---

### Post by swerdna on 2009-09-14
Deleted -- bad advice

---

