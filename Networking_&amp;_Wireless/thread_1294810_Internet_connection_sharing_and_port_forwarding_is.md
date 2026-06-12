---
title: "Internet connection sharing and port forwarding is driving me insane"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by Harbin on 2009-10-18
[IMG]http://i.servut.us/i/Getting_HTTP_server_to_public.png[/IMG]

I have internet properly shared to all computers, BUT still (after 7 hours of work) haven't managed to get my Apache HTTP server to be connectable from internet. Any tips? I really appreciate any, this thing is driving me absolutely insane. Have tried with iptables, firestarter, guidedog blah blah.

Current situation: I can connect to WANIP from my desktop computer, but other people still can't connect to HTTP server. It would be quite funny otherwise, but I'm really starting to lose my mental healt...

---

### Post by Harbin on 2009-10-18
[IMG]http://i.servut.us/i/ei_naurata.png[/IMG]

---

### Post by dmizer on 2009-10-18
> **Harbin said:**
> Current situation: I can connect to WANIP from my desktop computer, but other people still can't connect to HTTP server. It would be quite funny otherwise, but I'm really starting to lose my mental healt...

Are you absolutely positive that other people can't connect to your HTTP server? In other words, have you actually tested it from a computer that isn't connected to the same LAN as your HTTP server?

I'm not entirely clear on your setup despite your diagram and screen shot. Is the "gateway" an Ubuntu computer?

---

### Post by Harbin on 2009-10-19
Seems like my operator doesn't have any ports open for incoming connection, I guess my internet is perma NAT'd. Such a shame...

---

