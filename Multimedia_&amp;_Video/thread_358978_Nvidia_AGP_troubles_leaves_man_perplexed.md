---
title: "Nvidia AGP troubles leaves man perplexed"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by sayhello on 2007-02-11
Hello everyone,

I replaced my X800Pro for a 7800GS (on an Abit AV8 KT800PRO board, with a amd64 cpu, an AGP bus and running Edgy i386), after reading about how nvidia drivers are so much better. Using the Nvidia binary drivers, I have been able to configure twinview and DRI in a  pinch, as well as setting my primary monitor to my flat panel, with proper refresh rates for both monitors... a combination of things which wasn't so easy with FGLRX!
Everything worked fine, 3D, beryl and all...

However, I faced a very big problem: random lockups/freezes/system instability.
Reading forum posts, the nvidia driver FAQ and so on, it would seem all these problems might go away after switching to the nvidia AGP module, rather than the one bundled with Linux.

To confirm I was using the AGPGART module, a "cat /proc/driver/nvidia/agp/status" showed me AGP was enabled with the AGPGART module.

Since doing a "lsmod | grep agp" yielded me "amd64_agp" and "dmesg | grep -i nvrm" gave me the message that the nvidia module could not be loaded because the agpgart backend was already loaded, I knew I had to prevent those from loading.

To do so, I resorted to blacklisting the incriminating modules (agpgart, amd64_agp) in /etc/modprobe.d/blacklist.
Blacklisting will work in my case since I am running the i386 build of Linux, which loads agpgart as a module, as confirmed in "/usr/src/linux-headers-2.6.17-11-386/.config".

After rebooting, this seems to have done the trick:
```

$ lsmod | grep nvidia
nvidia               6827412  22 
agpgart                33456  1 nvidia
i2c_core               22288  6 i2c_ec,w83627hf,eeprom,i2c_isa,nvidia,i2c_viapro

```
```

$ dmesg | grep -i nvrm
[17179605.776000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006

```

No errors, w00t. And of course, NvAGP is set in my xorg.conf in the device section as "1".
As well, looking for errors in /var/log/Xorg.0.log is fruitless everything seems to be running peachy:
```

$ cat /var/log/Xorg.0.log | grep -i agp
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Use of NVIDIA internal AGP requested

```

HOWEVER, agp is not enabled anymore:
```

$ cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput  
of the 'dmesg' command and/or your system log file 
for additional information on this problem.

```

It seems everything is in place for the NVIDIA agp module to take over, and it apparently does, since it gets loaded. However, even after specifying it is the module I want to use, AGP is not enabled.
There are no related error messages in either dmesg, Xorg.0.log or syslog, thus my confusion.

Removing agpgart and amd64_agp from the blacklist lets me get AGP back with the appropriate NvAGP setting, albeit with the accompanying lockups.
Running with AGP off, my pc is actually much more stable than with AGPGART.

Can somebody help me fix this puzzling AGP problem?

---

### Post by fpo on 2007-02-12
Hi!
I've just upgraded the kernel 2.6.17-10 to 2.6.17-11 and reinstalled, as usual, the last available NVIDIA drivers for my graphic card (GeForce4 Ti 4600) and I'm now getting into the same troubles as you describe. Everything seems fine, no error message, 3D desktop just works but the system is freezing when running other 3D applications (with or without beryl). It never happened before with the same configuration. I've notice an excessive charge of CPU that I believe to be the cause of the problem. Unfortunately I've no suggestion how to solve it.

---

### Post by sayhello on 2007-02-12
A possible solution to the lockups is to change the built-in AGP module to the one supplied by Nvidia. Did you try following the steps I described above?

That SHOULD work for you.

But for me, the NVIDIA agp module is not working somehow. =(

---

### Post by sayhello on 2007-02-13
bump di bump?

---

### Post by fpo on 2007-02-14
Hi,

Yes I tried your trick but it doesn't make any noticeable improvement for me. The system is still unstable with 3D applications. However, for me, AGP is always loaded in both settings (with internal AGP or not).

These are my outputs (in my case agpgart and intel_agp are blasklisted):
```
$ lsmod | grep nvidia
nvidia               4717620  22 
agpgart                34888  1 nvidia
i2c_core               23424  2 i2c_ec,nvidia

$ dmesg | grep -i nvrm
[17179586.560000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[17179779.444000] NVRM: Xid (0001:00): 8, Channel 00000002

$ cat /var/log/Xorg.0.log | grep -i agp
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(II) NVIDIA(0): Detected AGP rate: 4X

$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Enabled
```

I don't know why it doesn't work for you but anyway it seems that it doesn't help

---

### Post by Rotarychainsaw on 2007-02-14
I read that the nvidia agp module only supports some specific chipsets. Maybe yours is too new or something. I think it is in the readme.

---

### Post by sayhello on 2007-02-15
I fixed the problem. Here's how:

I got frustrated after a few sleepless nights and decided to throw the towel.  I put my X800Pro back in, made necessary changes and rebooted. I saw that FGLRX was somewhat corrupted and nothing was working right. I went in synaptic, looking for some drivers and lo and behold, there sat the 9746 drivers from Nvidia in the restricted repository.

So, i decided to give that a shot and guess what... it works flawlessly!
No freezes, beryl works awesome and I get 13,000+ FPS on glxgears. Its stable on stock agpgart with sideband addressing and fast writes.

So, give that a shot and let me know how that goes.

EDIT: prior to using the drivers from restricted repo's, I was attempting to use Nvidia's binary drivers.

---

### Post by sumadartson on 2007-02-15
Same problems here, been struggling with it for days. The above fix didn't work though. Any suggestions?

---

### Post by keithjr on 2007-02-15
You can try and see if the beta drivers work any better for you.  These are use-at-your-own-risk, however..

[http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9625.html](http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9625.html)

---

### Post by sayhello on 2007-02-16
d'oh! The crashes never went away, I just hadn't run my system long enough. I talked too fast. Changing to the ubuntu repository packages did not change my situation. I still cannot use the NVIDIA agp module.
Disabling AGP still causes crashes.

any suggesstions?

---

### Post by Rotarychainsaw on 2007-02-16
I have no suggestions, I was just going to tell you tha I have the same problems. I got excited when you said the repo version worked, so I tried it out. Same thing with me, worked well, but still locked up sometimes. 

I gave up on nvidia on this damn laptop, I'm using the nv driver because at least suspend kind of works. haha.

---

### Post by tseliot on 2007-02-16
Try point 4 of the Problems Section of my guide and see if it solves the problem:
[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html)

---

### Post by sayhello on 2007-02-17
By point 4, did you mean the problems section?

Well, after doing the whole driver installation process many times, I looked into an automated way of doing things. I used envy, and used GCC version 4.1 since that's what the nvidia installer was expecting.

As far as running with renderaccel off, I will do so and let you know if that solves the stability problem.
I have read some people had freezes while being able to ssh in and finding out that nvidia drivers are taking 100% cpu utilization. I, on the other hand, have hard lockups. No sshd responding, nothing.

Thanks for looking into our problem, however :)

---

### Post by sayhello on 2007-02-20
Well I tried fumbling around for a few days, banged my head against the wall quite a bit. No dice.
When AGP is on, there are lockups. When it is off, my system is much more stable, albeit not totally lockup free.

Would any of the log files help?

---

### Post by sayhello on 2007-02-23
I wondered more and more if the problem was hardware related.
Well... It works totally fine in winblows.

I need to make a correction. Using the ubuntu-restricted-repo drivers nvidia-glx, with AGP ON (using AGPGART) with SBA on and FW off, it is now seemingly more stable than with AGP off.

HELP!

---

### Post by sayhello on 2007-02-24
I might very well have found the cure.
In a last-ditched attempt to fixing the problem, I realized that my computer only froze when my cpu throttled down (I have cool n quiet enabled).

Turning that off has made my computer lockup free for 24 hours so far!

Now, was that enabled when my ATI card was in the case? Maybe, maybe not. But it looks like I've found the real culprit. I'll report back if that changes =D

Good luck

---

### Post by tseliot on 2007-02-24
> **sayhello said:**
> I wondered more and more if the problem was hardware related.
Well... It works totally fine in winblows.

I need to make a correction. Using the ubuntu-restricted-repo drivers nvidia-glx, with AGP ON (using AGPGART) with SBA on and FW off, it is now seemingly more stable than with AGP off.

HELP!

You can ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

