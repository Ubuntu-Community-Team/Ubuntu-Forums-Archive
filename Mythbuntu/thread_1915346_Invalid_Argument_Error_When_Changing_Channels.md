---
title: "Invalid Argument Error When Changing Channels"
date: 2012-01-26
forum: Mythbuntu
---

### Post by pgjohnson on 2012-01-26
The following snippet from the backend log shows this error sequence;

Channel(/dev/video1) Error: SetInputAndFormat(1, PAL-BG) 
			while setting format (v4l v2)
			eno: Invalid argument (22)
Channel(/dev/video1): SetInputAndFormat() failed

The capture card is a Hauppage 2200 analogue/digital and I seem to have compiled the drivers OK as the card can be tuned to the local analogue station and viewed with VLC mediaplayer.

I have trawled the web and there is little conclusive information on what is happening inside MythTV when attempting to change or setup the channel thereby causing this error.

I have setup the 2200 under VLC player while WATCH TV is playing, but the screen in Mythtv remains blank and VLC plays on.

Any advice would be appreciated.

MythTV Version   : v0.24.1-80-g1de0431
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20110505-1
QT Version       : 4.7.3

Ubuntu 11.10

---

