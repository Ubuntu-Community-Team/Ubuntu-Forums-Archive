---
title: "ATSC, DefaultChanid, and LiveTV problems"
date: 2012-12-28
forum: Mythbuntu
---

### Post by MarkMunkacsy on 2012-12-28
I am new to both MythTV and the Ubuntu forums, so please be patient.:razz:
 
I've run into a recurring problem that I assume is somehow related to how I've set up MythTV: whenever I enter LiveTV on the frontend, if the initial channel is not an ATSC channel, then I cannot change to an ATSC channel without getting an "Error opening jump program file" error. However, if I force DefaultChanid in the database table named "settings" to be an ATSC channel (before I start up liveTV), then I can tune every channel. Thus, if I exit LiveTV while watching an ATSC channel, then I can restart LiveTV later and watch every channel. But, if I exit LiveTV while watching an MPEG channel, then I'll never again get an ATSC channel on LiveTV until I go manually force DefaultChanid to a different value. This doesn't affect recordings, which don't seem affected by DefaultChanid.
 
The error itself is somehow caused by the backend's inability to find "Payload Start" for the desired PID after the dummy recorder has shut down and shifted to the real recorder. The failure to detect the payload results in a zero-length ringbuffer file that will cause a frontend timeout and the error message.
 
As background, I'm using a Hauppauge HVR1250 on cable service provided by Cox Cable, which is providing a mix of ATSC channels and MPEG channels across a spread of QAM frequencies from 72 to 122. I originally started using MythTV 0.25, but upgraded to 0.26 (and didn't see any difference as far as this particular behavior goes).
 
I guess I have three questions:
 
[LIST=1]
[*]This seems strongly related to     ticket #9034, which was eventually closed as a duplicate, although     I've had trouble understanding the related ticket (#10178), which     was closed with "Won't Fix". Is there some special trick     to finding possibly-related existing tickets, in order to avoid     creating unnecessary extra work by opening what will turn out to be     a duplicate?
[*]Is there a setup parameter that     could be affecting this?
[*]Am I over-thinking this and I     should just open a ticket?
[/LIST]
 - Mark

---

### Post by Glen_Smith on 2013-10-14
I've got a similar problem.  I use only ATSC channels provided through Cox on an HomeRunHD tuner.  When I start on a non-high-def channel, I get the frame buffer error when I try to switch to a HD channel.  It only happens on live TV and I have no problems recording to HD or non-HD channels.  

I haven't tried the trick for forcing the default channel yet, so I can't comment on that part.  However, I've never loaded any mpeg channels, so I know that's not causing my issue.  It's a standard definition vs. high definition issue for me.

---

### Post by Glen_Smith on 2013-10-14
Oh, and I'm on the latest and greatest version of MythBunutu as of Sept 2013. (So not some old version of Myth).

---

