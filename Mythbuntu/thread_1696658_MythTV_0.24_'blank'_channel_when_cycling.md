---
title: "MythTV 0.24 'blank' channel when cycling"
date: 2011-02-27
forum: Mythbuntu
---

### Post by lindsayward on 2011-02-27
Hi there.
(I wasn't sure what the best title for this thread would be...)

I've just installed MythTV 0.24 after upgrading to Ubuntu 10.10 from 10.04 and MythTV 0.23-fixes. So far so good, except:
I have an odd problem (that I think didn't have before) that when I browse through the channels using up or down, I get to a blank one that resets the 'progress'.
I have channels like 2, 3, 5, 7... 32, 50, 72, 73 ... 88.
When I press up it goes to 50, with each change showing what show is on the channel (doesn't change until I press OK), but when I press up after 50 (One HD) I get a blank black box with no details and the next channel is 2. If I press OK on the blank one it doesn't change channels, just takes the black box away.
If I start above 50 and go down, it gets to 72, then the next one is blank, then the next one down is 88 again, so I can't cycle through all channels in one direction – annoying.
I've checked the channel table in MythWeb and everything looks OK. Each channel has an xmlid, channel number and freqid.

Any ideas? Thanks in advance.

---

### Post by myth1914 on 2011-02-27
I would go into the channel editor on the backend and remove channel 50 first.

---

