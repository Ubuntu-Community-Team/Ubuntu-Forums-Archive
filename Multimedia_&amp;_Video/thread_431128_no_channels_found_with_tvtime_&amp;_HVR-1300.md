---
title: "no channels found with tvtime &amp; HVR-1300"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by tracer_bullet on 2007-05-02
i recently upgraded my PC with a HVR-1300. and now that feisty fawn is out i finally have a working WiFi, and it is working great, and i'm finally able to use linux for something. so i tried setting up my system and almost everything works, main problem being my HVR-1300:

the drivers are all loaded fine and /dev/video0 is created, tvtime recognizes it as valid input but fails in finding any channels (analogue cable). can't test the DVB-T because of lack of freeview signals in my area.

any ideas?

---

### Post by MagnusL on 2007-05-05
Hi!

I have a similar situation. I found this: [https://www.redhat.com/mailman/private/video4linux-list/2007-March/msg00338.html](https://www.redhat.com/mailman/private/video4linux-list/2007-March/msg00338.html)

After loading the module cx88_blackbird a new device, /dev/video1, was created, and when probing it a firmware loaded. But no channels found. 

Have you had any progress?

Magnus L

---

### Post by packjamNL on 2007-05-10
Same situation here, I only need winxp for my HP wintv hvr 1300, I found only specs and links links: who knows we'll get it working, because it's a b*tch, never saw it working on any uX.


Model 	Tuner 	Host Interface 	Analogue 	Digital 	Other 	IR
HVR-1300 	Philips FMD1216ME 	PCI

CX2388x
	1x CX2388x

1x CX23416
	DVB-t (CX22702) 	Composite In

S-Video In FM Radio
	Yes

[http://gentoo-wiki.com/HARDWARE_Hauppauge_HVR_1300#External_Links](http://gentoo-wiki.com/HARDWARE_Hauppauge_HVR_1300#External_Links)
[http://www.linuxtv.org/links.php](http://www.linuxtv.org/links.php)
[http://en.wikipedia.org/wiki/Hauppauge_Computer_Works](http://en.wikipedia.org/wiki/Hauppauge_Computer_Works)
and ofcourse try "watch tv" in our own forum

---

### Post by Sprocket_dk on 2008-06-26
any progress on this one. i can only see digital channels.

---

### Post by DiGiTGOD on 2008-07-04
If only I can watch digital channels!!!

I can't get anything to work with the card... keep getting random errors...

Everyone everywhere seems to be getting the same problems with the same card...

It doesn't look like Ubuntu is going to support it anytime soon so think I'm going to switch distros over the next week or so... see if that helps...

People in the Fedora forum seem to be saying it works...

FYI... loads of people with information around the 1100, 3000 and 4000... just none on the 1300!

---

