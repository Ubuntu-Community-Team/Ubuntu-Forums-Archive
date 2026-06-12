---
title: "Failing to configure nv driver"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by rschroev on 2008-03-11
Hi,

I accidentally messed up my xorg.conf, and now I can't get Ubuntu to correctly work with my video card. 

On reboot Ubuntu is unable to detect video card/screen and asks me to configure it manually (as it did when originally installing Ubuntu). No problem, I select driver 'nv' and select 'LCD Panel 1680x1050'; that's what I have, and I know everything worked correctly with those settings before.

If I click 'Test', the screen is blanked and stays blanked. If I click 'Continue' instead, after a while I get a login screen, but in a very low resolution (640x480 or 800x600, I'm not sure), and it turns out that Ubuntu only uses the vesa driver instead of the nv driver.

The computer is a Lenovo Thinkpad R61, and the OS is Ubuntu 7.10 AMD64.

---

### Post by zxscooby on 2008-03-11
Try this command
```
sudo nvidia-xconfig
```

---

### Post by gtdaqua on 2008-03-11
just see this post:

[[SOLVED] Nvidia drivers Please edit your X configuration file (error) need help]("http://ubuntuforums.org/showthread.php?t=721108").

That post actually directs to another walkthrough tutorial explaining how to setup NVIDIA drivers correctly.

---

### Post by rschroev on 2008-03-11
Thanks for your answers.

You both refer to the nVidia-drivers, though, and I don't really need those. I guess I could use them anyway, instead of the nv-driver, but that means I need to recompile them at every kernel upgrade, and I'd like to avoid that.

---

### Post by gtdaqua on 2008-03-11
> **rschroev said:**
> Thanks for your answers.

You both refer to the nVidia-drivers, though, and I don't really need those. I guess I could use them anyway, instead of the nv-driver, but that means I need to recompile them at every kernel upgrade, and I'd like to avoid that.

oh. so wat display driver are u using? you can see the sticky posts in this section for installing ATI drivers.

---

### Post by PmDematagoda on 2008-03-11
> **rschroev said:**
> Thanks for your answers.

You both refer to the nVidia-drivers, though, and I don't really need those. I guess I could use them anyway, instead of the nv-driver, but that means I need to recompile them at every kernel upgrade, and I'd like to avoid that.

Are you upgrading the kernel regularly? If not then compiling the Nvidia drivers would be more sensible since you could then use compositing and other effects.

---

### Post by rschroev on 2008-03-11
OK, I just went ahead and installed the nvidia driver, and the screen is in high resolution again. So that's good :)

I still don't understand why Ubuntu wouldn't just want to work with the nv-driver, but I guess it doesn't matter that much.

---

