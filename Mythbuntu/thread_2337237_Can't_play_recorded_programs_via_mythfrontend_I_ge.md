---
title: "Can't play recorded programs via mythfrontend I get sound but no picture"
date: 2016-09-15
forum: Mythbuntu
---

### Post by bruban2 on 2016-09-15
I have just upgraded my Ubuntu 14.04 to Ubuntu 16.04.1 (note: I'm not using Mythbuntu). 

My previous Mythtv installation was rock solid for many years.

I'm finding a string of problems with the upgrade of Mythtv that I'm slowly resolving.

I'm finding it very difficult to solve my latest issue.

From the mythtv frontend, when I select a recorded program to watch, I get the message 'Please Wait' as normal, and then find that mythtv frontend has crashed. I hear the TV recording playing, but I cannot see a picture.

I see the following messages in /var/log/syslog that correspond to the time of the problem:

> 
Sep 16 10:47:06 mythtv gnome-session[1513]: QOpenGLContext::swapBuffers() called with non-exposed window, behavior is undefined
Sep 16 10:47:06 mythtv kernel: [  232.292521] snd_hda_intel 0000:01:00.1: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Sep 16 10:47:06 mythtv gnome-session[1513]: message repeated 11 times: [ QOpenGLContext::swapBuffers() called with non-exposed window, behavior is undefined]


I get the same issue when I try to watch live TV.

In trying to resolve this issue, I have purged and then re-installed the package mythtv-frontend using apt-get. The issue still persists.

I have done considerable searching to try and resolve the issue. The closest that I have found is [this mythtv post]("https://forum.mythtv.org/viewtopic.php?f=29&t=1393"). See the post by harpax at the bottom of the thread at Thu Apr 28, 2016 6:21 pm.

harpax suggested that: > This issue seems to be with QT 5.5.1 (maybe other versions of 5.5?). After a recent update to QT 5.6.0 the issue was gone

However, it appears that QT 5.6.1 won't be available until Ubuntu 16.10. 

I am trying to keep to the LTS version 16.04.1, but will change if I have no option.

Does anyone have any suggestions on how to resolve this?

---

### Post by uteck on 2016-09-17
Do you know if the video driver got changed during the upgrade?

---

### Post by bruban2 on 2016-09-18
Thanks for responding Utek. I appreciate it.

 Under Ubuntu 14.04, I was using the nouveau drivers. I use my Samsung TV as my monitor via a HDMI connection.

After upgrade, I could not get my display recognised when using my TV. My display was OK though using a flat panel monitor.

After upgrade and a number of experiments, I settled on the nvidea binary drivers. I now have my Ubuntu install displaying on my Samsung TV.

Details are:

Graphics Card:
```
root@mythtv:~# lshw -c video
  *-display               
       description: VGA compatible controller
       product: GF108 [GeForce GT 430]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:34 memory:f9000000-f9ffffff memory:e0000000-e7ffffff memory:ee000000-efffffff ioport:ef00(size=128) memory:fa000000-fa07ffff
root@mythtv:~# 

```

Driver:
```
root@mythtv:~# lspci -nnk | grep -i vga -A3
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 430] [10de:0de1] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GF108 [GeForce GT 430] [1043:836d]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_364_drm, nvidia_364

```

Note that I can play video files outside of Mythtv.

Any thoughts?

---

### Post by Caysho on 2016-10-17
I just encountered this.

On 16.04.1 amd64 with the nvidia driver.
It was working a day ago, I think the change has been updating the kernel.

kernel version is 4.4.0-43-generic

Setting the Appearance to use Auto or OpenGL does resolve it.

Keeping Qt in Appearance and changing to the nouveau driver also works.

I suspect it is an interaction between the nvidia driver and the updated kernel.

Which kernel are you on ?

---

### Post by bruban2 on 2016-10-17
Hi Caysho.

Thank you very much for responding to this thread. I appreciate it.

My environment has changed since I reported this, but the issue has again reappeared.

Changes:


[LIST]
[*]I have rebuilt my system. 
[*]I did a clean install of Mythbuntu 14.04.5. I could play recordings OK and did not see this issue. 
[*]Unfortunately my Mythtv database backup was at a newer version of mysql, so I had to upgrade this install to Mythbuntu 16.04.1. 
[*]I restored my old mythtv database successfully. 
[*]I am again getting the same issue with sound but no picture (and mythfrontend crashing). 
[*]I have removed my nvidia card and have reverted to the onboard Intel i915 video and default driver. 
[*]The issue still remains under the intel driver. 
[/LIST]

My kernel is:

```
root@mythtv:/home/bruce# uname -a
Linux mythtv 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```


I have also noted in my mythfrontend log the following error if that helps:

```
Oct 18 10:12:14 mythtv mythfrontend.real: mythfrontend[1682]: E Decoder avformatdecoder.cpp:4932 (GetFrame) decoding error#012#011#011#011eno: Unknown error 541478725 (541478725)
```

I'll try the config setting changes that you suggest.

Many thanks again.

---

### Post by bruban2 on 2016-10-17
Thank you Caysho,

The menu change that you suggested resolved my problem.

For others who have the same problem:

From the Mythfrontend menu, select Setup>Appearance and change the menu item 'Paint Engine:' to use 'Auto'

This was a very frustrating issue to resolve. Thanks also to Utek for your help early on.

---

