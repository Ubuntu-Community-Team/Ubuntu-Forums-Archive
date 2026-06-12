---
title: "Vaio SZ110 Speed/Stamina Switch + Xgl"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by pcaritj on 2006-10-10
OK, this might be a hard one :), but hopefully interesting for you guys. I have a sony Vaio SZ110 and almost everything is working beautifully (most of it out of the box! (so to speak)).

Presently, I have the NVidia GeForce Go7400 working perfectly with Xgl, etc. However, this gobbles up my battery at a rapid pace. To solve this problem, Sony saw fit to equip the SZ110 with a Speed/Stamina switch; in "Speed" mode it uses the NVidia card, and in "Stamina" mode it uses the onboard Intel i810.

My question: how can I set up Xgl to work in stamina mode? I have already read the tips here: [http://ariel.vardi.free.fr/ariel//vaiosz.html](http://ariel.vardi.free.fr/ariel//vaiosz.html) but it does not work for 3D acceleration because, when you start Xgl with the i810 enabled it attempts to use NVidia's GLX extensions, like so (from Xorg.log): 

```
...
(II) I810(0): Mode bandwidth is 61 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 324 Mbyte/s, 0 Mbyte/s
(II) I810(0): Initializing HW Cursor
(**) I810(0): DPMS enabled
(II) I810(0): direct rendering: Disabled
(II) I810(0): libshadow is version 1.0.0, required 1.1.0 or greater for rotation.
(==) RandR enabled
**(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)**
...
```

Do I need to somehow configure Ubuntu to only conditionally load the NVidia drivers? If so how? 

Thanks guys,
Paul

---

### Post by ScreemingBlue on 2006-10-13
Take a look at this link..

[http://ariel.vardi.free.fr/ariel//vaiosz.html](http://ariel.vardi.free.fr/ariel//vaiosz.html)

I'm interested in the SZ, can you tell me how ubuntu performs on it so far.???

---

### Post by pcaritj on 2006-10-13
ScreemingBlue,
As I mentioned in my original post I have looked at that site and, at least on this point, found it lacking. The instructions they provide are enough to get a standard X desktop working in both modes but does not extend to explaining how to do the same with Xgl. I'm quite certain I need to change my bootup procedure to load different GLX extensions (among other things, perhaps) but I simpy do not know how to do that yet.

To answer *your* question however: I have had a great deal of success with Ubuntu on my SZ110, as I said in the OP. Specifically, unaccelerated 2d video works out of the box (with the correct color depth, widescreen resolution, etc), driver installation (at least for the on board GeForce Go7400) is a breeze, sound and wireless work out of the box...the mute/volume softkeys (Fn+F2/3/4) even work perfectly. Hibernation is a little dodgy but power management, generally, seems to be good enough. I have also had no problems with the DVDR/CDRW combo drive. I have not had cause/opportunity to play with the integrated biometric device under Ubuntu so i can't speak to that except to say that I believe it to be implemented through USB so there is no reason, in principle, why it could not work. 

You must install a 686 kernel for it to make use of both processor cores but that is quite easy (installs as a package without trouble) and to be expected.

I think that should cover everything...I recommend it!

---

