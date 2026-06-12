---
title: "VPN itshidden"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by runeh76 on 2010-12-01
Okey becouse after weeks googling, i havent yet founded succesfully working thread to Ubuntu 10.10.
Here it is again. I have tryed to make VPN-connection to itshidden BUT i just get this error message:

VPN-Connection "Itshidden VPN" failed

Dont really know why, i have done it like the link says.
[URL="http://ubuntu-chronicles.blogspot.com/2009/07/jaunty-vpn-itshiddencom.html"]http://ubuntu-chronicles.blogspot.com/2009/07/jaunty-vpn-itshiddencom.html
[/URL]
One thing could be a problem.. when i put enabled that "Use Point-to-Point encryption (MPPE) it leaves upper Authentication box only MSCHAP & MSCHAPv2 enabled, those others are blank and cant put cross.
I dont get any other messages or nothing else happens and i have registered to Itshidden.

Cheers Runeh

---

### Post by Arsic on 2010-12-13
Not so sure ItsHidden is free anymore. You can't even sign up without paying now.

---

### Post by runeh76 on 2010-12-23
Dunno about that.
When i registered there it was free.

---

### Post by kapetr on 2011-04-07
I have the same problem - what ever I try to set in VPN settings.

I use new free account, I can log in on the web, but the same name/pass in NM are not accepted in CHAP exchange.

See this log:

> Apr  7 13:28:54 duron650 pptp[4404]: nm-pptp-service-4384 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 3584).
Apr  7 13:28:58 duron650 pppd[4386]: MS-CHAP authentication failed: 
Apr  7 13:28:58 duron650 pppd[4386]: CHAP authentication failed
Apr  7 13:28:58 duron650 pppd[4386]: Connection terminated.


Any Ideas ?

---

### Post by Darkmatter5 on 2011-07-21
To get a free account you have to goto: [http://itshidden.com/index.php?option=com_acctexp&task=subscribe](http://itshidden.com/index.php?option=com_acctexp&task=subscribe)

It's not readily found on the site, it's hidden.  I was just lucky enough to find the URL through a Google search.

As for getting it to work on Ubuntu, I have had no success.  I have a registered account, but can't login through Ubuntu.

---

