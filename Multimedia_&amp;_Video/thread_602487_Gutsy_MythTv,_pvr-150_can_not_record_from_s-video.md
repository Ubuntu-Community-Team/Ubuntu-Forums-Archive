---
title: "Gutsy MythTv, pvr-150 can not record from s-video"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by canzi on 2007-11-04
since moving to Gutsy i cant record s-video on my pvr-150 anymore.
I use the s-video to watch Foxtel which works fine but when i try to schedule a recording from any interface (mythweb, mythfrontend) they fail

in /var/log/mythtv/mythbackend.log i see
2007-11-04 22:26:33.282 Scheduled 1 items in 0.0 = 0.01 match + 0.01 place
2007-11-04 22:26:33.286 scheduler: Scheduled items: Scheduled 1 items in 0.0 = 0.01 match + 0.01 place
2007-11-04 22:26:33.326 TVRec(1): Changing from None to RecordingOnly
2007-11-04 22:26:33.340 TVRec(1): HW Tuner: 1->1
2007-11-04 22:26:33.343 Channel::GetCurrentChannelNum(101): Failed to find Channel '101'
2007-11-04 22:26:33.344 Channel(/dev/video0)::TuneTo(101): Error, failed to find channel.
2007-11-04 22:26:33.345 TVRec(1) Error: Failed to set channel to 101. Reverting to kState_None
2007-11-04 22:26:33.346 TVRec(1): Changing from RecordingOnly to None
2007-11-04 22:26:33.350 Canceled recording (Recorder Failed): 101 (1000) "Sun Nov 4 22:26:00 2007": channel 1000 on cardid 1, sourceid 1
2007-11-04 22:26:33.356 scheduler: Canceled recording (Recorder Failed): 101 (1000) "Sun Nov 4 22:26:00 2007": channel 1000 on cardid 1, sourceid 1

why is it trying to change channel on s-video?, the channel change box is empty.

any help appreciated

Canzi

---

### Post by emkamau on 2007-11-05
I have the same issue. I have my mythbox hooked up vi S-Video to a DirecTv satellite box that is constantly tuned to channel 615. I have even changed my SchedulesDirect  channel lineup to include only channel 615. I can watch the channel on mythtv but all scheduled recordings fail. Also myth does not seem to know what channel I'm on when on 615. The box on the screen that shows the channel info when you switch channels is always blank for 615.

Any ideas on what the issue is anyone? I feel I'm missing something fundamental/simple

emk

---

### Post by canzi on 2007-11-09
bump - has anyone got a working s-video or comp (recording) pvr-150 on gutsy?

---

### Post by canzi on 2007-11-09
now im confused, i went back to feisty, and even tried another computer but i still cannot record using the pvr-150 on s-video, i can watch it but i cannot record it.
anyone?

---

### Post by canzi on 2007-11-12
with further investigation ive found

from the fronted when i type a foxtel channel number, it switched to s-video but then says channel 9 and what every the show is on channel 9. if i then press up or down the right foxtel info is displayed but when i hit enter to choose it i get the foxtel channel but the channel 9 info.

im guessing this is why i can not schedule a record and looks to be a database issue.

anyone want to go out on a lim with this?

---

### Post by canzi on 2007-11-24
deleted all the channels and source, resetup source scanned and found 30 channels of nothing, assigned the foxtel to the first 12 channels and deleted the rest,
it now works.

---

