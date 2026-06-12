---
title: "Unable to connect XP &lt;-&gt; Ubuntu over Wireless"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by toreriks on 2009-10-31
Hi,

In an attempt to connect my fresh Ubuntu 9.10 install to an WinXP machine using the Terminal Server Client, I've encountered some networking problems.

Both machines have WAN access.

Here is what I've tried, unsuccessfully, so far:

-Terminal Server Client reports "unable to connect". (Protocol: RDP)
-Both machines run Apache. I'm able to  connect locally to both installations, but not  remotely. Error message from browser is in the lines of "Site not available".
-Tried telnet to both machines without success. On Ubuntu, telnet reports: "Unable to connect to remote host: No route to host"
-Tried VNC using Vinagre at the Ubuntu side and RealVNC on the WinXP side. Got error message: "Coonection to host closed".
-Disabled the firewall on the WinXP machine and retried all of the above, to no avail.

Any help / tips / suggestions will be appreciated.

Thanks,
tores

---

### Post by toreriks on 2009-11-05
I found the err. My wireless router was blocking all traffic between my hosts. Opening up for the appropriate IP's in the firewall solved it.

---

