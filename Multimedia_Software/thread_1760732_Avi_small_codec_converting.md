---
title: "Avi small codec converting"
date: 2011-05-17
forum: Multimedia Software
---

### Post by whynot on 2011-05-17
Hi
I need to convert an avi file that is over 150MB to small something like 20mb file.I know it will be some quality lost.But i need to do it.There is a player called VLC that has convert options. I have tried to convert to Divx3+Mp3 (ASF) but im geting this error. Is there any way to convert very small file.

```

Streaming / Transcoding failed:
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG Audio layer 1/2/3.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.

```

---

### Post by andrew.46 on 2011-05-18
It looks as if your shared libavcodec has been stripped of some of its more useful codecs. I have not tried this with vlc but I suspect you would be best to add the Medibuntu repository:

```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

and then add a beefed up copy of libavcodec:

```

sudo apt-get install libavcodec-extra-52

```

and this should get your encoding going, I confess again that I have not tested this with vlc...

---

