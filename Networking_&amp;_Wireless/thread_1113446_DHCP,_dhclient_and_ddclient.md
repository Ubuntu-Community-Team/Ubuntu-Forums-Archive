---
title: "DHCP, dhclient and ddclient"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by xefialtis on 2009-04-01
Here is a puzzle for you...

My server is on a DYNAMIC external IP. This means that when Comcast feels the urge, they can send a new lease request, and I get a new IP Address. They like to do this to the "residential" customers to keep them from benefiting like the "business" customers do (by having what appears to be a "static IP".

I use the service DynDNS, and there are others out there, that offer redirect services for dynamic IPs to your domain names.

This is what ddclient does. Every 5 minutes, ddclient checks my ip, sees if it has changed, and reports any changes to DynDNS to update my information. 

Ok, so I don't want ddclient to run every 5 minutes, or every 10 minutes...etc. I only want ddclient to run when the IP changes. This can be done when dhclient runs to grab a new IP address. 

The question I have is...WHEN does dhclient grab that new address? Is it in the exit or entry scripts?

---

### Post by freonchill on 2009-04-01
so you dont want ddclient running 24/7?

how about making a script that runs 24/7 and checks to see if ip has changed, if it has then it runs ddclient?

---

### Post by xefialtis on 2009-04-02
I am attempting to clean up some code and keep the system streamlined. The best way is to stop processes that are only going to make changes once in a great while from running all the time.

So, if I can find the script (entry or exit) for DHClient, I can add DDClient to it, so it will only run when the IP changes.

---

### Post by systemgod on 2009-05-02
If I understand the man page for dhclient correctly this should be done in the exit-hook (otherwise the new ip-address is not set yet).

I created the following script:

/etc/dhcp3/dhclient-exit-hooks.d/ddclient

which looks like:

---------------------------
case $reason in
	BOUND|RENEW|REBIND|REBOOT)
		/etc/init.d/ddclient restart
		;;
	EXPIRE|FAIL|RELEASE|STOP)
		;;
esac
---------------------------

Unless your lease time is bigger than 30 days (unlikely) this should update dyndns anytime you get a new lease (even if the ip-address didn't change) and keep your dyndns account alive.

---

### Post by freebeer on 2009-05-02
Perhaps a simpler approach might be available to you... your router might already be able to do this for you.  My Dlink router under Tools -> Dynamic DNS, I can enable it to notify DynDNS whenever the IP addy changes automatically.  No need for scripts, etc.

(Before I got this router, I, too, used the scripts.  They really aren't a burden on the system.  I think I set mine to check every hour.  In my case, my IP address, although dynamic, has only changed once in several years.  By setting it to one hour, an hour is the maximum (plus propagation time which is fast in my experience) that I can't reach my server.  That was fine for me, but your mileage may vary.

---

