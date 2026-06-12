---
title: "Video not working in Skype after upgrading to Oneiric"
date: 2011-10-17
forum: Multimedia Software
---

### Post by alexmoon on 2011-10-17
Hi,

My video has stopped working on Skype after upgrading to Oneiric with my Mac. The laptop does recognise the webcam - I tested it using [these]("http://ubuntuforums.org/showthread.php?t=1745517&highlight=mac+webcam") instructions:
"You can test your camera after installing vlc by entering the following in Terminal:
vlc v4l2:///dev/video0
...
In Cheese I get three resolution options in Edit -> Preferences: 640x480, 352x288, & 320x240. I changed it from 640x480 to something else, and it worked. Then I changed it back to 640x480, and it still worked."

It works with both VLC and Cheese. 

However, when I try to get it working with Skype I continually get a black screen. I've tried following [these]("http://ubuntuforums.org/showthread.php?t=1731392") instructions, which were working before:
"Try to load skype from terminal with
Code:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"

But no luck - I keep getting a black screen, and when I type it into the terminal I get the message: 
"ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored."

I've looked up the latter error, but couldn't find any solutions that worked.

Any help would be greatly appreciated!

Thank you!

---

### Post by stefmorp on 2011-10-18
In Oneiric the file is in a new location:

/usr/lib/i386-linux-gnu/libv4l/

So the command now is:


LD_PRELOAD="/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so" skype

Enjoy!
Stefano

---

### Post by alexmoon on 2011-10-18
YAY! Thank you!

---

