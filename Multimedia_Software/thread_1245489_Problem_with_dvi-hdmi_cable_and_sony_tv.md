---
title: "Problem with dvi-hdmi cable and sony tv"
date: 2009-08-20
forum: Multimedia Software
---

### Post by snoopo71 on 2009-08-20
I've bought a dvi-hdmi cable to connect the PC to a sony 55" screen, after plug the cable in the hdmi connection of the tv I saw the image. 

Configuring the screen I only have two possible diplay resolution configurations 720*480 or 1920*1080 I choose the 1920*1080 option and the TV screen auto-configures itself to 1080p and there is the problem, I've lost around 2 or 3 cm of my desktop in all directions and I don't know how i can configure this(the tv can't).
I attach a capture of my screen.
If you don't understand me please say it.

---

### Post by markbuntu on 2009-08-20
Your tv may be set to overscan which will cause that. Some gpu drivers have options to adjust tv overscan and some tvs do also.

720x480 is 720p and 1920x1080 is 1080p which is most likely all your tv reports it is capable of through the hdmi port.

---

### Post by snoopo71 on 2009-08-20
1º of all thx for answering.
So, I've been looking around for 4 hours and I'm getting crazy!!!
You're right, my TV is overscanning at 1080P and at 480p(720*480)(I still don't know why...:() and unfortunately for me there is no solution. I've changed the xorg.conf tried to set a virtual resolution and look for some program in the net and after seeing that there is a lot of people with the same problem I don't know what to do.

I have an ati 9600, and I'm using Ubuntu 9.04, then I can't install any Catalyst(maybe in 9.10...) so I can't access to all the features of the card :((I'm telling you that because I've read some nVidia drivers can underscan).

I've read a lot of pages and everybody is blocked with that problem, there is no program on ubuntu like powerstrip or switchresX, there is no way with the tv settings and there is no way with the drivers.

I surrender 'til 9.10 or any ati info...

---

### Post by markbuntu on 2009-08-21
In that case you should definitely file a bug report either to launchpad or directly at Xorg. It should be against the package

xserver-xorg-video-ati

If you don't file a bug report the devs may be unaware even though lots of people are talking about it in the various forums etc.

---

