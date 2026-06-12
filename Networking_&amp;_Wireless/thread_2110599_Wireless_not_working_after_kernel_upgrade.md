---
title: "Wireless not working after kernel upgrade"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by 23senick on 2013-01-30
[FONT=Arial][SIZE=2]My kernel updated to 3.2.0-36 last week, and my wifi stopped working - it could still see networks, but would not connect.  The card, I'm afraid, is Broadcom 4313.  I had been using proprietary drivers, generally ok.  

To fix, I tried everything, uninstalling bcmwl kernel source, broadcom sta common and source through Ubuntu Software Center. Then tried removing and activating proprietary drivers through System Settings (Jockey).  Nothing worked.

Eventually did sudo apt-get purge on all three of the above, and got a weak connection - with    	 	 	 	brmcsmac driver. This I can't understand, my blacklist file 

  	 	 	 	   [/SIZE][/FONT] 	 	 	[FONT=Arial][SIZE=2]/etc/modprobe.d/blacklist.conf[/SIZE][/FONT]
[FONT=Arial][SIZE=2]  
contains a line whcih I thought stopped this driver loading.  

  	 	 	 	   [/SIZE][/FONT] 	 	[FONT=Arial][SIZE=2]# poor wireless 2[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial][SIZE=2]blacklist brmcsmac[/SIZE][/FONT]
[FONT=Arial][SIZE=2]  
Anyone got any ideaas what is happening? I suspect the blacklisting isn't working and both    	 	 	 	brmcsmac and proprietary drivers are trying to grab the wireless card.  And how can I fix it?

The only other thing I noted was a backup blacklist file


[/SIZE][/FONT] 	[FONT=DejaVu Sans Mono][SIZE=2][SIZE=2][FONT=Arial]/etc/modprobe.d/blacklist.conf~

[/FONT][SIZE=2][FONT=Arial]Which is the same as the original.  Should I d[/FONT][FONT=Arial][SIZE=2]elete it, and how?

Thanks for reading![/SIZE][/FONT]
[/SIZE][/SIZE][/SIZE][/FONT]

---

### Post by 23senick on 2013-02-10
Solved - apparently due to latest version of Broadcom proprietary driver not being compatible with Ubuntu 12.04.  Need to revert to previous version.

See pages 2 and 3 on this thread 

[http://ubuntuforums.org/showthread.php?t=2111403](http://ubuntuforums.org/showthread.php?t=2111403)

---

