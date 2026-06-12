---
title: "cannot insert pwc module"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by rvdb on 2007-01-10
I updated the kernel (synaptic) to 2.6.17-10-386

After a kernel update i have to update the nvidia driver. This time i installed the newest from NVIDIA (because of the twinview support )

Now my pwc driver does not work anymore. I installed from source using the module assistent. Somehow the m-a stores the pwc.ko file in a directory that cannot be found so i moved it to 

/lib/modules/2.6.17-10-386/kernel/drivers/usb/media/pwc/pwc.ko

Then 

rein@vision-studie:~$ sudo modprobe pwc
FATAL: Error inserting pwc (/lib/modules/2.6.17-10-386/kernel/drivers/usb/media/pwc/pwc.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Anyone any idea what went wrong somewhere?

Note in the meantime i also installed drivers to use a dvb card from pinnacle. But that worked!

Regards

Rein

---

