---
title: "Radeon HD 3200 - Strang Problem!"
date: 2011-08-03
forum: Multimedia Software
---

### Post by nmxdaven on 2011-08-03
*Strange

I've been having a reoccurring problem with my system thats driving me a little crazy. 

My system will run perfectly fine for 8-24 hours. At some point during this time period, I will have a strange problem with media playback.

1. System will be working normally.
2. At some (Seemingly random) point when opening or as the system is playing back a media file, MediaPlayer will crash. It wont open up any additional files. Every time I try to load a new file, Media player will briefly open with no picture, then just close (about half a second)
3. If I try to open any media files (after 2 has happened) it will be the same thing. VLC will give me audio for some reason, but no video. 
4. This is the case with every type of video file I try to open. It doesn't matter what format, what file size, what playback program I use. 

The errors I get, (after the video has stopped playing back of course) is

**Totem**
> The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)                      [B]VLC
[/B]> [0x9a6800] signals interface error: signal 17 overriden (0x7f0b5dbcc450)
[0x9a6800] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x9a6800] signals interface error: signal 17 overriden (0x7f0b5dbcc450)
[0x9a6800] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]                      The only thing that seems to cure it is a hard reboot. 

Im running on a HP Touchsmart with a Radeon HD 3200. PLENTY of drive space on all partitions. 

Thanks for any help!

---

