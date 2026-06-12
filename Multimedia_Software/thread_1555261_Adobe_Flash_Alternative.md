---
title: "Adobe Flash Alternative"
date: 2010-08-17
forum: Multimedia Software
---

### Post by sfBlackfox on 2010-08-17
Hello everyone,

I notice that Adobe Flash is very unstable under Ubuntu, already it has crashed a couple of times and it seems to eat quite a bit of resources when I'm working. Is there a good alternative that is more stable and can handle the same things? I noticed Gnash is available, but after some digging I see that it does not come very close to Adobe Flash. 

Is there another option?

Cheers,
Hans

---

### Post by TBABill on 2010-08-17
There really isn't. Best you can do is use Adobe Flash, use Sun Java, make sure you're using a proprietary driver for your video card and enable CPU scaling (CPUFREQ). Those items are as close as I have gotten to keeping my machine cool...or close to as cool as it natively runs in Windows.

Just an FYI...flash does not support GPU acceleration in Linux like it does in Windows and MAC, so you will naturally see CPU usage spiking along with additional heat. Not much else I know of that can help reduce those heat levels. Proprietary drivers for video cards are probably the best option to protecting your hardware from unnecessary heat.

---

### Post by lovinglinux on 2010-08-18
> **TBABill said:**
> There really isn't. Best you can do is use Adobe Flash, use Sun Java, make sure you're using a proprietary driver for your video card and enable CPU scaling (CPUFREQ). Those items are as close as I have gotten to keeping my machine cool...or close to as cool as it natively runs in Windows.

I agree. There is lightspark, but is too soon to use it, since is not compatible with many things and uses more CPU.

Also check my [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) tutorial.

> **TBABill said:**
> Just an FYI...flash does not support GPU acceleration in Linux like it does in Windows and MAC, so you will naturally see CPU usage spiking along with additional heat. Not much else I know of that can help reduce those heat levels. Proprietary drivers for video cards are probably the best option to protecting your hardware from unnecessary heat.

In fact it does support GPU acceleration in Linux. The problem is that it doesn't use XV and not all content is developed to make use of GPU acceleration. Additionally, it doesn't play well with Compiz, which prevents HA to be used [[source]("http://blogs.adobe.com/penguinswf/2008/05/flash_uses_the_gpu.html")].

---

### Post by sfBlackfox on 2010-08-18
Thanks for the heads up guys, I'll try that optimization guide now :) 

Cheers

---

### Post by lovinglinux on 2010-08-18
> **sfBlackfox said:**
> Thanks for the heads up guys, I'll try that optimization guide now :) 

Cheers

Also make sure you don't have any duplicated plugins. You need to remove gnash, swfdec and lightspark for the Adobe flash to work properly.

See [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

