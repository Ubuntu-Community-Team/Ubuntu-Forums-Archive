---
title: "Nvidia driver not working after Envy installation"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by bullraiser on 2007-06-08
Hi,

I was having a perfect working nvidia driver that came along the default installation of the Ubuntu Feisty 7.04 until I installed Envy. I was thinking about trying Envy and installed it. After installing Envy, I tried installing nVidia driver. 

I saw that it installed some kernel source along with nvidia-glx and config. After the installation, I was prompted to reboot the system for the effect to take place and rebooted the system.

Alas, I was thrown up with blue screen dialog saying that my graphical instance cannot be started due to some nvidia driver problem. After looking into the Xorg.log.0, it seems that my kernel source and screen cannot be found. 

I uninstalled Envy and nvidia-glx, restricted modules and reinstalled them again (without Envy). But, I'm not able to get nvidia driver working. Can someone help me, how to restore the system back?

Any help appreciated.

TIA--

---

### Post by eggdeng on 2007-06-08
If you installed a new kernel, you can simply boot into your old one by selecting it using the up and down arrows on the grub menu screen. 
If you can't boot into this kernel, look in your /etc/X11 directory to see if there is a back-up of your xorg.conf file, it might be called xorg.conf.original or something similar. 
Back up your current xorg.conf and copy the original back up file over the current xorg.conf. Post again if you need help with this.

---

### Post by bullraiser on 2007-06-18
I had removed all my previous kernel versions, as I dont want to have the redundant kernal residing in my harddrive. Is there anyother option to get the nvidia driver working?

I get the exception "Nvidia Kernal mismatch". I had search few topics on this but couldnt find a good one that is working.

Can someone suggest me accordingly?

TIA--

---

### Post by eggdeng on 2007-06-18
Can you post the output of ```
lspci | grep VGA 
```and ```
uname -a
```

---

### Post by bullraiser on 2007-06-21
uname -a
Linux NeMo 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux



lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)

---

### Post by eggdeng on 2007-06-21
You could try ```
apt-cache search linux-image
``` to see the available kernels, then ```
sudo apt-get install whichever_kernel_matches_your_specs
```

---

### Post by bullraiser on 2007-06-22
ok, I will try this and post with the updates.

---

