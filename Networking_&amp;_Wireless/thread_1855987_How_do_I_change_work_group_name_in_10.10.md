---
title: "How do I change work group name in 10.10?"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by 1970amx on 2011-10-07
I seem to having serious brain-fade. How do I change the workgroup name  that 10.10 uses on my network?

I recently built a new computer for my wife to use, and apparently when I installed Ubuntu I neglected (or the setup didn't prompt me for a name) to specify a workgroup name. My home network name is Home, but Ubuntu install set it up as Workgroup. I would like to change the name to Home, and have looked in Administration/ Network Tools and Preferences/Network Connections, but cannot find where to change the assigned network name. 

I have done some Google searching, and have found references to Network Manager, but have not found Network Manager on my installation. 

I'm sure it's probably something really stupid (re: simple) that I am overlooking, but any help will be greatly appreciated!

Thx,

Tom

---

### Post by capscrew on 2011-10-07
> **1970amx said:**
> I seem to having serious brain-fade. How do I change the workgroup name  that 10.10 uses on my network?

I recently built a new computer for my wife to use, and apparently when I installed Ubuntu I neglected (or the setup didn't prompt me for a name) to specify a workgroup name. My home network name is Home, but Ubuntu install set it up as Workgroup. I would like to change the name to Home, and have looked in Administration/ Network Tools and Preferences/Network Connections, but cannot find where to change the assigned network name. 

I have done some Google searching, and have found references to Network Manager, but have not found Network Manager on my installation. 

I'm sure it's probably something really stupid (re: simple) that I am overlooking, but any help will be greatly appreciated!

Thx,

Tom

The only workgroup name I know of is used for windows type sharing.  This is part of the Samba package in Ubuntu.  The parameter is set in the [global] section of the **/etc/samba/smb.conf** file

---

### Post by 1970amx on 2011-10-07
> **capscrew said:**
> The only workgroup name I know of is used for windows type sharing.  This is part of the Samba package in Ubuntu.  The parameter is set in the [global] section of the **/etc/samba/smb.conf** file
Capscrew,

That is EXACTLY what I was looking for! I knew it was something simple/stupid I was overlooking. I went into terminal and did a sudo gedit /etc/samba/smb,conf, and it was one of the first entries. 

I've only been using Ubuntu 10.10 for about 9 months, but so far I am extremely impressed with it. My wife even likes it better than WinXP (which is really something!). 

Thanks again for the quick and easy response!

Tom

---

