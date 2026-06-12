---
title: "Video stopping"
date: 2009-11-09
forum: Mythbuntu
---

### Post by andysummerskill on 2009-11-09
Just installed Mythbuntu 8.40 from the Mythbuntu iso CD and after many issues the only unresolved item is with the video display on the back end machine.

No problems what so ever on my only front end machine which is a laptop running Ubuntu 9.04 with mythbuntu installed on top.

However, on my backend machine (which is set up as a back end / front end) when 'Watch TV' is pressed the TV picture appears but the video stops after just a couple of frames. The sound continues but it is of quite a poor quality.

When the 'Watch Recordings' screen is opened, the thumbnail video seems to work OK but as soon as I start to play the recording the TV picture starts but, again, the video stops after a few frames with the sound continuing.

The graphics card in the Backend is an ATI Radeon card.

Can anyone help?

Regards,

Andy

---

### Post by OffAxis on 2009-11-09
8.4 on the backend? Is that right?

You didn't mention what kind of Radeon, so I'll just suggest that you upgrade your OS install and match the latest proprietary hardware driver for that. ATI pared down their support of 'Legacy' cards in the last few releases of the Radeon driver, so you'll want to look and see how close to the current release you can get (although personally, I'm having HUGE problems with the Karmic release (9.10) and can't recommend it yet).

Can your backend computer play a movie or video in VLC or mplayer okay?

---

### Post by nickrout on 2009-11-09
> **andysummerskill said:**
> Just installed Mythbuntu 8.40 from the Mythbuntu iso CD and after many issues the only unresolved item is with the video display on the back end machine.

No problems what so ever on my only front end machine which is a laptop running Ubuntu 9.04 with mythbuntu installed on top.

However, on my backend machine (which is set up as a back end / front end) when 'Watch TV' is pressed the TV picture appears but the video stops after just a couple of frames. The sound continues but it is of quite a poor quality.

When the 'Watch Recordings' screen is opened, the thumbnail video seems to work OK but as soon as I start to play the recording the TV picture starts but, again, the video stops after a few frames with the sound continuing.

The graphics card in the Backend is an ATI Radeon card.

Can anyone help?


Yes you can by looking at your mythfrontend logs.

---

