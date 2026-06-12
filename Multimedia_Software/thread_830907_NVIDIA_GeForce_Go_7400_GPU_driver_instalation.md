---
title: "NVIDIA GeForce Go 7400 GPU driver instalation"
date: 2008-06-16
forum: Multimedia Software
---

### Post by momo07 on 2008-06-16
Hi there,

I recently downloaded drivers for my video card to work with Compiz from nvidia.com. The drivers from synaptic do not work with my card. However the downloaded file is in this extention:
[B]
NVIDIA-Linux-x86-1.0-8756-pkg1.run[/B]

I am using Ubuntu ver 8.04 Hardy on a sony vaio model vgn-sz5mn, and I'm pretty new to the Linux os.  Any help would highly be apreciated.

Thank you in advance

---

### Post by salvador_luna on 2008-06-16
Hello!

Wich drivers from synamptic you tried? I have a nVidia Corporation GeForce 7150M (rev a2) and the only way to make it works is using the nvidia-new drivers:

sudo apt-get install nvidia-glx-new nvidia-new-kernel-source nvidia-glx-new-dev

Also, i updated my bios.

If you want to use the drivers from nvidia, you shouldd try envy... i think it installs the drivers you want, but i'm not sure, i never used envy because the nvidia-new always worked fine for me.

---

### Post by momo07 on 2008-06-16
Thanks for your response,

I used the same driver you are using but when I boot my system I just get a black screen.  I will try envy now and let you know. Thanks again

---

### Post by gohanssjn on 2008-06-16
Good luck with envy, it helped me in the past.

I have the same card and the nvidia-glx-new works for me just fine, so hopefully envy can get thet set up for you.

---

### Post by brigadoon on 2008-06-16
I had a blank screen when first installing my driver on a Toshiba laptop. I needed to add an Option switch to my xorg.conf configuration file. If you keep getting a blank screen you may need to add a similar line that I did. I added the following to the default screen section....

Option "UseDisplayDevice" "DFP"

This option tells the driver to use the default flat panel display. My complete solution is located at...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

Good luck.

---

