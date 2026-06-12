---
title: "How to stream video in (not from!) Mythbuntu?"
date: 2010-12-10
forum: Mythbuntu
---

### Post by Hex on 2010-12-10
Hey, guys,

I keep finding info how to stream media from Mythbuntu, but I can't seem to find information how to add a media stream and watch it.

Our ISP offers free channels that can be played in VLC without a problem. They are in the format [http://ip: port](http://ip: port) with different ports for different channels.

How can I add them all and watch them from Mythbuntu? Thank you!

---

### Post by tgm4883 on 2010-12-10
> **Hex said:**
> Hey, guys,

I keep finding info how to stream media from Mythbuntu, but I can't seem to find information how to add a media stream and watch it.

Our ISP offers free channels that can be played in VLC without a problem. They are in the format [http://ip: port](http://ip: port) with different ports for different channels.

How can I add them all and watch them from Mythbuntu? Thank you!

You probably want to look at [http://www.mythtv.org/wiki/IPTV](http://www.mythtv.org/wiki/IPTV)

---

### Post by Hex on 2010-12-11
> **tgm4883 said:**
> You probably want to look at [http://www.mythtv.org/wiki/IPTV](http://www.mythtv.org/wiki/IPTV)

Yes, thank you for the technical information, however, I was asking how to actually add a list of RTSP streams in Mythbuntu and watch them? Or maybe it's not supported?

edit: Seems like what I need is mythstream, although installation seems rather tough. Any links would be greatly appreciated.

---

### Post by tgm4883 on 2010-12-11
It looks like you add it in the backend as a network recorder  

[http://www.mythtvtalk.com/network-recorder-m3u-file-format-7431/](http://www.mythtvtalk.com/network-recorder-m3u-file-format-7431/)

[http://ubuntuforums.org/showthread.php?t=1321801](http://ubuntuforums.org/showthread.php?t=1321801)

mythstream shouldn't be needed for this

---

### Post by ian dobson on 2010-12-11
Hi,

I use a dreambox recorder and use the "freebox" iptv tuner to grab the video stream from the recorder.

You need to create a iptv tuner on the backend and point it at a m3u file that contains a list of the channels/ip addresses. This will create the required infomation in myth and add the channels.

It's a bit of a pain in the butt to get it working but for me it was worth it.

edit: Here's a good howto:- [http://avenard.com/iptv/MythTV.html](http://avenard.com/iptv/MythTV.html)
Regards
Ian Dobson

---

### Post by Hex on 2010-12-12
> **ian dobson said:**
> Hi,

I use a dreambox recorder and use the "freebox" iptv tuner to grab the video stream from the recorder.

You need to create a iptv tuner on the backend and point it at a m3u file that contains a list of the channels/ip addresses. This will create the required infomation in myth and add the channels.

It's a bit of a pain in the butt to get it working but for me it was worth it.

edit: Here's a good howto:- [http://avenard.com/iptv/MythTV.html](http://avenard.com/iptv/MythTV.html)
Regards
Ian Dobson

Thanks for the reply. I've seen this howto, however, my ISP only provides a list of separate channels, not an m3u file. Any idea if I can create the m3u file?

---

### Post by Hex on 2010-12-13
@ian, thanks for the reply, I've stumbled on [http://www.mythtv.org/wiki/Dreambox-NetworkRecorder](http://www.mythtv.org/wiki/Dreambox-NetworkRecorder)

According to it, MythTV can't stream over http, so I have to start a vlc daemon to convert it to udp. Seems like too much hassle for streaming a couple of channels. Thanks for the help!

---

### Post by ian dobson on 2010-12-13
Hi,

Maybe anoth way would be to start vlc on the frontend (you just need to edit the xml menu files to add a menu option) so that it starts vlc with the required URL as part of the command line.

Not sure how easy that would be/how good you hacking skills are but that would be an easy way out.

Regards
Ian Dobson

---

### Post by Hex on 2010-12-26
Thanks, that's a good idea.

---

