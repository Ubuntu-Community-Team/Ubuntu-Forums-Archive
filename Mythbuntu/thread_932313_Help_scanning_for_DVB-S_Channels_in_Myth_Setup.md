---
title: "Help scanning for DVB-S Channels in Myth Setup"
date: 2008-09-28
forum: Mythbuntu
---

### Post by fibble on 2008-09-28
Hi,

When trying to scan for satellite channels in MythTV Setup I get nothing.

A command line scan on Astra-28 works fine, and Kaffeine scans, find channels and I can watch tv no problems.

Myth Setup however just skips straight to an empty channel list. It doesnt try to scan at all! No progress bars.

I have used the Full (Tuned) scan option. Used the Astra28 freq info from /usr/share/doc/dvb-utils/examples/scan/dvb-s/  but no scan ever happens :(

Am i doing something wrong? Can anyone who has done this successfully share their experience with me?

Thanks

Andy

---

### Post by fibble on 2008-09-29
Hi,

After trawling some wiki's and mailing lists I realised I had never looked at the DiSEq settings menu when configuring my DVB-S Card.

As i dont have a DiSEq switch i thought it unecessary, but you have to tell MythTV What type of LNB you have connected to your DVB-S card before it will attempt to tune to any channels during the scan.

I now have channels. Hopefully this might help somebody else :)

Andy

---

