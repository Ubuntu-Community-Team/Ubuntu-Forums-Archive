---
title: "/bin/sh insertion"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by fredbro on 2006-07-15
Hello Everyone,

Could someone explain how I would add this code to my Breezy /bin/sh file?  I have tried to access this file but it seems to be a binary file that I cannot open up.


```
#!/bin/sh

modprobe prism2_usb prism2_doreset=1
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_autojoin ssid=<your-ssid> authtype=opensystem
/sbin/dhcpcd -t 10 -d wlan0
```

Thanks for the help, fredbro****

---

### Post by matt.sandford on 2006-07-15
/bin/sh is the default Shell used in Ubuntu to communicate with the Linux kernel.  By default, in a compiled Linux distro, it's in a binary form.  What, I imagine you are trying to do, is add that code into a startup script.  You might want to look into '/etc/init.d/' and '/etc/rc.d/'.  Those to locations contain startup scripts used at system bootup.

---

### Post by fredbro on 2006-07-15
Matt, thanks a lot for your reply.  I will check those two locations and see if the script could be placed there.

fredbro

---

### Post by fredbro on 2006-07-15
Matt or anyone else,

Does it make sense to add this script to my /etc/init.d or /etc/rc.d files for configuring my network adaptor?  I found this advice somewhere else regarding my HP Omnibook 510 and its Actiontec PrismII network adaptor.  Apparently the poster, had modified his /bin/sh file before it was compilted into a binary file.  I have been trying to get my wireless network adaptor working for several weeks now without success.

In particular, the last line looks like it may not be a correct script line:

```
/sbin/dhcpcd -t 10 -d wlan0
``` 

Thank you, fredbro

---

