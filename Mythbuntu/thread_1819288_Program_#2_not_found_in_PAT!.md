---
title: "Program #2 not found in PAT!"
date: 2011-08-05
forum: Mythbuntu
---

### Post by movieman on 2011-08-05
Does anyone know how to fix this? We have one digital channel which broadcasts both SD and HD. I have MythTV configured so that it picks the HD channel for HD shows and SD channel for SD shows. It was working fine for a couple of weeks, now every time it tries to record an SD show I get this message in the backend log and it records from the HD channel instead.

The TV works fine so I presume the signal is being broadcast correctly, but MythTV can't find it.

---

### Post by ian dobson on 2011-08-06
Hi,

Looks as if your tv provider has changed the channel list/internal multiplex list. Just run mythtv-setup and do a transponder scan/channel scan, that should fix it.

Regards
Ian Dobson

---

### Post by movieman on 2011-08-06
Thanks. It says 'Found one off-air channels' but then it's asking if I want to delete all, set all to invisible or ignore all. I've no idea what any of those options mean and they all seem bad.

---

### Post by movieman on 2011-08-06
Ah, OK, I told it to ignore that and then it asked if I wanted to update the two known channels. Maybe that will have fixed it.

---

### Post by movieman on 2011-08-06
No, doesn't seem to have made any difference :(. I don't understand why scan can find the channels but it can't then record from one of them.

---

### Post by ian dobson on 2011-08-06
Hi,

Did you do a channel scan or transponder scan?

Regards
Ian Dobson

---

### Post by movieman on 2011-08-06
Channel, I presume.

---

### Post by ian dobson on 2011-08-07
Hi,

The maybe try a transponder/full scan on mythtv-setup.

The mythtv scanner isn't really the best. Also maybe try using w_scan to create a channels.conf file that you can import into mythtv.

Regards
Ian Dobson

---

