---
title: "nVidia fadeout effect doesn't work"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by craftybones on 2006-11-25
Hello,

I have the following setup:

AMD64 3700
1 Gig Ram
80G Maxtor IDE hard drive
300G Seagate SATA
Nvidia GeForce 6100 (onboard)

I installed the Nvidia drivers off the Ubuntu reps, everything works as such, however, you know the Ubuntu "fadeout" effect when you leave the computer idle for a bit? It doesn't fadeout gradually, I wonder if it has anything to do with settings or whatever. Does anyone know? Drivers don't seem to be an issue, is there anyway of benchmarking the driver?

Please let me know.

Thank you,

craftybones

---

### Post by craftybones on 2006-11-25
From all the previous posts I read, I gathered that this was a problem in Ubuntu Dapper or earlier. However, i am running Edgy.

craftybones

---

### Post by incubus on 2006-11-25
Hey craftybones,

By that do you mean that the fadeout happens instantly or that it's choppy?
Are you getting acceleration? (I don't think this is related)
```

$ glxinfo |grep direct

```

incubus

---

### Post by craftybones on 2006-11-25
Hello incubus,

Thanks once again for your speedy reply.

Yes the fade out is really choppy.
```

moonwolf@trantor:~$ glxinfo | grep direct
direct rendering: Yes

```

What next? I am guessing this is a driver issue...

Craftybones

---

### Post by incubus on 2006-11-25
Oh boy, you're out of luck, aren't you.  haha. : )

Have you tried it without the nvidia driver? Say, nv or vesa?

incubus

---

### Post by craftybones on 2006-11-25
I've tried it with vesa, the nvidia driver didn't load upon install. With vesa, everything else is choppy, haven't tried NV yet.

craftybones

---

### Post by incubus on 2006-11-25
craftybones,

I'm afraid I won't be able to offer much help.  It could be the module, but it could also be that something's wrong with your set up.

Is glxgears also choppy?
```

$ glxgears

```

I would also run "top" for a while and see if everything is going as expected. See if there's something taking up a lot of resources. Also, double check that your processor is recognized at /proc/cpuinfo

incubus

---

### Post by craftybones on 2006-11-25
glxgears isn't choppy.

top doesn't reveal anything majorly wrong.

Processor, is also recognized just fine. I also tried running Euphoria and Euphoria runs like a charm, highly doubt its the module if such things do work.

craftybones

---

### Post by craftybones on 2006-11-25
[http://ubuntuforums.org/showthread.php?t=267600&highlight=fade](http://ubuntuforums.org/showthread.php?t=267600&highlight=fade)

The above seems to claim that this is a problem with the distribution itself. However, I've seen this effect work just fine on some other systems.

craftybones

---

### Post by incubus on 2006-11-25
I'm with you, craftybones.

Too bad I don't have GNOME here.  I have no idea where to look at.  But it seems something related to GNOME, I would say.

Let's wait for somebody more savvy to come around.

incubus

---

### Post by incubus on 2006-11-25
The weird thing to me is that you said you had Dapper before and everything worked just fine.

incubus

---

### Post by incubus on 2006-11-25
Is this related to what you're seeing?

[https://bugs.launchpad.net/distros/ubuntu/+source/gnome-session/+bug/12389](https://bugs.launchpad.net/distros/ubuntu/+source/gnome-session/+bug/12389)

incubus

---

### Post by craftybones on 2006-11-25
Yeah, the bug you posted, sounds exactly like the problem I've had so far. In fact, the systems I've seen it work on have all had CRT monitors. Thanks a ton. Will follow the bug up and see what's happening.

Thanks,

craftybones

---

### Post by craftybones on 2006-11-25
True, but I am not sure I entirely paid attention to the fade effect then. I've become nitpicky ever since Ubuntu started playing russian roulette with my SATA drive :)

Thanks once again.

Craftybones

---

