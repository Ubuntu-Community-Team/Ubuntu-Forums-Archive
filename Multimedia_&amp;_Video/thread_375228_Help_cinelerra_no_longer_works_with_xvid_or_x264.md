---
title: "Help cinelerra no longer works with xvid or x264"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by cor2y on 2007-03-03
Hello.
A while back i installed the latest Deb version of cinelerra-cv and have only now gotten around to using it on some DV video i converted from RAW DV to both X264 and xvid using the previous version of the software.


When i launched cinelerra-cv it gave a message for the XVID encoded file along the lines of
> 
virtual int FileMove::read_frame(VFrame*):quicktime_read/quicktime_decode_video failed. result:

For the X264  file from the terminal this was what i got
> new vcodec: couldn't find codec for "h264"


So ok i thought maybe because i used the vanilla deb install
 maybe i need to compile it myself with xvid and x264 listed via configure.
So i uninstalled the deb , and followed the instructions on how to compile listed here. configure found my install of xvid and x264 (both compiled form source just to be sure) so i installed and it still gives the same error.

The only difference between when i used cinelerra and now is
1) The version used
2) I used the latest xvid  source and x264  sources, for xvid 1.1.2 and x264 the latest from svn both of which were recognized 
in ./configure with cinelerra.

Before in the earlier version i was able to import and edit both xvid and x264 files as well as DV files now i can't edit xvid or x264 encoded files.

Anyone have any idea what could be wrong?
They are both open source codecs.

---

