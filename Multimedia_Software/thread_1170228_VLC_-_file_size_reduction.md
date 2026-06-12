---
title: "VLC - file size reduction"
date: 2009-05-26
forum: Multimedia Software
---

### Post by MeKino on 2009-05-26
Hi,

I'm using vlc to stream video to a file. Using the default settings a two-hour recording results in a 5.3 Gb file.

So, I have two questions:

1. What parameter do I change to reduce the file size during recording to, say, 1.5 Gb per hour?

2. Is there a method to reduce the file size after recording (not just compression) such that I could fit a 5.3 Gb, 2 hour recording onto a dvd?

Thanks in advance.

---

### Post by SteveDee on 2009-05-26
> **MeKino said:**
> Hi,

I'm using vlc to stream video to a file. Using the default settings a two-hour recording results in a 5.3 Gb file.

So, I have two questions:

1. What parameter do I change to reduce the file size during recording to, say, 1.5 Gb per hour?

2. Is there a method to reduce the file size after recording (not just compression) such that I could fit a 5.3 Gb, 2 hour recording onto a dvd?

Thanks in advance.

You can lower the video bitrate (vb in the following example) or scale the picture down (say scale=0.8) to reduce the file size.

Example: To view & capture from a camera (MPEG-4) use a command line such as:-
vlc -width=1000 v4l2:///dev/video0:norm=pal:input=1 --sout '#duplicate{dst=display,dst="transcode{vcodec=mp4v,vb=4096,scale=1,acodec=mp4a,ab=64,channel=1}:duplicate{dst=std{access=file,mux=mp4,dst=/home/steve/Videos/myVideo.mp4}}"'

For existing video files you could use "Convert" from VLC gui (Media > Convert > File ...and so on).

---

### Post by MeKino on 2009-05-26
Thanks for the reply, but I should have said I was using vlc in pvr-mode to capture tv.

Here is the script I use:


cvlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=855250 :pvr-bitrate=-1 :pvr-caching=300 :pvr-width=-1 :pvr-height=-1 :pvr-framerate=-1 :pvr-keyint=-1 :pvr-bframes=-1 :pvr-bitrate-peak=-1 :pvr-bitrate-mode=0 :pvr-audio-bitmask=-1 :pvr-audio-volume=-1 :pvr-channel=0 --sout file/ps:///home/kino/vlcmovie-%d-%m-%Y-%H:%M.mpg

which of the above would be best to change?

---

### Post by SteveDee on 2009-05-26
> **MeKino said:**
> Thanks for the reply, but I should have said I was using vlc in pvr-mode to capture tv.

Here is the script I use:


cvlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=855250 :pvr-bitrate=-1 :pvr-caching=300 :pvr-width=-1 :pvr-height=-1 :pvr-framerate=-1 :pvr-keyint=-1 :pvr-bframes=-1 :pvr-bitrate-peak=-1 :pvr-bitrate-mode=0 :pvr-audio-bitmask=-1 :pvr-audio-volume=-1 :pvr-channel=0 --sout file/ps:///home/kino/vlcmovie-%d-%m-%Y-%H:%M.mpg

which of the above would be best to change?

I'd suggest you experiment with the pvr-bitrate.

The "-1" means default. Try setting it to 1024. That will hopefully give a dramatic reduction in file size (to confirm you have the right parameter), but may not provide acceptable quality.

---

