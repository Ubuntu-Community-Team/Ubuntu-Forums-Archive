---
title: "Hauppauge HDPVR 1212 - frame rate audio sync video drift problem (60fps vs 59.94)"
date: 2010-04-15
forum: Mythbuntu
---

### Post by davidstoll on 2010-04-15
The HDPVR records from my component input at 720p (satellite service), but the frame rate is 60fps rather than 59.94.  The problem is the audio and video start to drift.  After a half hour recording, the audio/video sync has drifted to several seconds.

The only way to (temporarily) fix this fps problem (which results in an audio drift) is to connect it to a Windows box and run the latest driver/firmware update on it, reboot the Windows box with it still connected and then reconnect it to my MythBuntu.  This normally helps, but not always.

Simply turning the box on and off doesn't help, you have to run through the update in Windows.  It lasts a day or so at 59.94fps and then reverts back to 60.

Can anyone help?

---

### Post by jcroblesemanuelli on 2011-05-16
I know it has been almost a year since your post but wanted to provide you with some information that may help with your problem.  It certainly helped me.  I was having the same problems you mention with the audio drift.  The problem was mainly when watching a cable show in which the audio feed was dolby digital (DD) but then during commercial breaks it would switch to a stereo feed which my receiver automatically detected it.  FYI my setup is as follows:

cable box --component out -->HDPVR
cable box --optical audio out -->HDPVR
HDPVR --USB-->MediaPC
MediaPC --HDMI out -->receiver
Receiver --HDMI out--> TV
Receiver hooked up to 5.1 surround speakers.

When the receiver automatically detected the audio feed switch from DD to stereo (during some commercials) and then switch back to DD for the show the audio drift problems started and would only get worse the longer the show.

Hauppage Support states that the latest drivers 1.5.7 addresses this issue.  But guess what, I had those drivers and was still experiencing the problem.  My solution was to just put my receiver in a simulated surround stereo mode (i.e. no auto-detect of audio feed) and the audio drift problem both in live and recorded tv went away.  With this solution I don't get true surround sound on my tv shows but in all honesty who cares about surround sound on tv shows.  Even in live sports events the only thing you hear through surround speakers are fans cheering so I am ok with this solution.  Other people may not be satisfied with this setup but it works for me.

---

