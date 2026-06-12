---
title: "How to load a new module on kernel with a different name"
date: 2013-01-03
forum: Multimedia Software
---

### Post by evildeejay on 2013-01-03
Hi all,
I want to use two video-acquire easycap60 at the same time.
But when I try to use both of them the second one doesnt start.
I think that is a conflict between the two cards and for this I want to load two different modules in the Kernel.
If i type 'sudo modprobe easycap' it loads the module but i can run only one card, when i try to run the second one it doesnt work.
Is it possibile to load another module for easycap with a different name?
I saw there is the option '-o'
I tried with 'sudo modprobe easycap -o easycap0' but it says 'invalid use of -o'
Can you help me?
Thanks in advance.
Marco

---

### Post by tgalati4 on 2013-01-03
A quick google search shows that there are some options to use with the easycap module:

[http://jared-oberhaus-tech-notes.blogspot.com/2011/11/easycap-dc60-and-ubuntu-1110.html](http://jared-oberhaus-tech-notes.blogspot.com/2011/11/easycap-dc60-and-ubuntu-1110.html)

What you want is /dev/video0 and /dev/video1, so you want to call your devices video0 and video1 so that they show up in various video applications.

It's possible that the driver or udev rules will only create one video device.  You might need some udev rules to check for existing device and then create a second device.  That's beyond my knowledge at the moment.

[http://www.kernel.org/doc/readme/drivers-staging-easycap-README](http://www.kernel.org/doc/readme/drivers-staging-easycap-README)

---

### Post by evildeejay on 2013-01-03
Hi and thanks for reply.
The driver creates correctly video0 and video1 under /dev folder.
But when I can see only one stream at a time.
While I'm watching the first e.g. /dev/video0 and i run my program with /dev/video1, the stream of video0 stops and restarts itself while /dev/video1 is completely black.
The only way to see video1's stream is:
close video0 stream
'sudo rmmod easycap'
'sudo modprob easycap'
and run again video1.

I'd like to load a module 'easycap0' in kernel for video0 and 'easycap1' for video1.

---

