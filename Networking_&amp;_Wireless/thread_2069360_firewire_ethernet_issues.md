---
title: "firewire ethernet issues"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by Wej on 2012-10-10
About a year ago, I used directions on an article on the ubuntu site, [https://help.ubuntu.com/community/EthernetOverFirewire](https://help.ubuntu.com/community/EthernetOverFirewire) to configure Ethernet over FireWire. It worked great, and I was able to transfer data between servers. I just went to transfer some more data today, and one of the servers' firewire interface was missing. I fiddled with it a bit, but can't seem to get it to talk to the other server anymore. I had that page bookmarked, so I went to it to see if I was missing something, but the article has changed completely. It now references firewire-net, whereas before, it referenced the eth1394 modules. I didn't update the server at all, so I need the old article and the details it contained. Is there any way to find that old article? Wayback machine doesn't have it, and searching google always gets me the current article. I searched through my bash history and tried removing and re-adding the modules that I had added in the past, but that doesn't seem to have solved it. The interface came back with a different name (eth1 vs. eth1-00), but giving it an IP address and trying to ping the other servers on the firewire hub doesn't work.

Does anyone know either A: how to get ethernet over firewire working properly again on an older kernel or B: how to retrieve an old article from the community wiki so I can figure out how I did it last time?

---

