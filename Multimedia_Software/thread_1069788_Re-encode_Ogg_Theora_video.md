---
title: "Re-encode Ogg Theora video"
date: 2009-02-14
forum: Multimedia Software
---

### Post by DPic on 2009-02-14
Sometimes when i try uploading .ogv files from Cheese to YouTube they don't work (no matter how many times i try) with a "failed to process" error. What's the easiest way to re-encode the video so that it may work?

_***Update: ***_This command saved me: [http://www.linuxrising.org/files/transcode2oggt](http://www.linuxrising.org/files/transcode2oggt)
gst-launch gnomevfssrc location=$1 ! decodebin name=decode decode. ! ffmpegcolorspace ! theoraenc ! queue ! oggmux name=mux ! gnomevfssink location=$2 decode. ! audioconvert ! vorbisenc ! queue ! mux.

Replace "$1" with the input file and "$2" with the output

---

