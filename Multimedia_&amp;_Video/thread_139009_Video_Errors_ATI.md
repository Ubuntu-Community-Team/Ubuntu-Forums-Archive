---
title: "Video Errors? ATI"
date: 2006-03-03
forum: Multimedia &amp; Video
---

### Post by wiley00 on 2006-03-03
I finally decided to switch over to the dark side this weekend after grabbing another hard drive from newegg.
I downloaded the x64 version of Ubuntu (I have an athlon 64 chip), partitioned the new drive with the Live disc and went about configuring.
I am ver new to the whole linux scene, but have always been around OpenSource software so I figured Id give it a shot.
A few questions I have gathered so far...
Firstly..my ATI card. I believe everything is good to go, but is there anyway to check to see if it is enabled?
I've been to the deivce manager which really wasnt any help, but from the looks of things (1280x1024 reso, 24bit color) everything seems to be in order.

Another question I have is regarding the hideous noise coming from my computer...I narrowed it out to 'around the PCI area' of the motherboard...the sound starts during boot up of ubuntu (ASPA 1 or whatever) and doesnt let up...I think its either my vid card or network jack, but thats the general area. Anyone have any ideas, bad video driver or something to that effect...

And my last question.
I have a creative Extigy external sound card. Got it to work just fine with ubuntu, but went ahead and booted onto my windows drive (to play some games) and cant get any sound for the life of me.
Everything is enabled, the sound isnt muted, the device is set to 'use', power is on, drivers updated, but cant get anything.

Any help or questions would be awesome.

-N

---

### Post by incubus on 2006-03-03
[QUOTE=wiley00]
Firstly..my ATI card. I believe everything is good to go, but is there anyway to check to see if it is enabled?
I've been to the deivce manager which really wasnt any help, but from the looks of things (1280x1024 reso, 24bit color) everything seems to be in order.
[/QUOTE]

I can try to help you with this one.

Open a terminal and run:
glxinfo |grep direct

If 3D rendering is working correctly, you should see "direct rendering: yes".

Otherwise, you may need to install the proper drive, probably "fglrx". Search this forum for guidance.

incubus

---

### Post by wiley00 on 2006-03-03
ran the command and behold its not the right driver I guess
nick@ubuntu:~$ glxinfo |grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

Going to reformat my windows box, get that up and working again, then Im gonna come back and try and figure this Linux stuff out...

Thanks for the code incubus.

---

