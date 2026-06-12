---
title: "Issues with New Live Streaming Recorder/Playback  ?"
date: 2012-11-06
forum: Mythbuntu
---

### Post by topcat5 on 2012-11-06
I'm running mythbuntu 0.26 with the latest fixes with a combined FE/BE and a remote FE. I am running this system with a couple of HD Homerun duals and a HVR2250 without any major issues.  With that as a base I decided to try the new Live Streaming Recorder/Playback mechanism introduced with 0.26.  

I used these instructions to give it a try. 

[User_Manual:Setting_up_HTTP_Live_Streaming_Recorder]("http://www.mythtv.org/wiki/User_Manual:Setting_up_HTTP_Live_Streaming_Recorder")


Unfortunately I can't seem to get it to work reliably.  

On the combined FE/BE machine changing to one of the streaming channels on liveTV usually works OK.  However, if I then change to another streaming channel, the FE will lockup  and usually requires the BE to be rebooted. If instead I change back to a regular "non streaming" channel it seems to work as expected.  

On the other hand it's a complete no-go on the remote FE.  When I attempt to watch a streaming channel on the remote FE, I may get a few seconds of video and then the FE completely locks up and may also crash.  If it is locked, killing (requires -9) the FE process may allow recovery.  Other times, it may require both the FE & BE machines to be rebooted.   

Interestingly, in both cases a livetv recording is successfully created  of the selected channel.  After I recover the machines I can view this recording from the livetv group on either FE without issue.  The duration of the recording lasts until the BE is rebooted, or some timeout has been hit but it lasts well beyond where the FE crashed.  

I've taken a look at the FE & BE logs and noticed the FE complains that it can't connect to the .mpg for the program even though it does exist on the BE.  Before diving deeper problem analysis I'm looking to see if anyone else has gotten Live Streaming Playback to work.      Thanks for any comments or suggestions.

---

