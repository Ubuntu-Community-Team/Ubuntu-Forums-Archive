---
title: "iwgetid requires root on Dell Mini9 w/ BCM4312 (10.04)"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by A1Dox on 2010-06-20
I'm working on some scripts to automatically run when my Ubuntu net/laptops are started in different network environments. I know how to get the scripts to run when interfaces come up, and am trying to work out the best way to identify a location to take the appropriate scripted actions. I stumbled across a how-to that used "iwgetid --raw" to spit out the current SSID of a connected WLAN. That seemed a good starting point, but on this Dell Mini9 it is causing me some grief.

In fact, iwgetid and all the "Wireless Tools for Linux" utils are suffering from the same issue. They run without root privs (they're all mode 755), but do not return any results. If I "sudo iw<whatever>" the command executes correctly and returns the expected results. I have another machine, also running Lucid with a different wireless adapter, and the commands execute as expected.

My problem is on this Dell Mini9 running Lucid and the Broadcom STA drivers. I found a thread about Conky's Wireless status indicators not showing any results on Broadcom chipsets running the STA drivers, and am guessing this may be the same issue. In the other thread, running Conky with root privs "fixed" the problem too.

Does anybody have any advice? I looked through the source for the tools to see if I could work out what they used to source their data, to see if the mode flags of that was the problem, but drew a blank.

Can anybody help?  I'd prefer not to need to sudo the whole script, then I can have it run automatically but at the moment can't make it work without raising it's privs.

Thanks in advance...

Dox

---

