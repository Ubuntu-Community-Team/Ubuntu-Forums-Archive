---
title: "Nvidia 7950GT not accepting nvidia driver"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by dutch_boi1 on 2007-09-16
Hey, i have a fresh install of ubuntu 7.04 with all the latest updates. So i decided to install the nvidia driver. I followed the words in this post [http://ubuntuforums.org/showthread.php?t=551669](http://ubuntuforums.org/showthread.php?t=551669)

Where as i was told to Try: sudo /etc/init.d/gdm stop
sudo sh /path/to/the/driver/NVIDIA-Linux-x86 blah, blah, blah (newest driver)
Accept license, let driver remove old drivers and compile module, let driver reconfigure your xorg file
sudo /etc/init.d/gdm start
If need be: startx
Make sure you have build-essential:
sudo apt-get build-essential

I did that and the driver installed it configured my xorg.conf and everything. Its just that the driver doesnt like my system; Gigabyte GA-P35-DQ6, Q6600,3gb ram, nVidia 7950GT. I mean it loads everything in the background and i hear the sounds but it cant send the image to my display. My monitor will just go Blue (no signal) and thats as far as it gets with the driver set to nvidia in the xorg.conf file. iIf i set it to nv or vesa it works fine.

So how come it wont accept the optimized driver :S? I have tried installing the driver through envy and through restricted all dont work with the driver set to nvidia.

Any Idea's?

---

### Post by dutch_boi1 on 2007-09-16
Well after reading through the guides here :[http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

I have found out that my card is not supported :( through both pages of notes it didnt say nVidia 7950GT only GX2 and 7900GTX.

Wierd thing is this has worked before?

---

### Post by heldal on 2007-09-16
The driver included with ubuntu 7.04 only supports the GX2 version of the 7950 according to the supplied doc (/usr/share/doc/nvidia-glx-new/README.txt.gz).

Support for the 7950 GT (PCI ID 0x0295 - use "lspci -vvnn" to check) can be found in the latest driver released by Nvidia (version 100.14.11). This will probably be included in the october release of ubuntu. In the meantime you're best off removing any of the driver-packages you have installed and install the original one from Nvidia instead ([http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)). The downside of not using the original ubuntu-packages is that you'll have to remember to recompile the kernel-module for the card if a kernel-update is installed.

---

### Post by dutch_boi1 on 2007-09-16
Hey ok hmmm could u show me how to remove my old drivers? thing is i have the newest drivers i just realised. The ones of the nvidia site so i have no idea.

---

### Post by heldal on 2007-09-16
Try "method 2" in the following document. That should also cover the removal of drivers you've already installed :

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

### Post by dutch_boi1 on 2007-09-17
well i tried method 2 and the installer wouldnt work, then i changed some of the commands to suit my system and the installer finished  but it still wouldnt work.

Thanks for the try though, no idea how to make this card work :(

---

### Post by dutch_boi1 on 2007-09-17
quick edit: what i dont understand is how ive had it working before :S

---

