---
title: "iPodVideoEncoding wiki page: change required?"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by malibu on 2008-01-17
How do the wiki pages get corrected?  I believe there is a changes required on the iPodVideoEncoding page.  The ffmpeg command given:

ffmpeg -i input_file.avi -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec libfaac -ab 192k -s 320x240 -aspect 4:3 output_file.mov

..doesn't work because the -bufsize field is now specified in bytes instead of kilobytes.  I had to change it to -bufsize 4096k or it complains about the VBV buffer being too small.  Also, the build instructions on the page don't seem to work in gutsy.  I followed them and ffmpeg could still not find the libfaac audio codec.  I followed alternate instructions I found for building from the SVN onto gutsy and it worked.

---

