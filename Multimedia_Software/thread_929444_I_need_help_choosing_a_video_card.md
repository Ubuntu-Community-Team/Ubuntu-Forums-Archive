---
title: "I need help choosing a video card"
date: 2008-09-25
forum: Multimedia Software
---

### Post by Reddington on 2008-09-25
I tried to install Ubuntu on my machine which has a Radeon x800 video card. After trying my best to get the ATI drivers to work in ubuntu with no luck I've decided to try using a different video card. 

Is there anywhere I can go to find out which video cards work best on Ubuntu? I don't plan on using it for any highly graphical games so I just need a simple, efficent card that has support on Ubuntu. 

Any recommendations?

---

### Post by Mattlock on 2008-09-25
I don't see why there should be any problem to find drivers for a common card like that (I even found some for my random x1400)

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way")

^ A decent tutorial on how there, and once it's installed you can access the Catalyst control panel from Applications>Accessories>ATI Catalyst Control Center.

---

### Post by sloggerkhan on 2008-09-25
an x800 should work pretty well out of the box.

Maybe you could explain your issues in some more detail?

---

### Post by eragon100 on 2008-09-25
A 512 MB GeForce 8 8500 GT sounds good for you. Completely supported with the nvidia binary driver, and perfect for compiz-fusion, watching movies, and even casaul gaming (and older games such as openarena, neverwinter nights, urban terror, and unreal tournament 2004)

It's also very cheap :wink:

I have a 512 mb geforce 8 **8600** GT, and I picked that one up for around 70$. This card is good for quality 3d graphics, such as nexuiz on maximum setting @ 1680 x 1050. I don't think you will need if you don't game much, tough.

---

### Post by sloggerkhan on 2008-09-25
> **eragon100 said:**
> A 512 MB GeForce 8 8500 GT sounds good for you. Completely supported with the nvidia binary driver, and perfect for compiz-fusion, watching movies, and even casaul gaming (and older games such as openarena, neverwinter nights, urban terror, and unreal tournament 2004)

It's also very cheap :wink:

I have a 512 mb geforce 8 **8600** GT, and I picked that one up for around 70$. This card is good for quality 3d graphics, such as nexuiz on maximum setting @ 1680 x 1050. I don't think you will need if you don't game much, tough.

I've got an 8600gt 256mb fanless. Good for games at 1680x1050, but it sucks at video playback. It only supports xv overlay and its upscaling isn't that great. A good $70 card right now IMO is ati radeon 4670.

---

### Post by pelle.k on 2008-09-29
> It only supports xv overlay and its upscaling isn't that great.
Can you elaborate on that? I've always felt xvideo was great!? (get no upscaling at all with other video overlay modes such as X11, opengl, etc).
Also, xvideo has always had the most video acceleration for me.
What do you use?

btw, isn't it true that ati (currently) have problems with compiz and video playback at the same time. video tearing, flicker, opengl fullscreen problems? Correct me if i'm wrong..

---

### Post by sloggerkhan on 2008-10-01
ati's xv implementation is similar to nvidia's and in my experience works with compiz.
However, opengl overlay on ati (in my experience) is much better than xv in terms of overall quality of upscaling and will not work with compiz.

The thing about ati right now is that depending on what exact card you have I imagine things can be pretty different, more so than just the dif between the open and closed drivers. For example, with open drivers, some, but not all, ati cards support kernel based mode setting. With commercial drivers, there is the change in capabilities from fixed hardware pipelines to programable shaders, and other factors.

Also worth noting is that accoring to phoronix, next driver release should have umd, or accelerated media decoding in addition to playback.

---

