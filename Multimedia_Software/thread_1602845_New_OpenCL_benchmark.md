---
title: "New OpenCL benchmark"
date: 2010-10-21
forum: Multimedia Software
---

### Post by pelotoescogorciao on 2010-10-21
Hello,

I've just seen this new OpenCL benchmark using ray tracing:
[www.ratgpu.com]("http://www.ratgpu.com")

It supports Ubuntu 10.04 and 10.10 ( x86/x64 ). Now that Maverik Meerkat supports OpenCL by default, this test can be used to compare the results vs Windows, measure the GPU overclocking stability or just see if you've an OpenCL-capable system, etc...

Here are my results with Ubuntu 10.04 and privative FW 260.19.12 from NVIDIA's official web:

[IMG]http://img695.imageshack.us/img695/5846/ratgpuubuntu.jpg[/IMG]

( I use the spanish version, of course it's available also in english )

In Windows 7 x64 takes 610 secs, so Ubuntu's drivers seems to be very good! :guitar:

---

### Post by pelotoescogorciao on 2010-10-22
Wow! Ubuntu score is actually better than Windows!

---

### Post by a-user on 2010-10-22
i just tried version 0.4.3 but it just crashes with a segmentation fault. that's all it says. using nvidia card with propritiary drivers here on ubuntu 10.10 64bit.

---

### Post by pelotoescogorciao on 2010-10-22
> **a-user said:**
> i just tried version 0.4.3 but it just crashes with a segmentation fault. that's all it says. using nvidia card with propritiary drivers here on ubuntu 10.10 64bit.
What GPU are you using?

Have you installed the the amd64 .DEB version and not the i686 one hacking with the -i -force_all option, haven't you?
Also you need the Forceware 260 ( not older ones ) and have the system updated. Installing the ia32-libs package is also a good idea.

you can do a quick test: open a console and navigate to /opt/ratGPU/StandaloneRenderer/x64

there, put this:

ldd -d StandAloneRenderer

and see if any dynamic library is missing.

---

### Post by pelotoescogorciao on 2010-10-22
It runs well with my Ubuntu 10.10 amd64 , GTX460 192bits and privative FW 260.19.06 from Synaptic. I've installed ratGPU clicking over the ratGPU_0.4.3_amd64_Ubuntu_10.deb file.

[IMG]http://img80.imageshack.us/img80/8968/ratgpuubuntu1010x64.jpg[/IMG]

( curious: seems the x86 drivers are a bit faster than the x64 ones )

---

### Post by a-user on 2010-10-25
i am using the 64bit deb and i have the newest 260 nvidia drivers isntalled. i have a nvidia gt220. it crashes uppon start already in console with the single message "segmentationfault".

when i'm back home i will try the "ldd"-thing. but for that i will have to reinstall it cause i purged it.

---

### Post by pelotoescogorciao on 2010-10-25
By the way, there is a new version (0.4.4) in case you still have problems with the 0.4.3

---

