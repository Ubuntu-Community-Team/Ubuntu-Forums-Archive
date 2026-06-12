---
title: "NVIDIA 180.29 - problems installing"
date: 2009-02-21
forum: Multimedia Software
---

### Post by sgcharest on 2009-02-21
I've tried to download and install the driver several times from the NVIDIA site [http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html) , and am unable to install it according to the NVIDIA site directions.  The pkg downloads to my desktop.  I then run ""sh NVIDIA-Linux-x86-180.29-pkg1.run" as per the instructions, and am told I can't install it.  For some reason I also cannot "accept" the terms and usage page either.  Perhaps the two problems are connected?  Any thoughts would be welcome.

Second question:  I believe my processor is 64 bit capable but not sure.  How can I tell?

Using 8.10 32 bit, 2 meg RAM, NVIDIA 8600 with 500k memory.

Thanks in advance.

---

### Post by jeeves on 2009-02-21
If you have not already found these, try the instructions here they are much more detailed than what's on the Nvidia site:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

*I believe my processor is 64 bit capable but not sure. How can I tell?*

There are a bunch of ways to do this. The simplest is probably to launch the **System Monitor** and look on the and look on the "System" tab for the **Hardware Information**. 


Another method  would run be the following in a terminal:
```

cat /proc/cpuinfo
```
This return a bunch of info about your CPU including the "model name". You will probably be able to tell from that model name, if not a little googling the model name will probably indicate if its 32 or 64 bit.

---

### Post by norwoods on 2009-02-21
i can tell what processor i have from the Applications--System Tools--sysinfo application.  then look up the processor with google and 64 bit.  for example, i google intel celeron 420 64 bit and get a link to a wikipedia web site which lists: Instruction set 	x86, x86-64

what version of ubuntu are you running? i upgraded to 8.10 for nvidia driver availability.

---

### Post by sgcharest on 2009-02-21
Worked great.  Thanks.  I'm using 8.10 Intrepid 32 bit but going to upgrade to 64 bit shortly to go with my 64 bit processor.  Thanks again.

---

