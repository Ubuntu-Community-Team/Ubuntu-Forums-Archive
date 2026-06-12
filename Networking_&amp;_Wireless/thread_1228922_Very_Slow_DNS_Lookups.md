---
title: "Very Slow DNS Lookups"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by boilednut on 2009-08-01
I recently noticed a significant slowdown in loading web pages on my Jaunty box. Using the network analysis utility Netalyzr:

[http://netalyzr.icsi.berkeley.edu/](http://netalyzr.icsi.berkeley.edu/)

I narrowed the issue down to very slow DNS lookups: the Jaunty box, consistently, has over an order of magnitude worse DNS lookup latency than a Windows XP box on the same LAN (1700ms vs. 110ms). Both DNS lookups were done against OpenDNS; both machines were connected over Ethernet; both tests were run in Firefox 3.0.12.

Also, to eliminate hardware as a cause, I booted the Jaunty box into Windows Vista, and my lookup times were on par with those on the XP box.

I only noticed the problem after I installed the BIND security updates; although, since I didn't do any Netalyzr comparisons prior to the updates, I may have just overlooked it before.

Any ideas for a cause or fix?

---

### Post by dominiquec on 2009-08-02
I have this problem on my home DSL connection but not in my office DSL connection.  I use different providers, so perhaps that's an issue; my home computer is also a laptop with wireless and wired connections, again another possible source of difference.

I managed a fix on my laptop by connecting to wired Ethernet.  Then I manually configured my eth0 via /etc/network/interfaces and disabled by Wifi.  I seem to have better results now.

Your mileage may vary.

---

### Post by boilednut on 2009-08-02
Thanks...disabling my wireless adapter at the hardware layer did provide a significant improvement in my lookup latencies. A reboot was required to notice the improvement.

---

### Post by Crafty Kisses on 2009-08-02
I would suggest you use Wireshark so when you do the DNS lookup to see what is actually happening and see what is causing the slow down. You may also want to look into the following directory:
```
/etc/resolv.conf
```
Then see your options. I honestly would try and use Wireshark and see what is causing the slow DNS lookups.

---

### Post by jfr1tz on 2009-08-19
noticed this issue too,solution posted [here]("http://techxplorer.com/2007/02/22/slow-browsing-using-firefox-on-ubuntu/") solved it in my case.

---

### Post by boilednut on 2009-08-19
Thanks jfr1tz: the fix you suggested dropped by lockup times to ~900ms -- a substantial improvement.

**Update:** Actually, I was mistaken: disabling ipv6 in Firefox didn't improve my lookups; the improvement I noticed was a result of disabling my wireless adapter at the hardware layer.

---

### Post by .nedberg on 2009-08-29
Don't know if you fixed your problem or not.

I noticed the same behavior on my machine, and tried some different things to fix it. I changed to openDNS and disabled ipv6, without much result.

OPs post led me to the solution. I have a "clean" install of Ubuntu and compared some installed packages regarding bind. winbind was installed on all my machines with this problem. Uninstalling winbind (and restarting network) made the difference! I no longer have to wait for pages to load!

Only "problem" I have noticed is that I can no longer ping/ssh to local computers using the hostname, I need to use either the ip or hostname.local. I will probably add some rules to /etc/hosts later to solve that.

Hope this helps!

---

### Post by boilednut on 2009-08-29
Thanks .nedberg: your solution led me to another, similar, one. Instead of removing winbind, I modifed the *hosts* setting in

    [COLOR="Blue"]/etc/nsswitch.conf[/COLOR]

to move *dns* before all of the SMB/CIFS-related lookup services (I made it the 2nd entry -- right after *files*). With this change, my dns lookup times dropped dramtically: down to **99ms**. Also, since I didn't remove winbind, I'm still able to ping local machines based on hostname.

NOTE: You have to reboot after making the 'nsswitch.conf' change for it to take effect.

---

### Post by .nedberg on 2009-08-29
Great! That's an even better solution!

---

### Post by charlesrdavis on 2010-11-22
I had a very big difference in DNS lookup in 9.10. (Typical page load: Windows 3 seconds, Ubuntu 20 seconds.) Moving DNS as described above completely solved the issue.

---

### Post by VanillaMozilla on 2010-11-22
This can happen if you have an error in the DNS address.  You may get multiple timeouts before the system tries an alternate.  See [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/621879](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/621879) .

You can use
nslookup -d2 <url>
to display complete lookup debugging information (but nslookup may not use the same options as a Web browser or other program).

Please let me know if you find this to be your problem.

---

### Post by guardado on 2011-12-04
> **boilednut said:**
> Thanks .nedberg: your solution led me to another, similar, one. Instead of removing winbind, I modifed the *hosts* setting in

    [COLOR="Blue"]/etc/nsswitch.conf[/COLOR]

to move *dns* before all of the SMB/CIFS-related lookup services (I made it the 2nd entry -- right after *files*). With this change, my dns lookup times dropped dramtically: down to **99ms**. Also, since I didn't remove winbind, I'm still able to ping local machines based on hostname.

NOTE: You have to reboot after making the 'nsswitch.conf' change for it to take effect.

Thanks this also solve my problem of slow DNS.
In the file I change:

hosts: files mdns4_minimal NOTFOUND=return dns mdns4
To
hosts: dns files mdns4_minimal NOTFOUND=return mdns4

---

