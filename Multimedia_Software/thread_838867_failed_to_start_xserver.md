---
title: "failed to start xserver"
date: 2008-06-23
forum: Multimedia Software
---

### Post by black dawg on 2008-06-23
I just recently installed some updates to 7.04. I'm getting a fatal error that says:

FATAL: Could not open '/lib/modules/2.6.20-17-generic/volatile/nvidia.ko' : No such file or directory
(EE) NVIDIA(0): Failed to laod the NVIDIA kernel module!
(EE) NVIDIA)(0):  ***Aborting***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found

Can anyone help me fix this?  Thanks in advance!

---

### Post by jasapper on 2008-06-24
Same situation here after installing new kernel 2.6.22-15-generic over the weekend, Other than the kernel rev error message is identical. Running Kubuntu 7.10 though with nVidia FX5500. Rebooting to previous kernel 2.6.22-14 everything starts right up no problem. No solution as of yet.

---

### Post by anindya_m on 2008-06-24
You need to recompile the nvidia kernel module for the new kernel. There should have been a corresponding nvidia upgrade on synaptic. If not, just download and run the nvidia unified installer from their website. It will install the new kernel module. The link is: [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

---

### Post by jasapper on 2008-06-24
> **anindya_m said:**
> You need to recompile the nvidia kernel module for the new kernel. There should have been a corresponding nvidia upgrade on synaptic. If not, just download and run the nvidia unified installer from their website. It will install the new kernel module. The link is: [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

I can't believe I had not run across the issue before now, or at least seen references while perusing the forums. I took another look right after posting and whaddya know [there it was]("http://ubuntuforums.org/showthread.php?t=797270"), a HOWTO no less! Just booted the new kernel in recovery reinstalled the driver. Also went ahead and setup the script to do this automatically in the future. As always I am better for the experience.

---

