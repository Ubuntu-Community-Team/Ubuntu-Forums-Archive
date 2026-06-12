---
title: "No automatic commercial flagging for one channel"
date: 2010-10-06
forum: Mythbuntu
---

### Post by laffinet on 2010-10-06
For some reason automatic commercial flagging doesn't work for one of my channels (ABC1 in Australia).

All my other recordings get flagged automatically during recording, just this one doesn't.

I checked in the channel editor, the commercial flagging method is the same ("use global settings"), so why doesn't it get flagged ?

Starting the manual flagging job works fine.

Any ideas ? Thanks

---

### Post by ian dobson on 2010-10-06
Hi,

Could it be that the ads run for a long time (> 5 minutes)? There is a option to set the maximum expected advert length, but this is limited to 6minutes (in the code) I think.

Comm flagging works by looking for "changes" in the video, for example sender logo, format (4:3,16:9). If the sender is clever and keeps on changing the size/color/position of the sender logo then the commflagger will have a problem finding the adverts.

Regards
Ian Dobson

---

### Post by laffinet on 2010-10-06
Nope, it's not the ad length. The recordigs on that channel don't get flagged. 

When I edit the recording and try to bring up the ad flags I get an "recording not flagged". If I then run commercial flagging manually (ie through the jobs menu) the ads get flagged. Hope this makes sense

---

### Post by TopEnder on 2010-10-07
> **laffinet said:**
> For some reason automatic commercial flagging doesn't work for one of my channels (ABC1 in Australia).

All my other recordings get flagged automatically during recording, just this one doesn't.

I checked in the channel editor, the commercial flagging method is the same ("use global settings"), so why doesn't it get flagged ?

Starting the manual flagging job works fine.

Any ideas ? Thanks
Maybe it has something to do with the ABC are not allowed to run commercials and they call their own advertising as something other than commercials?

---

### Post by ian dobson on 2010-10-07
Hi,

Then the only thing I can think of is that the channel is marked "commercial free", go check that in mythtv-setup.

Regards
Ian Dobson

---

### Post by laffinet on 2010-10-07
> **TopEnder said:**
> Maybe it has something to do with the ABC are not allowed to run commercials and they call their own advertising as something other than commercials?

It's not so much commercials I'm trying to ge flagged, more the beginning and end of the program. I always records a bit of extra both sides to make sure I get the whole program.

It's not that nothing gets detected, the recording never gets flagged unless I start the job manually.

---

### Post by laffinet on 2010-10-07
> **ian dobson said:**
> Hi,

Then the only thing I can think of is that the channel is marked "commercial free", go check that in mythtv-setup.

Regards
Ian Dobson

I did that, it's set to "use global settings", just like all the other channels.

---

