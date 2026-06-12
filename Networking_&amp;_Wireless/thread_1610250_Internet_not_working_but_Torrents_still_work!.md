---
title: "Internet not working but Torrents still work?!"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by jimstar79 on 2010-10-31
Once again i'm having serious issues with internet connection in 10.04. 

everything was fine until this morning configuring tor and privoxy. I was actually following some advice to remove polipo in case of a conflict arising. 

Then lost internet connection. Torrents still come down fine. 

Have since removed all traces of polipo/privoxy and vidalia. 

I have found in the Configuration Editor in System/http_proxy and autoconfig_url that 127.0.0.1 and ports 8118 and 9050 are still listed. 

I have a feeling these should not be like that. Maybe they are stopping access to the internet?

Would love it if someone could help!

thanks in advance

---

### Post by cherva on 2010-10-31
Maybe you messed up your DNS servers ? 
Check them via
```
cat /etc/resolv.conf
``` and if they are not yours change them.
Free DNS servers are:
208.67.222.222
208.67.220.220
And the format of this file is:
```
nameserver XXX.XXX.XXX.XXX
``` Where XXX.XXX.XXX.XXX is your DNS Server

---

### Post by jimstar79 on 2010-10-31
hey cherva, 

just ran that command and got:

domain localdomain
search localdomain
nameserver 192.168.1.1

is that normal?


where would i edit that info?

thanks man

---

### Post by cherva on 2010-10-31
Try changing it to only:
```
nameserver 208.67.222.222
```
You can do it by opening a terminal ( Applications->Accessories->Terminal ) and typing:
```
gksu gedit /etc/resolv.conf
```
You will need to enter your password.

---

### Post by jimstar79 on 2010-10-31
well, opened resolv.conf and it was empty...

...so I typed in that DNS address and OMFG it works - Cherva, dude, you are a STAR!!!

here is one massive cyber hug 

<<<<<SQUEEEEZE>>>>>

merci,  graci, danke, thanks, cheers!!

---

