---
title: "nvidia+ubuntu 10.04"
date: 2010-10-08
forum: Multimedia Software
---

### Post by boxingfan on 2010-10-08
hello everyone

im having a lot of issues with my video card, i can't install it correctly
i get low graphics mode and some times a black screen..login+password
i had read a lot of post, installed ubuntu a few times, done a lot of stuff but i can't 
get it, im a noob, using ubuntu for a week now and i love it.
plese help

---

### Post by tommcd on 2010-10-09
> **boxingfan said:**
> 
im having a lot of issues with my video card, i can't install it correctly
i get low graphics mode and some times a black screen..login+password

*Please answer these 2 questions*.
What nvidia card do you have?
How have you tried to install the nvidia driver?

The easy way is to install the nvidia driver from the Ubuntu repos using the Hardware Drivers Manager:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

*Note*: If you had previously tried to install the driver from nvidia.com, you will need to *completely remove* that driver before installing the driver from the Ubuntu repos.

Ans welcome to the Ubuntu forums!

---

### Post by boxingfan on 2010-10-09
thank you for you replay,every thing look fine,but now if i go to "sistem, administration,hardware drivers"i get "NO PROPRIETARY DRIVERS ARE IN USE ON THIS SYSTEM" is that ok? and i get (desktop effects coulld not be enable) on appearance preferences, how can i fix it?im realy new at this thank you
e-GeForce 6200

---

### Post by gordintoronto on 2010-10-09
You might need to install a more up-to-date video card to get desktop effects. Personally, I'm more concerned about what I can *do* with my computer than any eye-candy.

---

### Post by brenthen on 2010-10-09
i have a similer issue with ubuntu 10.10
had my card going fine on 10.04 but after upgrade i can only boot with low graphics mode from recovery  when i check  propriety drivers it says  driver installed(Nvida 96) but not in use ???

---

### Post by tommcd on 2010-10-10
> **boxingfan said:**
> ... every thing look fine,but now if i go to "sistem, administration,hardware drivers"i get "NO PROPRIETARY DRIVERS ARE IN USE ON THIS SYSTEM" is that ok? ...
So the *Hardware Drivers Manager* does not offer to install any nvidia drivers for you at all? Is that correct?
Also, once again, since you have not answered this question:  How have you previously tried to install the nvidia driver on Ununtu?? This is imporatant!!!
> **boxingfan said:**
> 
, how can i fix it?im realy new at this ... e-GeForce 6200
It is odd that Ubuntu does not offer to install any driver for the nvidia 6200. I used to have a nvidia 6200 on my system, and Ubuntu worked just fine with it. This was an earlier verison of Ubuntu though.
The driver you want is listed in the Ubuntu repos as *nvidia-current*. According to the Ubuntu repos, nvidia-current:
> GPUs such as GeForce series 6 or newer are supported.  
[http://packages.ubuntu.com/lucid/nvidia-current](http://packages.ubuntu.com/lucid/nvidia-current)
Note: This is not the latest nvidia driver, but for an older card like the 6200 this should be just fine. I am using the same driver for my 8600GT.

Here is the most fail safe method for installing the nvidia driver: First, switch to a virtual terminal by hitting: **ctrl** + **alt** + **F2**. Then login; and then stop X:
```
sudo service gdm stop
```
Then install and configure the nvidia driver:
```

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

```
When you reboot, hopefully the nvidia driver should be enabled. You can check this by running in the terminal:
```
glxinfo | grep -i render
```
It should report something like this:
```

tom[data]$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
tom[data]$ 

```
The thing to look for there is: *direct rendering: Yes*;
And the OpenGL render string should list your nvidia card: *OpenGL renderer string: GeForce 8600 GT*.

Again, and this is important: 
If you had previously tried to install the driver from nvidia.com, you will need to *completely remove* that driver before installing the driver from the Ubuntu repos. 
Write back if you need more help.

---

### Post by tonsil on 2010-10-10
> **brenthen said:**
> i have a similer issue with ubuntu 10.10
had my card going fine on 10.04 but after upgrade i can only boot with low graphics mode from recovery  when i check  propriety drivers it says  driver installed(Nvida 96) but not in use ???

:confused: Unfortunately Nvidia 96 drivers are not supported in Ubuntu 10.10 Maverick and neither is Nvidia 173. Take a look at this bug: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974)

---

