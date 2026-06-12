---
title: "ntpdate domain.local (no server suitable for synchronization found)"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by guimenez on 2010-11-02
I can't update my ubuntu clock with my server.

If i run the command **ntpdate domain.local**,  it gives me this erro  (no server suitable for synchronization found)

if i run the command **nslookup domain.local** it works well and found my server

please, what can i do?

thanks

---

### Post by SeijiSensei on 2010-11-02
Are you running ntpd on the server?  Is port 123/udp open to the client?

Try using a [public NTP host]("http://support.ntp.org/bin/view/Servers/NTPPoolServers") like 0.pool.ntp.org.

---

### Post by guimenez on 2010-11-03
> **SeijiSensei said:**
> Are you running ntpd on the server?  Is port 123/udp open to the client?

Try using a [public NTP host]("http://support.ntp.org/bin/view/Servers/NTPPoolServers") like 0.pool.ntp.org.

thanks for replying

it gives me the same error :(

i need to open 123 udp on my router? or my windows server

thanks

---

### Post by SeijiSensei on 2010-11-03
I meant that if you had a local server providing NTP, you'd need to make sure the clients could see its port 123.  In principle, you shouldn't need to open the port on the router, since the client's request should be masqueraded by the router the way it masquerades all other traffic.

Let's start with something more basic, though.  What happens if you enter "host 0.pool.ntp.org"?  Maybe your DNS isn't resolving properly.  What happens if you use "ntpdate 70.86.250.6" which is the IP address of one of the 0.pool servers?

What about my original question.  Are you running an NTP server on your server box?  Does it have log entries reporting that it updated the system clock periodically?  If you can get an NTP server working locally, that would be the best solution.

---

