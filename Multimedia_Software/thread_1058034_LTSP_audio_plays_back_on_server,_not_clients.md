---
title: "LTSP: audio plays back on server, not clients"
date: 2009-02-02
forum: Multimedia Software
---

### Post by djsephiroth on 2009-02-02
Using "movie player" and VLC. Everything runs like a charm on the server (8.10 x86 desktop). Audio for Youtube video plays on server for some odd reason; video plays on client as intended. "movie player" has the same issue. Using latest VLC with the VLC pulse audio plugin. 

On a side note, "movie player" will now start to open the .mkv file I've been using as to test video playback, but will close before playing any audio or video. File loads, then... crash. It only did this after I played the file from the server right after I had played it once on the client. Server happily plays the file with no issues.

Server is a Pentium D-based HP desktop. Client is an old Dell Optiplex GX1 (PII-based).

---

### Post by djsephiroth on 2009-02-04
Hurr durr: [http://wiki.ltsp.org/twiki/bin/view/Ltsp/Sound](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Sound)

Not fixed yet, but this info should help immensely.

---

### Post by djsephiroth on 2009-02-05
*echo $ESPEAKER* returns a blank line when run on the server.

On the client, the sound cards that show up appear to be the two that are physically in the server. Testing OSS causes tones to come out of the server. Testing ALSA or Pulse Audio Server causes an error. For Pulse Audio, the error is "connection refused". Is there something I forgot to set up on the server apropos Pulse Audio? I've got the proper packages installed (via *sudo apt-get install ltsp-server-standalone*).

---

### Post by djsephiroth on 2009-02-05
Seems to be an issue with the clients' hardware, not the configuration on the server side. The old Optiplex GX110 does not list any sound cards except for the ones on the server. Sounds that should play on this old clunker play on the server instead. However, sounds that should play on a newer P4-based Dell Inspiron in the LTSP network do in fact play on the Inspiron. I suspect that the issue is simply that the Optiplex's built-in sound is crufty and not supported out of the box, and that therefore I just need the proper kernel module for the Optiplex in order to enable the sound card. Mostly solved... will update after more poking and prodding. Will also test the Inspiron's ability to play my .mkv test file.

---

### Post by haddog on 2009-02-15
DJ. I have a similar issue. Did you get your issue resolved? I have 3 Dell optiplex GX200's w/256MB ram that I am using as thin clients.

When I start the thin clients and then sign on,  I hear the Ubuntu startup music play on each of them. There must be an internal speaker in the pc's. But when trying play a video that is played thru a flash plugin in firefox, I get no audio.

The video and audio works fine on the LTSP server.

---

### Post by haddog on 2009-02-15
Found this regarding sound on thin clients at the Edubuntu FAQ. Resolved my audio not playing on you tube videos, etc issue.

[https://help.ubuntu.com/community/EdubuntuFAQ](https://help.ubuntu.com/community/EdubuntuFAQ)

"Sound doesn't work on flash applets (eg youtube videos) on my thin clients!

This issue was a long-standing problem with the proprietary Adobe Flash Plugin. It has recently been fixed, although the fix did not make it into Edubuntu 7.04 (Feisty Fawn). The simplest way to fix this issue is to install the libflashsupport package on your server:

sudo apt-get install libflashsupport

---

### Post by djsephiroth on 2009-02-24
Whoops, I posted the results to facebook and not to Ubuntuforums. Root of the issue: it was just a crappy old Dell GX series. Looks like no sound card was ever working on it in the first place. All other clients work perfectly and do not exhibit the issue. Case closed.

---

