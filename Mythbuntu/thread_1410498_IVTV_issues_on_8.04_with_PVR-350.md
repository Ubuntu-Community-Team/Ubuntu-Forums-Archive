---
title: "IVTV issues on 8.04 with PVR-350?"
date: 2010-02-18
forum: Mythbuntu
---

### Post by elklabone on 2010-02-18
Ubuntu 8.04.4 LTS
PVR-350 Video Card

Hi All - 

Read here a lot, post rarely, usually find my solutions in other posts. Moderate Linux skills... 

Upgraded Mythbuntu 7.something to 8 and then version 9, all hell broke lose with version 9 so downloaded and burned 8.04 LTS to a disk and reformatted reinstalled. Getting everything working again. 

I'm trying to chase down some issues with the system freezing up, which wasn't a problem previously.

I think I have some issues with IVTV... here are some of the log entries that catch my attention:

mythfrontend.log
2010-02-18 16:41:23.401 IVD: ivtv version 1.1.0
2010-02-18 16:41:23.431 Using the PVR-350 decoder/TV-out

2010-02-18 11:31:17.763 IVTV rawframes decreased! Did the decoder reset?
2010-02-18 11:31:18.822 IVD Error: Fetching frames played from decoder
... and later...
2010-02-18 17:48:02.321 ivtv picture start overflow

mythbackend.log

2010-02-18 19:00:03.089 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
                        is not supported by ivtv driver, using 48000 Hz instead.
2010-02-18 19:00:03.092 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  2010-02-18 19:00:03.136 Started recording: $

 properly capture VBI data on PVR-250 and PVR-350 cards.

And finally from:
messages
ivtv0: All encoder VBI stream buffers are full.
ivtv0: Cause: the application is not reading fast enough.

All of these messages tend to repeat from time to time... not sure if they all happen at the same time.

Any ideas or suggestions would be greatly appreciated.

-Mark

---

### Post by elklabone on 2010-02-18
... and should I be using IVTV or  [FONT=monospace][/FONT]ivtv-fb ?? Are they the same thing? I think I installed ivtv and not ivtv-fb when trying to get the pvr-350 sending the output to our TV.

-Mark

---

