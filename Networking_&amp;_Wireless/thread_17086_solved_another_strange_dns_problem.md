---
title: "solved another strange dns problem"
date: 2005-02-25
forum: Networking &amp; Wireless
---

### Post by sabot4ge on 2005-02-25
well, i realiazed that there were so much people complaing about DNS problems with ubuntu. I really wonder if this is fixed in thenew realese.

well my problem was the same of the majority. 
Im using a ADSL connecton wit a modem in bridge mode (not router) and used pppoeconf to configure my dsl connec (is there another way?)

while perfect connect it still could not navigate, afte various tests i realizied that simply DEactivete your ether card reslv the problem (?????) thats right

ifdown eth0
pon dsl-provider

and voila! browsing like hell  :twisted:
computer --> sstem config. --> network to deactivete it from boot

a hole hour and still browsing the web.
i hope it helps someone

ps: someone could give a thecnical explanaton for this?
and sorry for the bad english, its not my native language

---

