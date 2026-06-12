---
title: "MP3 Postcasting &amp; RSS Radio"
date: 2013-03-07
forum: Multimedia Software
---

### Post by msutcliffe on 2013-03-07
Afternoon

I have for some time been using mythtv to record radiobroadcasts, and podcast them to my iphone.  I use RSS Radio on the iphone to listen to the podcasts.

This used to work perfectly.  Some time ago (not sure when), the MP3 files played within RSS radio stopped seeking within the file.  Downloads from bbc podcasts etc work perfectly, but not the mp3 files I create locally.

It is the same if I manually convert a file to M4a, aac etc format.

I'm using the command in the mythexport MP3.pm script:
system("avconv -i \'$self->{_inputFile}\' -y -acodec libmp3lame -ac 2 -ab 128k -ar 48000 -vn \'$self->{_outputFile}$self->{_extension}\'");

Any help/ideas appreciated.

---

