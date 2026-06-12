---
title: "buggy internet problem"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by mefistofeles666 on 2010-02-01
So I updated my ubuntu, hardy, and for some reason my wireless started acting up ever since. I used to connect through wifi-radar because the standard network manager wasn't all that good. wifi radar started acting up too to the pooint that it would say it was connected to the local host 127.0.0.1, and it would not allow me to disconnect. so i switched back to using network manager since i was not able to resolve the issues with wifi radar and after much research I came up with people having the same problem and no one knew how to resolve it.

network manager was even buggier than before and it would only connect for a couple of mins and then just disconnect. and sometimes it would take me severals attempts before connecting to the wireless. I installed WICD and purged network manager, but wicd was acting the same way as the network manager so ipout in my ubuntu cd and re-installed network manager, but the problem is that nm is acting up and i can never keep a solid conection and am having the same problems as described before.

so, I'm posting to see if there's any kind of troubleshooting I can follow in order to see why has my wireless manager started to act this way. It was fine before, and i was able to keep a conection, but now it drops all too often.

also ndiswrapper doesn't seem to be functioning well because I always get the following message, even after reinstalling it:

sakura@sakura-laptop:~$ ndiswrapper -l
Error: no ndiswrapper utils found!

and lspci gives me the following lines, in case you were wondering what my wireless card was:

01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
05:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)



thank you for any help you can give.

---

