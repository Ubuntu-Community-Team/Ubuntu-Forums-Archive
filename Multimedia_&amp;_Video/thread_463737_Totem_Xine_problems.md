---
title: "Totem Xine problems"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by No Whammies on 2007-06-04
I noticed that even though all my codecs are loaded and functioning (all work perfectly in SMPlayer) Totem crashes on some wmv files.  Here's the terminal message that accompanies the crash.




External func OLEAUT32.dll:8
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU   
Decoder is capable of YUV output (flags 0x1b)
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 87 error_code 2 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Anyone have ANY idea what the problem is, or how to fix it?

---

### Post by pmj on 2007-06-04
Hope that Xine's wmv compatibility is better when you install the next version of Ubuntu half a year from now. Really, there's not much you can do about this, other than play the problem videos in another player.

---

### Post by Bablefish on 2007-06-04
There is even a more simplier solution it's called Automatrix it gives you the codecs and plugins for practically everything

---

