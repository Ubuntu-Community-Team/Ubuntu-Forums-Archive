---
title: "GeForce 8300 GS - can't open device file /dev/nvidia0"
date: 2008-04-24
forum: Multimedia Software
---

### Post by jsedwards on 2008-04-24
I am running Kubuntu 7.10 on a Dell Inspiron 530 with a GeForce 8300 GS (rev a1) video card.  I have been using the "nv" driver, but when I tried to watch any video with Kaffeine it would stutter terribly.  It is unwatchable.

I normally try to avoid the binary drivers but I thought I would give it a go to see if Kaffeine would play a video correctly.

So I did the following:

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

And when I rebooted X windows didn't start.  I tried doing a startx and got the "can't open device file /dev/nvidia0" message.  I tried using the old xorg.conf file that worked with the "nv" driver and just changed the driver to "nvidia" but it does the same thing.

The device looks like it is okay:

$ ls -l /dev/nvidia0
crw-rw-rw- 1 root root 195, 0 2008-04-24 06:57 /dev/nvidia0

Any advice would be most appreciated.

Thanks
  -Scott

---

### Post by jsedwards on 2008-04-24
I have attached the Xorg.0.log file (I had to split it into two) and the startx.txt file is the text when running startx.

Also the nvidia module looks like it is loaded:

$ lsmod | grep nvidia
nvidia               4716468  0
agpgart                35016  2 nvidia,intel_agp
i2c_core               26112  9
lgdt330x,cx88_dvb,cx88_vp3054_i2c,dvb_pll,tuner,nvidia,cx88xx,i2c_algo_bit,tveeprom

---

### Post by pquinnet on 2008-07-29
> **jsedwards said:**
> I am running Kubuntu 7.10 on a Dell Inspiron 530 with a GeForce 8300 GS (rev a1) video card.  I have been using the "nv" driver, but when I tried to watch any video with Kaffeine it would stutter terribly.  It is unwatchable.

I normally try to avoid the binary drivers but I thought I would give it a go to see if Kaffeine would play a video correctly.

So I did the following:

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

And when I rebooted X windows didn't start.  I tried doing a startx and got the "can't open device file /dev/nvidia0" message.  I tried using the old xorg.conf file that worked with the "nv" driver and just changed the driver to "nvidia" but it does the same thing.

The device looks like it is okay:

$ ls -l /dev/nvidia0
crw-rw-rw- 1 root root 195, 0 2008-04-24 06:57 /dev/nvidia0

Any advice would be most appreciated.

Thanks
  -Scott

I also am running KUBUNTU on a new DELL Vostro 200 with the same NVIDIA card and no driver was installed.  I have tried loading the driver I downloaded from the NVIDIA site but it won't build correctly generating errors along the way.  Did your NVIDIA drivers load automatically when you installed UBUNTU or KUBUNTU ??  Mine did not. I am reading and searching for how to get the driver loaded.  Anything you can add will be helpful.  
thanks.....pq

---

