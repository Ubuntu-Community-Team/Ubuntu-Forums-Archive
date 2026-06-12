---
title: "Sopcast on Gutsy-amd64 - Segmentation Fault (core dump) error."
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by ryth on 2007-12-06
Hey Folks,

I'm trying to get the command line sopcast running on my gusty install, but I'm having a lot of problems.

Essentially once installed I am running the following command to run it:

**./sp-sc-auth sop://myserver/mychannel xxxx yyyy**

Every time I run it I get the following error:

> Segmentation fault (core dumped)

Anyone have any suggestions?  Pasted below are the full log file.

Thanks.

> detect MTU=4c4
Connection=11   Connection=11
i=0   51
ipExternal:177b454c  Internal:c801a8c0  portLocal:34976    portExternal1:34976    External2:34976  linkType:51
tm3.sopcast.com proto=17
adv=419
TD1=4294961575-5721:  1196985499:419:2984596014
tm3.sopcast.com proto=17
adv=694
TD1=4294962199-5097:  1196985500:694:2984596115
Average difference=4294961887
4294961887
4294961887
3dbedaf0 28ba0b0d
Not valid ID
74c037b2 b293cad8
sop://broker1.sopcast.com:0/99
system channelID=99
detect MTU=4c4
localaddr:      c0a801c8:24289, externaladdr:4c457b17:24289
STOP QUIT
retv = 0
        spsc_cleanup_sysch
sopch2_schedule_sc_misc_sysch retv=0
CHLST blockSize=0
2984592711:2984590706
Segmentation fault (core dumped)

---

### Post by giddy1945 on 2008-01-22
Anyone?

---

