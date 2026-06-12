---
title: "Can I rebuild Ubuntu kernel EXACTLY as it is BUT with low latency support?"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by temcat on 2006-11-11
Hi folks,

I know that I can take vanilla kernel and apply Ingo Molnar patches to it to get low latency. However, is it possible to compile Ubuntu kernel <i>exactly</i> as it (with all Ubuntu-specific patches) PLUS enable low latency? Is there any HOWTO for that?

---

### Post by Peepsalot on 2006-11-11
I don't know much about kernel compiling, but there is a project called autokernel that some people on these forums are working on  Those guys might know a way.
[http://www.ubuntuforums.org/showthread.php?t=222018&highlight=autokernel](http://www.ubuntuforums.org/showthread.php?t=222018&highlight=autokernel)

---

### Post by zettberlin on 2006-11-11
> **temcat said:**
> 
However, is it possible to compile Ubuntu kernel <i>exactly</i> as it (with all Ubuntu-specific patches) PLUS enable low latency?

yes you can, at lest you can build a kernel from the official sources with DESKTOP_PREEMPT and CONFIG_HZ=1000 enabeled - this would be like the first Dapper-Standardkernel that worked very good with jackd realtime (yet not as powerfull as with REALTIME_PREEMPT as you get with the Molnar-Patches).


> **temcat said:**
> 
 Is there any HOWTO for that?

We work on it, a friend did the trick with good results, now we reproduce it and will spread word as soon as possible.

---

### Post by temcat on 2006-11-12
> **zettberlin said:**
> a friend did the trick with good results

Cool! By the "trick", do you mean DESKTOP_PREEMPT and CONFIG_HZ or applying Ingo Molnar patches to Ubuntu stock kernel?

---

### Post by dolson on 2006-11-12
> **temcat said:**
> Cool! By the "trick", do you mean DESKTOP_PREEMPT and CONFIG_HZ or applying Ingo Molnar patches to Ubuntu stock kernel?

I used to have a tutorial to do what zettberlin is talking about up on the ubuntustudio.com wiki site that no longer exists. It is located here now: [https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption](https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption)

However, I don't think zettberlin understands what you were asking.

The answer to your question is, back during Dapper's beta days, myself and a couple others on IRC managed to created a version of Ingo's patches that applied to Ubuntu's kernel source. However, the kernel continued to morph, and we were unable to do the same thing with any release version of Dapper kernel. I tried once on Edgy and couldn't do it either, so I have given up on this. You can try it, but you will need to get your hands very very dirty, manually fixing failed chunks and making decisions about how to modify code. If you aren't good at programming, then you're most likely not going to get any further than I did.

However, since realtime patches are currently being integrated into the main kernel, it won't be long before Ingo's patch just disappears right into the source. At that point, Ubuntu will have a realtime kernel option built in.

So until then, follow the tutorial or stick to the default kernel, or tweak the default kernel for better performance. Of course if you decide to attempt patching Ubuntu's default kernel, and you succeed, please let us all know.

---

### Post by zettberlin on 2006-11-13
> **dolson said:**
> 
However, I don't think zettberlin understands what you were asking.


May be, i should have emphasized, that by merely rebuilding the standardsources, you canNOT get the same power into the kernel as you can with applied Molnarpatches. Yet you can get a kernel that works much better than the standardkernelbinaries.

> **dolson said:**
> 

However, since realtime patches are currently being integrated into the main kernel, it won't be long before Ingo's patch just disappears right into the source. At that point, Ubuntu will have a realtime kernel option built in.


wich would be the best for everyone, having a usable RT-Mainlinekernel built and maintained by dozens of professionals at canonical would allow support for VM-Wrae, NVIDIA etc also and is most preferable.
(And we should push that issue at the regarding places in the Ubunutucommunity - sometimes I have the feeling, Musicmaking does not have the needed importance amongst official developers)

---

### Post by temcat on 2006-11-13
Thanks, that was informative!

---

