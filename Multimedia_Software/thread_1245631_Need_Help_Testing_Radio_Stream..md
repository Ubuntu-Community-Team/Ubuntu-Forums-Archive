---
title: "Need Help Testing Radio Stream."
date: 2009-08-20
forum: Multimedia Software
---

### Post by Trapper on 2009-08-20
Ubuntu 9.04 X86_64

I have a radio stream that worked just fine several months ago but no longer works for me. Doesn't work in my 32 bit install either. Nor does it work in Fedora anymore. I've tried just about every audio app and FF plugin that exists. I have all the gstreamer bads & ugly too. Also all available windows codecs. The stream does work in windows.

The link I am trying to hear is:

[http://wqam.com/streamer/index.php](http://wqam.com/streamer/index.php)

I get the flash ad prior to the actual stream okay. I just get nothing after it.

If someone will try the link and if they successfully get the audio stream to play, I'd appreciate a posted reply and perhaps what they were able to access the audio with.

Thanks,
   Trapper

---

### Post by Trapper on 2009-08-21
An added Note:

This seems to be a JW Media Player situation. I know previously in the past after the flash ad played a player popped up in the window and went right into the audio stream with no difficulty. The player no longer pops up in the window.

Everything works normally on winXP with FireFox. After the flash ad it connects to a StreamTheWorld server and audio plays okay. From all I can tell this is a flash audio stream.

---

### Post by howefield on 2009-08-21
To confirm the player automatically pops up in windows but not Ubuntu, at least not in mine.

You can bypass the advert by pasting in the streams address into your browser. Add the following to the end of your aforementioned link and see what happens..

?displaystreamer=true

---

### Post by Trapper on 2009-08-21
> **howefield said:**
> To confirm the player automatically pops up in windows but not Ubuntu, at least not in mine.

You can bypass the advert by pasting in the streams address into your browser. Add the following to the end of your aforementioned link and see what happens..

?displaystreamer=true

Yup. This gives me the player and the live audio stream. 

[http://wqam.com/streamer/index.php?displaystreamer=true](http://wqam.com/streamer/index.php?displaystreamer=true)

I appreciate the tip. I'll just bookmark the link as it is above.

I have a couple of Canes games that are radio only this season and I was absolutely dreading having to install Windows just for that.

I am curious. Is there something that can be done on the server side by the wqam folks that will circumvent the end user having to do the ?displaystreamer=true routine?

---

### Post by howefield on 2009-08-21
> **Trapper said:**
> I am curious. Is there something that can be done on the server side by the wqam folks that will circumvent the end user having to do the ?displaystreamer=true routine?

Most likely, but I'd expect they'll have other things to worry about... hopefully :)

---

### Post by Trapper on 2009-08-22
> **howefield said:**
> Most likely, but I'd expect they'll have other things to worry about... hopefully :)

I'm just trying to determine if this ?displaystreamer=true "fix" is something that can be eliminated with perhaps a simple script hack on the server side or something of that nature. The link works correctly in Windows without the addition of  "?displaystreamer=true" but it apparently doesn't in linux. I am just wondering why the difference. The script? The flash player? etc.

If it is something that could be quickly adjusted in the server script I have no doubt the webmaster  would be open to making the adjustment.

I do know this listen live routine at wqam used to work without a hack just like it works in Windows now. There's got to be some specific reason for the abrupt change. Finding out what it is appears to be another matter.

---

