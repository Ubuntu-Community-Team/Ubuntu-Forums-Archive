---
title: "Gstreamer won't play some mp3 files"
date: 2009-06-24
forum: Multimedia Software
---

### Post by anishmangal2002 on 2009-06-24
There are **some** mp3 files that won't play with any gstreamer based player like exaile, rhythmbox, songbird but plays with vlc.

The codec information for these files as reported in vlc is as follows.

Codec: mpga
Language: 
Type: Audio
Channels: 1
Sample Rate: 22050 Hz
Bitrate: 32kb/s

There's seemingly nothing wrong but these files just don't play.
Most of the files seem to play both in vlc and gstreamer players and the problem is only with a specific set of files. For example, a file with following info works with both.

Codec: mpga
Language: 
Type: Audio
Channels: 2
Sample Rate: 44100 Hz
Bitrate: 128kb/s

Any comments! :confused:

------------
UPDATE
------------

ISSUE PARTLY RESOLVED

I had this problem while I was using bluetooth headphones. On normal speakers, gstreamer was able to play the files. 

Probably, the reason gstreamer wasn't able to play track was because it contained a single audio channel and the bluetooth profile didn't support it.

However it still doesn't explain why vlc was able to play it while using bluetooth headphones.

**_Could this be a bug. Has anyone tried yet to play a single channel audio track on bluetooth headphones using gstreamer?_**

I'm attaching my .asoundrc below just for reference (bluetooth adress replaced by x's)

pcm.bluetooth {
    type bluetooth
    device xx:xx:xx:xx:xx:xx     
    profile "hifi"	
}

Regards,
Anish

---

