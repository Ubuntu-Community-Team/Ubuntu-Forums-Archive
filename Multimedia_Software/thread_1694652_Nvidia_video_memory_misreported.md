---
title: "Nvidia video memory misreported"
date: 2011-02-24
forum: Multimedia Software
---

### Post by yoda2031 on 2011-02-24
I'm trying to increase my framerate on World of Warcraft, and I'm not sure if this will help but it should in theory.  I'm not even sure if I'm right in my assumption that it's currently non-optimal.

nvidia-settings reports the full 1024MB of onboard video memory from my 420GT, but lspci reports three separate figures which don't even add up to 256MB:

01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ZOTAC International (MCO) Ltd. Device 1167
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=128M]
	Memory at e8000000 (64-bit, prefetchable) [size=32M]
	I/O ports at dc80 [size=128]
	[virtual] Expansion ROM at efe00000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

Now, I don't know which to trust, is all the video memory being detected or just the pittance that lspci reports?

To my mind, more graphics memory means you can store more graphical code and data closer to the gpu resulting in faster framerates, right?

So, is there any way to correct the problem (if it exists) and/or increase the performance of the card?

Thanks in advance.

---

### Post by tjones00 on 2011-02-24
> Now, I don't know which to trust, is all the video memory being detected or just the pittance that lspci reports?

To my mind, more graphics memory means you can store more graphical code and data closer to the gpu resulting in faster framerates, right?

pittance in lspci.

In theory yes more memory can increase performance but it's also used as a upseller by many graphics cards manufacturers. More ram doesn't necessarily mean faster. Faster ram and gpu means faster.

ie. a 1GB card isn't necessarily faster than a 512mb card with the same gpu if more than 512mb isn't used due to bandwidth limitations.

It's the same selling point as rpm with a hdd 7200 rpm doesn't mean its faster than a 5600 rpm drive. bandwidth tests that manufacturers generally do not report is the definitive speed test for a hdd.

Since you can't tweak the ram settings on graphics cards the way people get improved performance is by overclocking the gpu.

---

### Post by yoda2031 on 2011-02-24
> **tjones00 said:**
> 
pittance in lspci.
[QUOTE]
So something is wrong, then.  I have 1024MB on the card, it says so on the box and I have no reason to doubt that fact.

[QUOTE=tjones00;10492027]
In theory yes more memory can increase performance but it's also used as a upseller by many graphics cards manufacturers. More ram doesn't necessarily mean faster. Faster ram and gpu means faster.


I realise that.  However, video memory is closer (in terms of latencies, and coincidentally physically) to the GPU than system memory, because it's on the same card.  If I can utilise more video memory for graphics-related code and data, the result is a decrease in overall graphical latencies.  Correct me if I'm wrong.

> **tjones00 said:**
> 
ie. a 1GB card isn't necessarily faster than a 512mb card with the same gpu if more than 512mb isn't used due to bandwidth limitations.


Since I already own a 1GB card, this point is moot.

> **tjones00 said:**
> 
It's the same selling point as rpm with a hdd 7200 rpm doesn't mean its faster than a 5600 rpm drive. bandwidth tests that manufacturers generally do not report is the definitive speed test for a hdd.
[QUOTE]

Bandwidth tests are not reported because you need to test the drive inside a given system.  Latencies from many internal components (hardware and software) contribute to a hard drive's resulting bandwidth.  Upgrading from a 5400 to its 7200 equivalent without changing any other components will almost always produce a performance increase.  One should also note that bandwidth is not a good measurement of overall drive performance; picture the case where you're reading 50 files from 50 different locations on the drive at once - which is not uncommon in servers and gaming rigs - you want your disk to be able to seek to the new locations as quickly as possible.  But this thread is not about hard drives, it's about graphics cards.

[QUOTE=tjones00;10492027]
Since you can't tweak the ram settings on graphics cards the way people get improved performance is by overclocking the gpu.

Overclocking the GPU is not generally a good idea.  If you're lucky, you'll get a slight performance increase.  If you're not quite so lucky, you'll have your GPU throttled and get a moderate performance decrease.  If you're unlucky, you'll have your GPU significantly throttled and end up with severely degraded performance.  If you're unluckier still, you'll have your GPU reset from time to time.  If you're unluckier than that, you'll have your GPU melt and become worthless.  If you're the unluckiest man ever, your GPU will melt onto your motherboard resulting in a bricked system.

"Can't tweak the ram settings on graphics cards" - what exactly did you mean by this?  I can't figure out to which "settings" you refer.

Thanks for your reply, and I apologise in advance if I offended you with my response, it may come across terse as I am quite tired and not very good with people.

---

### Post by cchhrriiss121212 on 2011-02-25
There is nothing wrong with either lspci or the card, the output you have is normal.
[http://www.linuxquestions.org/questions/linux-hardware-18/lspci-v-determining-video-memory-853165/](http://www.linuxquestions.org/questions/linux-hardware-18/lspci-v-determining-video-memory-853165/)

---

### Post by yoda2031 on 2011-02-25
> **cchhrriiss121212 said:**
> There is nothing wrong with either lspci or the card, the output you have is normal.
[http://www.linuxquestions.org/questions/linux-hardware-18/lspci-v-determining-video-memory-853165/](http://www.linuxquestions.org/questions/linux-hardware-18/lspci-v-determining-video-memory-853165/)

Thank you.  I wonder why I didn't find when I was searching... oh well.

---

