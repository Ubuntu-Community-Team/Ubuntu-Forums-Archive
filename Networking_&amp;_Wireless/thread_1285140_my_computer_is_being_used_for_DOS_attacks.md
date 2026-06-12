---
title: "my computer is being used for DOS attacks"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by blueson on 2009-10-07
using ubuntu 8.04

initially, i noticed my browser was slow to access google and there were no time-out messages. i went through my router log and found "smurf" and "syn flood" entries from the computer i was using (192.168.2.101) using random ports (44325) to an ip address that turned out to be google.com. i also ran chkrootkit and found "packet sniffer" on my eth1 which happens to be my wireless.

my first question is, what exactly triggers the syn flood? is it a something on my machine or possibly in my router? i'm guessing it's my machine since the source ip of the syn flood was the box i was using. if so, how can i find out which service/script/application is responsible? if i reinstall my box, will it clear the problem?

also, when i'm at home i use my wired network (eth0) to browse but my wireless (eth1, where the sniffer was found) is always open. is it possible that that someone hacked into my computer using my wireless connection? or was it from a sketchy website?

third, what kind of info can the hacker get through the packet sniffer? i want to know if the same person can save my mac address or whatever info they need and then do the same thing even if i reinstall my machine.

thanks

---

