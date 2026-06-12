---
title: "Ubuntu Server 10.04 Hostapd daemon not starting"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by BadOpCode on 2010-05-28
Weirdest thing ever and i'm going nuts trying to figure it out.

tried the command line

sudo /usr/sbin/hostapd -P /var/run/hostapd.pid -B /etc/hostapd/hostapd.conf

works no prob

so I figured maybe something buggered with the start-stop-daemon dealio in /etc/init.d/hostapd.   
put the command line as it should look after all the stuff is filled in at a prompt.  Works.
try to start script via sudo /etc/init.d/hostapd start script says its starting and gives a OK but the daemon never starts and its no where in memory when i do ps waux | grep hostapd
Is it just me or has other people ran into this?
How do I test a start script to see why its failing even though it says its not?
I'm totally mystified as everything works when i check manually. :confused:

---

### Post by BadOpCode on 2010-06-01
I sat down and looked at the script a couple nights ago.  The /etc/init.d/hostapd has a clause in it that it will exit if the config in /etc/default/hostapd does not have RUN_DAEMON="YES"
Even though the forced to run as a daemon (-B) switch is being used so there its not going to be any other way as-is.
On my setup /etc/default/hostapd had RUN_DAEMON="YES" commented out.
Ya this is a silly mistake on my part as I should have been able to catch this sooner.  But I never dreamed someone would add such a dumb clause and require everyone to go digging through scripts in order to get the daemon to load.
I mean... wouldn't it make more sense if it was ...
```

if [ $RUN_DAEMON == "NO" ]; then
  exit 0
fi

```
rather than...
```

if [ $RUN_DAEMON != "YES" ]; then
  exit 0
fi

```
that way if nothing is specified at all it would default to yes and the script would load the daemon.
Unless the idea is we are going to have Micro$oft's "Are you REALLY sure?" style of scripts.

---

### Post by irose123 on 2010-06-15
> **BadOpCode said:**
> 
On my setup /etc/default/hostapd had RUN_DAEMON="YES" commented out.


So glad you found this, I would have spent ages trying to solve exactly the same problem on my lucid server: works when run manually as you describe, but daemon doesn't seem to start at boot time though.

I just uncommented the line above and restarted, and bingo, hostapd now runs at startup!

---

### Post by schodt on 2010-07-14
> **BadOpCode said:**
> 
On my setup /etc/default/hostapd had RUN_DAEMON="YES" commented out.

Thanks a lot. That helped me.

---

### Post by dcosmin on 2010-09-21
Thanks ! Its working :P

---

### Post by EddieO2 on 2010-09-25
Thanks!
I've been tearing my hair out over this one!

---

### Post by markturnip on 2011-01-09
I'm also having an issue with the Hostapd daemon not starting. 

Running sudo /usr/sbin/hostapd -P /var/run/hostapd.pid -B /etc/hostapd/hostapd.conf also works fine for me & returns:
Using interface wlan0 with hwaddr 18:f4:6a:a7:51:8d and ssid '

However if I run /etc/init.d/hostapd start it doesn't do anything nor return with a message.
Would you mind posting your hostapd daemon here?

Thanks.

---

### Post by merlinblack on 2011-04-26
I think the RUN_DAEMON in /etc/default/hostapd refers to if hostapd should be run or not at all - in contrast to the -B switch.

This saves having to edit symlinks in the rc?.d directories when you want to enable or disable running it on boot.

But that's just a educated guess.

---

### Post by HonoredMule on 2012-09-22
It appears that in Precise someone tried to fix the issue, and actually made it worse.  RUN_DAEMON is no longer included in the package-supplied /etc/default/hostapd file, nor is it checked in the init script anymore.  So, you'd think it's no longer needed--and you'd be wrong.

To make matters worse, neither the init script (which by the way is still pure classic sysVinit) nor the default config specify the location of the configuration file.  So in /etc/default/config you must explicitly define RUN_DAEMON *and* DAEMON_CONF or hostapd won't start nor report any error.  It's possible I missed it, but there don't seem to even be any errors in /var/log/syslog or /var/log/messages.

Perhaps the release team is trying to score one of [these](http://www.thinkgeek.com/product/f141/?cpg=gplus).

---

