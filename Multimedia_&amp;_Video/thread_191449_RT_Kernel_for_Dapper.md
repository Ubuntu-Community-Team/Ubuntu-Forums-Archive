---
title: "RT Kernel for Dapper"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by drwhizbang on 2006-06-07
Hi All,

Has anyone been working on an RT kernel for dapper? I know it was mentioned earlier, but that it was impossible to keep up with the kernel updates. Now that dapper is released and the updates have slowed I was wondering if anyone was resuming this task.

I took a stab at it myself, but I am not a kernel hacker by any stretch of the imagination, and being a reformed redhat/fedora guy I am not as familiar with the kernel patching procedure for building debs. Is there a way to split out all the separate patches so that I can find the conflicting patch? I don't know.

---

### Post by dolson on 2006-06-07
I tried, but I can't get it to patch either, and earlier on in the dev process I did it with no major issues.

At this point, I think it is a lost cause until someone with more knowledge than me can do it.

This is not really a problem that is the result of Ubuntu's massive kernel driver patching, but instead it is caused by them constantly backporting fixes and such from newer kernels.

Why not just ship the newer kernel? It is stupid to stray so far from vanilla like this that it becomes a patcher's nightmare.

I already contacted a few people to help try hacking on this, but they are busy at the moment, and hopefully we can work together at some point... Worst-case, we will wait for a new, patchable Edgy kernel, and then make that work on Dapper and provide howtos and deb packages.

---

### Post by DoctorWhizBang on 2006-06-08
Ok. Thanks for the update.

I have done this kind of thing before with fedora, but when you open up the kernel source rpm it contains a bunch of individual patches, and if can figure out which one is causing the conflict you can simply exclude it. With the deb, however, all I get is the source and one big patch. I haven't looked at it yet, so maybe I am missing  something, but I don't quite understand how they merge all the kernel patches into one diff - seems pretty ugly to me.

---

### Post by balleklorin on 2006-06-11
I've thrown out the dapper kernel and installed vanilla 2.6.16 with the rt29 patch. The only other patches I've added to the kernel besides RT is emvs and iptables. 

I notice no problems with the vanilla kernel, everything is just as before. I guess some drivers might be lacking, even though I (with a number of rare hardware devices) never had a problem with that.

---

### Post by pellgarlic on 2006-06-19
[QUOTE=balleklorin]I've thrown out the dapper kernel and installed vanilla 2.6.16 with the rt29 patch. The only other patches I've added to the kernel besides RT is emvs and iptables.[/QUOTE]

i'm planning to do something similar, except keeping the dapper kernel, and just adding another "realtime" kernel to boot into when i want to. i would like to build a kernel as close as necessary to the dapper kernel, in order to provide the same functionality if possible, although i'm having trouble finding information about what patches are applied to the ubuntu kernel. 

so, can i ask why you applied those other two patches? (i.e. have you read somewhere that they are amongst the ubuntu kernel patches, or is it from experience of compiling the kernel without them and having problems, or is it drawn from past experience of kernel compilation?)

also, can you tell me if alsa is included in the "vanilla" kernel, or have you had to install it later?

---

### Post by drwhizbang on 2006-06-19
The 2.6.17 kernel has just been released, and the following changelog entry caught my attention:

> SMP "alternatives" for x86-32. This features detects the configuration of the system at boot time, and patches certain instructions in the kernel image on the fly with optimized versions for UP or SMP, depending on what system is running.

[http://kernelnewbies.org/LinuxChanges]("http://kernelnewbies.org/LinuxChanges")

I believe this is the pathc that was conflicting when I was trying to apply the RT patch to the ubuntu kernel. If this is the case, it may be possible to merge the 2.6.17 patch from Ingo into the ubuntu kernel. I will have a look at this.

---

