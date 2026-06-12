---
title: "Unable to Enable Wireless"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by gordon33 on 2011-06-09
Hello all

I am unable to Enable Wireless with 10.04.  It worked 7 days ago.  

Their was an update to the Netgear wireless router 7 days ago.

I have HP Gt06-200 lap top.  Its wireless light is blue.  So it appears that the lap top sees the wireless router.

I have checked the WEP Key many times.  

To day I find  with terminal command rfkill

gordon@gordon-laptop:~$ rfkill
Usage:	rfkill [options] command
Options:
	--version	show version (0.4)
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
gordon@gordon-laptop:~$

---

### Post by chili555 on 2011-06-09
> gordon@gordon-laptop:~$ rfkill
Usage: rfkill [options] commandPlease try:```
rfkill list all
```Thanks.

---

### Post by gordon33 on 2011-06-09
Hello chili555

Yesterday both blocks were no.

gordon@gordon-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by jramshu on 2011-06-09
Hard blocked means it is disabled by the wifi switch on the laptop itself and rfkill will not be able to enable it, only the wifi switch/button will be able to do this.
Try disabling it then re-enabling it with the switch/button.

---

### Post by gordon33 on 2011-06-09
Hello jramshu

I rebooted my computer as there is no responce from the blue wireless button .  Here are the results now.

gordon@gordon-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
gordon@gordon-laptop:~$

---

### Post by gordon33 on 2011-06-09
Hello all

Its working now.  But Why

All I did was hold the blue lit wireless button down for about 30 sec. and gave up hope that it would go out or change to an orange color.  Then I shut down and restarted the lap top.

Got back to this post, re-ran "rfkill list all" to find the blocks gone and able to connect to the wireless router.


gordon33

---

### Post by jramshu on 2011-06-09
Mine does that sometime, I have a g60 though and it has an actual wifi button. I have to hold it for a few seconds before it starts working.

---

