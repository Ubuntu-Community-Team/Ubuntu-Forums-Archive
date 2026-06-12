---
title: "totem: insufficient resources for operation"
date: 2009-05-15
forum: Multimedia Software
---

### Post by AGSzabo on 2009-05-15
when starting a repaly of any media in totem there is a good replay in the first two secondes, then totem quits itself with the folllowing error output:

```
calla@dunwyn:~$ totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
import sha
input_dvb: continuing in get_instance
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

(totem:13160): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(totem:13160): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
(Details: serial 100 error_code 11 request_code 133 minor_code 19)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)
calla@dunwyn:~$ man totem
calla@dunwyn:~$
```

this is curious because before install of the dvb-plugins the replay of mpg, mp3 and youtube worked perfectly.

whats solution?

i found this same problem through the forum search and did see that the same prob ocurs with other players as well but w/o solution...

regards,
Szabo

---

### Post by wprime on 2009-05-22
Bump - anyone have a solution for this issue?

---

### Post by davidwillis on 2010-05-10
I have the same problem with 10.04.  I have searched, and most say it is a driver problem for intel video chipsets... I am using an nvidia card.

---

### Post by davidwillis on 2010-05-10
I found some more information

>  Re: Video players (Totem, VLC, etc.) fail with BadAlloc error
Thought I'd post my solution to this error. I'm using the i810 graphics driver, and my video card uses shared memory, which seems to be causing the error. My problem was that all movie players crashed when playing any video with a resolution higher than 640x480. After adding two lines to my xorg.conf file, I can finally play my 1024x768 screencasts.

I added these lines to Section "Device" in xorg.conf:
Code:

        Option  "VideoRam"      "65536"
        Option  "CacheLines"    "1980"

Related to bug #4229
__________________

I have an nvidia geforce 7300 with 128mb of ram.  So I doubled the videoRam in that example.  It did help.  Here is the strange thing.  If I have nothing open, I can play any videos full screen, but when I open firefox, and google chrome I can only play a video with a small window.  And the more I open the smaller the window needs to be before it crashes.

Adding these options in xorg helped for sure, but I don't know if there is a way to fix it so it works even when other programs are open.

---

### Post by davidwillis on 2010-05-26
All works fine with fedora 13 running the nouveau driver with the experimental 3d effects.  So now I know it can be solved.  Now to try and get it to work in ubuntu

---

