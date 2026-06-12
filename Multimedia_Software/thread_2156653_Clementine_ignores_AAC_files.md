---
title: "Clementine ignores AAC files"
date: 2013-06-22
forum: Multimedia Software
---

### Post by Mozai on 2013-06-22
When using Clementine (v1.1.1, as per Ubuntu 13.04), it ignores AAC audio files.  I have installed what I am told is the proper gstreamer plugins for playing *aac files, so I'm not sure what I'm doing wrong here.
 
I've been able to coerce it into playing the audio files by adding the containing folder to a playlist, but I am unable to add individual *.aac files to a playlist.  The *.aac files do not appear in the Clementine "Library" list.

Steps to reproduce, without the pointy-clicky.
```
$ cat /etc/issue
Ubuntu 13.04
$ dpkg -l |grep clementine
ii  clementine                                1.1.1+dfsg-1ubuntu1 

$ qdbus org.mpris.clementine /TrackList org.freedesktop.MediaPlayer.AddTrack file:///tmp/horsepower.mp3 false
# current playlist has horsepower.mp3 appended
$ qdbus org.mpris.clementine /TrackList org.freedesktop.MediaPlayer.AddTrack file:///tmp/Equinox_Tori.aac false
# current playlist is unchanged
$ qdbus org.mpris.clementine /TrackList org.freedesktop.MediaPlayer.AddTrack file:///tmp/ false
# both horsepower.mp3 and Equinox_Tori.aac are appended to the current playlist.


```

I also get weird results when querying Clementine via dbus when an AAC file is playing: instead of giving me a mostly empty metadata set with "location: /tmp/Equinox_Tori.aac"  it will give me all the metadata of the last *.mp3 file that played, despite the fact that its the *.aac file that is currently playing.

---

### Post by Yellow Pasque on 2013-06-22
I'd make sure gstreamer0.10 can play them first, and also share output of gst-inspect:
```
sudo apt-get install gstreamer0.10-tools
gst-launch-0.10 playbin uri=file:~/example.aac
gst-inspect-0.10 | grep -i aac
```

---

