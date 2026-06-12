---
title: "recording problem in ubuntu"
date: 2008-05-20
forum: Multimedia Software
---

### Post by Dai777 on 2008-05-20
Just installed Hardy and put in recordmydesktop becuase I was having problems with it. A fresh install 5 minutes ago with only one programme installed recordmydesktop. 

Also had problems with xvicap and istanbul. 

Just before I reformatted I did try PCLinuxOS in Virtualbox and it recorded full screen no problem so the problem is with ubuntu.
How do I fix it?

RMD screwsup recording at any size eg 800x600 etc
When trying to use recordmydesktop I get the following error:

dai@dai-desktop:~$ rcordmydesktop
bash: rcordmydesktop: command not found
dai@dai-desktop:~$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 44100Hz
Capturing!
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7e63200]
#4 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0xb8) [0xb7ba4608]
#5 recordmydesktop [0x804e7e6]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6 [0xb7e62cb2]
#4 /usr/lib/libX11.so.6 [0xb7e62fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7e4a74b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6 [0xb7e62cb2]
#4 /usr/lib/libX11.so.6 [0xb7e62fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7e4a74b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7e63200]
#4 recordmydesktop [0x804b159]
#5 recordmydesktop [0x8051083]
#6 recordmydesktop [0x804f21c]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6 [0xb7e62cb2]
#4 /usr/lib/libX11.so.6 [0xb7e62fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7e4a74b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7e63200]
#4 recordmydesktop [0x804b159]
#5 recordmydesktop [0x8051083]
#6 recordmydesktop [0x804f21c]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 recordmydesktop [0x804b174]
#4 recordmydesktop [0x8051083]
#5 recordmydesktop [0x804f21c]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6 [0xb7e62cb2]
#4 /usr/lib/libX11.so.6 [0xb7e62fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7e4a74b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7e63200]
#4 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0xb8) [0xb7ba4608]
#5 recordmydesktop [0x804e7e6]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0x1a5) [0xb7ba46f5]
#4 recordmydesktop [0x804e7e6]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6 [0xb7e62cb2]
#4 /usr/lib/libX11.so.6 [0xb7e62fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7e4a74b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7e63200]
#4 recordmydesktop [0x804b159]
#5 recordmydesktop [0x8051083]
#6 recordmydesktop [0x804f21c]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 recordmydesktop [0x804b174]
#4 recordmydesktop [0x8051083]
#5 recordmydesktop [0x804f21c]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6 [0xb7e62cb2]
#4 /usr/lib/libX11.so.6 [0xb7e62fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7e4a74b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7e63200]
#4 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0xb8) [0xb7ba4608]
#5 recordmydesktop [0x804e7e6]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0x1a5) [0xb7ba46f5]
#4 recordmydesktop [0x804e7e6]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6 [0xb7e62cb2]
#4 /usr/lib/libX11.so.6 [0xb7e62fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7e4a74b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7e63200]
#4 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0xb8) [0xb7ba4608]
#5 recordmydesktop [0x804e7e6]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0x1a5) [0xb7ba46f5]
#4 recordmydesktop [0x804e7e6]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a0981e]
#2 /usr/lib/libX11.so.6 [0xb7e62518]
#3 /usr/lib/libX11.so.6 [0xb7e62cb2]
#4 /usr/lib/libX11.so.6 [0xb7e62fcf]
#5 /usr/lib/libX11.so.6(XNextEvent+0x8b) [0xb7e4a74b]
#6 recordmydesktop [0x8051776]
#7 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#8 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a09767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a098b1]
#2 /usr/lib/libX11.so.6 [0xb7e62421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7e4a734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d284fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ae1e5e]

---

### Post by Dai777 on 2008-05-20
I finally figured it out - needed to add position_fix=1 to the options of the snd-hda-intel kernel module driver in /etc/modprobe.d.

not sure if this will fix my problem and even if it does I don't know how to fix it.

---

### Post by Dai777 on 2008-05-20
just went back to gutsy as a fresh install and recordmydesktop works fine.
did a full screen screen recording and a smaller 800x600 recording no problem.

---

