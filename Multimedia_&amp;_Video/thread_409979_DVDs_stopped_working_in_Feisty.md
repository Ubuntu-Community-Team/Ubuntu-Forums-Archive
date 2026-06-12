---
title: "DVDs stopped working in Feisty"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by Smaf on 2007-04-15
I have libdvdcss2, libdvdread3, libdvdplay0 and libdvdnav4 installed, and I could watch DVDs fine in Feisty until the kernel updated to 2.6.20-14 and also to 2.6.20-15. I can still watch DVDs if I boot into the 2.6.20-13 kernel, but not in the more recent ones. I've tried reinstalling the above mentioned packages, but to no avail. I can read the contents of dvds fine. When trying to run players from a terminal (vlc, gxine, kaffeine) I get virtually an identical error message output in the terminal:

libdvdnav: Unable to find map file '/home/smaf/.dvdnav/FINAL_FANTASY_VII.map'
libdvdnav: vm: ifoRead_VTS_ATRT failed
libdvdread: Can't allocate memory for file read!
libdvdnav: vm: ifoRead_VOBU_ADMAP vgmi failed

[it gets all the CSS keys here fine, then...]

*** Zero check failed in ifo_read.c:926
    for vts_ptt_srpt->zero_1 = 0x3058

*** libdvdread: CHECK_VALUE failed in ifo_read.c:928 ***
*** for vts_ptt_srpt->nr_of_srpts < 100 ***

libdvdread: Can't allocate memory for file read!
libdvdread: Unable to read PTT search table.
libdvdnav: ifoRead_VTS_PTT_SRPT failed - CRASHING!!!
vlc: vm.c:202: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)


Edit: It appears it affects any media file I try reading from dvds or cds. I can't read anything that's a media file. Trying to read an avi from a cd in vlc output this:
[00000294] access_file access error: read failed (Input/output error)

It won't even let me copy the file to my hard drive. I cannot read mp3s from cds/dvds, either.

---

