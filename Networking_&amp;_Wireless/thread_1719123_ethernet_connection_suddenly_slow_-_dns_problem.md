---
title: "ethernet connection suddenly slow - dns problem?"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by johnmuir on 2011-04-01
If anyone can help on this I'd be most grateful.

A couple of days ago my internet connections suddenly became very slow/intermittant. 

I thought the problem was at my DSL provider but after more checking the problem seems to be in Ubuntu/Linux somewhere. 

Reason: I can dual boot with windows 7 and have no ptoblem at all. Also I tried a Ubuntu laptop on the same router ethernet port and it also works fine. So its not my hardware or my provider, and its not a general Ubuntu problem either.

There are no error messages in any of the /var/log files and ifconfig looks normal. 

It seems to be a DNS problem as it's the initial connection to a host which often times out. If I get a connection, I can e.g. stream an radio station fine.

If I try to e.g. traceroute any host it times out (no reply).

Ubuntu 10.10 is totally up to date as of today.

I'm stuck! How can I troubleshoot this to find the cause? Any thoughts or help much appreciated. 

John

---

### Post by Enigmapond on 2011-04-01
You can always try Googles public DNS servers as they tend to be very quick. Right-click the network icon/Edit Connections/IPv4 settings/DNS Server and input 8.8.8.8 & 8.8.4.4 separated by a comma. This may help.

---

### Post by johnmuir on 2011-04-01
Thanks, I tried that but that wasn't the answer. It must be something specific to this one machine as the Ubuntu laptop has no problems on the same router port.

---

### Post by dineshs on 2011-04-01
Did you try [disabling ipv6 ]("http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can")?

---

### Post by johnmuir on 2011-04-01
IPv6 is already disabled (I think - Method: Ignore)

---

### Post by dineshs on 2011-04-01
Please try what is suggested (under the heading ipv6) in the link given in post #4.

---

### Post by johnmuir on 2011-04-01
OK, checked that, but IPv6 was already disabled in Firefox. The problem is the same if I use Opera or Chrome or Konqueror.

---

### Post by johnmuir on 2011-04-01
Hallo Enigmapond!

I changed the DNS servers as you suggested and the problem disappeared! Many thanks!

But why?

Only this machine is affected and only since a few days. Another Ubuntu machine on the same port using the default configuration has no problems? 

I'd like t get to to the underlying cause of the problem. Using Google as DNS server seems like a quirky workaround...

---

### Post by Enigmapond on 2011-04-01
> **johnmuir said:**
> Hallo Enigmapond!

I changed the DNS servers as you suggested and the problem disappeared! Many thanks!

But why?

Only this machine is affected and only since a few days. Another Ubuntu machine on the same port using the default configuration has no problems? 

I'd like t get to to the underlying cause of the problem. Using Google as DNS server seems like a quirky workaround...

Hey glad it helped. As to the root of the problem, I have no idea. I always use the google DNS as it has always been quicker than my ISP's default.

Cheers!

---

### Post by johnmuir on 2011-04-03
I'm sorry to report that the problem is suddenly as bad as ever. I'm still using the Google servers, but have all the problems and symptoms as in my original post. Does anyone have any idea how to get to the root of this problem?

---

