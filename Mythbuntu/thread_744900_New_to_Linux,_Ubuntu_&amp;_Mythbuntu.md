---
title: "New to Linux, Ubuntu &amp; Mythbuntu"
date: 2008-04-04
forum: Mythbuntu
---

### Post by jlaham on 2008-04-04
First off, hello to all, and congrats on your continued efforts, with the development and contributions to Mythbuntu; truly an amazing distro... Like most PC owners, I am a Windows native, so I am rather new to the Linux world, but i must say that I do love it and getting familiar with it more and more on a daily basis... But that's outside the scope of this post.

I was looking into building a home entertainment system based on a mythTV backend, but as always, with the misfortune of my geographical location it is relatively hard for me to find the appropriate hardware without having to pay a bundle to get it shipped, which is why i face a lot of hesitation on picking my hardware.

Where I live, the only way I can get decent TV programs is through DVB-S streams, and so such an investment can be rather tricky.

Since HD is slowly being introduced to the satellite broadcasting community, should I invest in a DVB-S2 tuner?

How compatible is DVB-S2 with mythTV/mythbuntu?

Anybody recommend a certain DVB-S2 tuner, preferable expandable to have a CI slot?

Is it a given that if a certain tuner is compatible the linuxtv drivers then it will work with mythTV?

That's as far as i have gone with the Live TV version of the backend, one other question i have is a little trickier. Since I am currently building a full system i decided that i would like to integrate everything together, so right now i'm running a windows home server (just until Ubuntu Home Server is released). The one added advantage that I love about this machine is its dynamically sized storage pool, and due to this I want to (once the tuner is set up) directly record LiveTV to windows home server.

Logically speaking, this should be doable by simply locally mounting a specific shared folder from my home server (over my newtork), with the proper credentials, and set that as my recording directory in the mythtv backend. But since i'm pretty much a noob to the linux OS itself, I have no idea how feasible this actually is, so anybody willing to shed some light on this point is most welcome.

:-)

---

### Post by RJ Hythloday on 2008-04-04
This might be of some help
 
[Myth compatible HW](http://www.mythtv.org/wiki/index.php/Video_capture_card#ATSC_.28HDTV.29_cards)

---

### Post by jlaham on 2008-04-04
Actually, I already did that, but while i was doing some reading I came across the LinuxTV drivers, and the v4l-dvb drivers. And I came to see that the hardware list on their wiki is a lot more exhautive. Which is why i asked the other question, which is, can I assume that as long as a device is supported by the v4l-dvb driver then  it can be used in my mythbuntu backend?

---

### Post by nasha on 2008-04-04
> Which is why i asked the other question, which is, can I assume that as long as a device is supported by the v4l-dvb driver then it can be used in my mythbuntu backend?


Yes, provided you install the v4l-dvb drivers:

```
Install the necessary software:

sudo apt-get install mercurial linux-headers-generic build-essential

Obtain the latest v4l-dvb source code:

hg clone http://linuxtv.org/hg/v4l-dvb

Compile and install:

cd v4l-dvb
make
sudo make install
```

---

### Post by laga on 2008-04-04
> **nasha said:**
> Yes, provided you install the v4l-dvb drivers:


No. Ubuntu already comes with "v4l-dvb" drivers. A snapshot was integrated into the kernel during its development cycle. It's usually not needed to install a newer snapshot, unless you need a specific bug fix or some other piece of code from the current head of v4l-dvb.

Telling people to install v4l-dvb from mercurial isn't always a good idea because the code in that repository might be broken sometimes. It'll also clutter up the user's system with kernel modules which are not under control of a package management tool, bringing their installs into an inconsistent state which makes it impossible to debug anything.

Please, do not recommend that people should install v4l-dvb from hg unless there are good reasons to believe that it'll fix their problems.

It'd be very cool if we could have weekly builds from the v4l-dvb repo. Does anyone want to make that happen? :)

---

