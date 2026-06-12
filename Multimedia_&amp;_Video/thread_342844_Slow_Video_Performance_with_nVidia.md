---
title: "Slow Video Performance with nVidia"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by JimFlint on 2007-01-20
I am quite new to Ubuntu, but have v6.10 running on a few machines now.
My main issue is that the nVidia graphics seem very slow and I think I am missing something obvious.
I have an nVidia 6800 in one machine and an FX5200 in another - both machines are good spec (i.e. 3GHz cpu, 1 or 2 Gb RAM etc)

I used apt-get to download the nvidia driver and installed it - checking that my xorg.conf has nvidia as the driver (and not nv)

Any ideas anyone ??

---

### Post by Drew Woodard on 2007-01-21
what specifically seems slow to you, is it 2d stuff 3d stuff?  Does window drawing feel sluggish or is it playing videos or something else?

---

### Post by NotPhil on 2007-01-21
> **JimFlint said:**
> I used apt-get to download the nvidia driver and installed it [...] the nVidia graphics seem very slow.

The drivers at the repositories didn't work right for me either.

So, I installed xserver-xorg-dev with the Synaptic Package Manger. Then, I download the video-driver installation script from [NVIDIA's Web]("http://www.nvidia.com/content/drivers/drivers.asp") site. 

After that, I switched to console mode by pressing [Ctrl]-[Alt]-[F3]. Then, I quit X-Windows with "sudo /etc/init.d/gdm stop".

I removed the drivers from the repositories with "sudo dpkg --purge nvidia-glx".

I typed "sudo nano /etc/default/linux-restricted-modules-common" to edit the list of restricted kernel modules that Ubuntu links to at start-up, and put "nv" in the quote marks at the bottom of the file, and pressed [Ctrl]-X and then Y to save the file.

Then, I typed "sudo sh Desktop/NVIDIA-Linux-(whatever-the-version-is)-pkg2.run" to install the drivers and tell X-Windows to use them.

Finally, I typed "sudo /etc/init.d/gdm start" to start X-Windows. Now it works fine.

---

### Post by JimFlint on 2007-01-21
1. It is 2d gfx, such as switching desktops and moving windows around that are slow for me.

2. When I run the NVidia.....run  script it moans about the kernel and wants to download something from nVidia and then hangs.
Is this because I am behind a proxy and if so how can I fix it ?

Thanks
JF

---

### Post by NotPhil on 2007-01-21
> **JimFlint said:**
> When I run the NVidia.....run  script it moans about the kernel and wants to download something from nVidia and then hangs. Is this because I am behind a proxy and if so how can I fix it ?

I think mine downloaded some files so it could rebuild part of the kernel. You might try downloading the linux-source package from the repositories and see if the script will run without connecting to another site.

---

