---
title: "Samsung QX310, NVIDIA GeForce 310M, lack of 3D acceleration"
date: 2011-07-23
forum: Multimedia Software
---

### Post by RadFel on 2011-07-23
Hi,
After I installed the system (Ubuntu 10.04 64-bit), I wanted to turn the owner driver (nvidia-current) on in order to gain hardware graphics acceleration, among others 3D acceleration.

When I installed this driver and restarted the computer, it appeared that the error message shows up:
```
(EE) No devices detected.
No screens found.
```

If I want to have any window based environment at all, I have to go back to the previous settings, without this driver.

The only solution I found so far on the Internet tells to turn this driver off at all, what means no 3D acceleration.

Has anyone encountered this problem and found a solution? Is there any possibility to turn hardware acceleration on for this card on Ubuntu?

--
Regards,
Radek

---

### Post by khelben1979 on 2011-07-23
Have you tried the drivers from nvidia.com? If not, I would recommend it. Make sure to get the correct one which supports your Geforce 310M chipset.

Update: I checked the webpage, and it says that graphic drivers for the 64 bit platform is not supported, only 32 bit. [Check here]("http://www.nvidia.com/object/linux-display-ia32-275.21-driver.html").

---

### Post by BicyclerBoy on 2011-07-23
Of course the 64 bit environment is supported by nvidia but not if you download the ia32 driver version...

Ubuntu 10.04 probably does not have a driver version with support for 310M altho it is just a mobile GT210.

But the OP problem is most likely optimus graphics..
[http://lmgtfy.com/?q=optimus+linux&tbs=,qdr:y]("http://lmgtfy.com/?q=optimus+linux")[]("http://lmgtfy.com/?q=optimus+linux")

Other keywords to read up on are:
deBumblebee
vgaswitcharoo

---

### Post by RadFel on 2011-07-23
> **khelben1979 said:**
> Have you tried the drivers from nvidia.com? If not, I would recommend it. Make sure to get the correct one which supports your Geforce 310M chipset.

Update: I checked the webpage, and it says that graphic drivers for the 64 bit platform is not supported, only 32 bit. [Check here]("http://www.nvidia.com/object/linux-display-ia32-275.21-driver.html").

I downloaded the drivers from NVIDIA's website and the outcome was the same.

I'm afraid I'm stuck.

--
Regards,
Radek

---

### Post by RadFel on 2011-07-23
> **BicyclerBoy said:**
> Of course the 64 bit environment is supported by nvidia but not if you download the ia32 driver version...

Ubuntu 10.04 probably does not have a driver version with support for 310M altho it is just a mobile GT210.

But the OP problem is most likely optimus graphics..
[http://lmgtfy.com/?q=optimus+linux&tbs=,qdr:y]("http://lmgtfy.com/?q=optimus+linux")[]("http://lmgtfy.com/?q=optimus+linux")

Other keywords to read up on are:
deBumblebee
vgaswitcharoo

It solved the problem for me, at least it looks so now. Thanks!

--
Regards,
Radek

---

### Post by khelben1979 on 2011-07-24
> **BicyclerBoy said:**
> Of course the 64 bit environment is supported by nvidia but not if you download the ia32 driver version...

You're absolutely right and thanks for correcting me. :) I knew that but expressed differently.

Good that you got it working!

---

