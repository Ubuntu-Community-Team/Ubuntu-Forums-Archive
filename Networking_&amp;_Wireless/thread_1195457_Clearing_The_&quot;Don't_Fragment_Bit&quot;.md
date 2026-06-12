---
title: "Clearing The &quot;Don't Fragment Bit&quot;"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by EricPope on 2009-06-23
How do you configure Ubuntu so that the "don't fragment bit" in the IP headers of outgoing packets is cleared? I think some of my outgoing packets might be getting dropped when they travel to network segments with low MTU.

Thanks,
Eric

---

### Post by lensman3 on 2009-06-23
"ip" might do it with the MTU discovery "stuff".  

The "tracepath" program might help you figure out what the MTU should be.

The following code snippit is in /etc/init.d/networks

if [ -f /proc/sys/net/ipv4/ip_always_defrag ]; then
	        if [ `cat /proc/sys/net/ipv4/ip_always_defrag` != 0 ]; then
		        action $"Disabling IPv4 automatic defragmentation: " sysctl -w net.ipv4.ip_always_defrag=0
		fi
	  fi
	fi

That might fix it.


Look at a script called "/sbin/cbq".  This has some very high level info on scheduling packets through interfaces.  But it uses a program call "tc" to set the packets scheduling.  It might give you additional clues.

Hope something here will help.

---

