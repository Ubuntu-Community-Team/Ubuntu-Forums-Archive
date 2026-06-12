---
title: "DeVeDe, isos too small from m4v files"
date: 2011-03-23
forum: Multimedia Software
---

### Post by Wobblybob on 2011-03-23
Hi All, I'm finding that if I burn m4v files created in handbrake of about 1.4Gb using DeVeDe that the resulting iso image is 80Mb yes Meg. When I play them in VLC they are either chopped short or run too fast and short. If I convert them from m4v to avi then DeVeDe creates the correct sized working iso. It's a solution but who wants to convert files twice when DeVeDe should just do it. All worked ok just a couple of weeks ago. I've tried reverting to previous versions of both handbrake and DeVeDe with no luck and am beginning to think it may be an ffmpeg problem.

running this process on Maverick Xubuntu but I suspect the Ubuntu version is not the problem. Handbrake is from the ppa

---

### Post by Wobblybob on 2011-03-23
Running devede from the command line I get

> mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
/usr/lib/devede/devede_other.py:685: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  tree.add_from_file(filename)
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Skipping frame!

Skipping frame!

[pages worth of Skipping frame]

Skipping frame!

Skipping frame!

Skipping frame!

Skipping frame!
Launching program:  dvdauthor -x /home/bob/Videos/test.xml
elemento:  /usr/bin

So apart from a missing mplayer socket problem, a deprecated python reference it's skipping lots of frames no wonder the results are poor. :)

---

### Post by Wobblybob on 2011-03-23
ok so I think I've now solved this after days of testing, the solution seems to be to not convert m4v's in handbrake using the Framerate option [Same as Source], so in the Video Tab you need to select an actual frame rate for the conversion. I've tested this with two different clips from DVD's and this has now let DeVeDe create a correcty sized iso image which plays perfectly in VLC. I hope this helps out others with the same problem.

[IMG]http://i1234.photobucket.com/albums/ff411/orange1942/Tech/Handbrake.png[/IMG]

---

