---
title: "VLC DVB-T Network Streaming"
date: 2011-08-30
forum: Multimedia Software
---

### Post by xannen on 2011-08-30
Currently, a setup to play DVB-T (or live digital TV) using VLC works properly.

After some google search on how to VLC network streaming, attempts to stream the DVB-T across local area networking (LAN) somewhat works.  There were cases where the receiver vlc client couldn't connect and gave error.  But there were cases where such errors were not evidence (at least not reported), but there was neither any video or audio being displayed, and the stop/play/pause etc buttons clickable (which did nothing as there were no video and audio to stop/pause etc).

It would be appreciated if there is a definitive guide to making this work.

Intended software use:

Ubuntu 11.04 or higher (as 11.10 should be out soon)
VLC: version 1.1.9 or higher

Please advise.

---

### Post by johnoly99 on 2011-08-30
Good god, please someone answer this!  I can't get VLC to stream to a website anymore with 11.04.  Really regretting moving up to 11.04.

---

### Post by xannen on 2011-08-31
Bump

---

### Post by thewolfman on 2011-09-01
Have you installed "mozilla-plugin-vlc", you can get it via "getdeb":

[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

Reload once the ppa is installed and search for the plugin.

Regards thewolfman:P

PS: for general DVB-T viewing; I would use either "me-tv" or "kaffeine", they are both far better than VLC for DVB-T reception!!.

---

### Post by xannen on 2011-09-01
> **thewolfman said:**
> Have you installed "mozilla-plugin-vlc", you can get it via "getdeb":

[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

Reload once the ppa is installed and search for the plugin.

Regards thewolfman:P

Please elaborate on how mozilla-plugin-vlc assists in solving my problem?

---

### Post by xannen on 2011-09-01
Test on streaming a video file worked via RTP.

After much searching on google and VLC forum there seems to be no supplied response to make TV network streaming work.  Similar threads to this were on the VLC forum, however, no workable solution was given. In most case no response was given after such question was asked.

At this point in time, it is even possible for VLC version 1.1.9 to play DVB-T and stream it simultaneously on LAN?

Could a VLC / Multimedia / Networking expert provide a detail insight or preferably a tutorial on how to stream live DVB-T on a local area network?

Details on setting the appropriate protocol/port, media format (e.g. mpeg, asf, etc?), setting bitrate and other media or networking details that influence the workability or quality of the streaming would be appreciate.  And as mentioned afore, if a tutorial format for these instruction would be highly desirable.

---

### Post by xannen on 2011-09-02
Bump

---

### Post by thewolfman on 2011-09-02
Hi,

go to Edit > Preferences > Applications and have a look there, you may have to change which app runs what and it may solve your problem!!.

Regards thewolfman:P

---

### Post by xannen on 2011-09-02
To: thewolfman

Are you implying that the streamed media is to be viewed in Firefox or a web browser?  That is not the intent.



The intended setup is to have a server using VLC (version 1.1.9+) to stream live digital TV across a local area network, and then another (client) computer on the network is to pick up the streamed media using VLC also.

Thus far, the server computer has installed the appropriate DVB-T hardware and firmware.  A file containing my local DVB-T channels is generated with the utility scan.  VLC is capable of opening this file as a playlist, and play or stream each listed TV channel.

The next goal, which is the current problem, is the inability or misconfiguration to allow streaming live digital TV from one VLC to another VLC across a local area network.

The LAN streaming occurs from one ubuntu 11.04 computer to another ubuntu 11.04 computer.  Both computers use VLC 1.1.9 application.  Please provide advice and preferably exact details on recommended setup.  For example:

Which protocol is viable and optimal for streaming: http, rtp, rtsp, etc?

Which encoding method is supported for VLC ubuntu to VLC ubuntu LAN streaming?  Explanation on bitrate, channels, frame rates, caching, etc would be highly appreciated.

Search on this forum, googling, and even on the VLC website and its forum has not yield much explanation on how to configure how to achieve this set up in a workable manner.

---

### Post by thewolfman on 2011-09-03
What I meant was that if you install the VLC Mozilla plugin, you can use that to view VLC via Firefox. As I am not sure what you intend to view with VLC, I cannot really add any more to this thread!!.

Regards thewolfman:P

---

### Post by xannen on 2011-09-04
Bump

---

### Post by xannen on 2011-09-06
Bump

---

### Post by xannen on 2011-09-06
Bump

---

### Post by xannen on 2011-09-07
Bump

---

### Post by hydrox24 on 2012-01-20
I bump this aswell, needs to be answered. Perhaps try the VideoLan forums too?

---

### Post by sbjaved on 2012-11-04
Looking to set up a VLC TV streaming setup. Xannen please post the steps for the server side setup. If you work out the client side issues please post these too. I'm runnning 12.04

---

