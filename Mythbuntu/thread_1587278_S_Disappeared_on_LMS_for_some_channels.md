---
title: "S Disappeared on LMS for some channels?"
date: 2010-10-03
forum: Mythbuntu
---

### Post by Saubazi on 2010-10-03
Some of the channels are not visible anymore the S went away from LMS
Only message that I think has something to do with the issue is from backend log:
2010-10-02 18:26:52.957 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(4908) desired(33) 

What can I do? It is not in the reception - the same channels can be viewed with normal digibox, so it is not a signal issue or changed transponders/frequencies or so...

---

### Post by ian dobson on 2010-10-03
Hi,

rescan yor channels. It looks as if your tv provider has changed some of the internal streams (PAT/PMT). Mythtv reacts badly to changes in the stream structure.

Regards
Ian Dobson

---

### Post by Saubazi on 2010-10-03
Yes, Can do - I just thought that there are no changes from satellite side as everything works normally on a standard digibox

---

