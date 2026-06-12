---
title: "Can't get midi synthesizer to work (Yoshimi)"
date: 2011-06-28
forum: Multimedia Software
---

### Post by oxf on 2011-06-28
HI,

Maybe someone can help me with this. I installed the Yoshimi midi synthesizer. When I try and start it I get the following silly message

"Bad things happened... Yoshimi strategically retreats!" :confused:
I presume this is a fancy way of saying something didn't install properly? So I've reinstalled it in synaptic and it still does this.

Is there any way of getting to the bottom of whats happening? Any advice appreciated.

Katya

---

### Post by oxf on 2011-06-28
Any ideas??

---

### Post by kayosiii on 2011-06-29
Yoshimi is a version of ZynAddSubFx specifically tailored towards low latency usage. Running jackd is probably a requirement to get this to work correctly and you will want to have your system set up for that. Check the Ubuntu Studio forum for details on that.

If low latency is not important to you then I suggest ZynAddSubFx as it should sound almost identical.

---

### Post by oxf on 2011-06-29
> **kayosiii said:**
> Yoshimi is a version of ZynAddSubFx specifically tailored towards low latency usage. Running jackd is probably a requirement to get this to work correctly and you will want to have your system set up for that. Check the Ubuntu Studio forum for details on that.

If low latency is not important to you then I suggest ZynAddSubFx as it should sound almost identical.

Thanks

ZynAddSubFx sems to work but hogs 95% of my CPU!!!

I seem to already have the jackd packages so don't know why Yoshimi doesn't launch.

Katya

---

### Post by cchhrriiss121212 on 2011-06-29
You will need to start jack to make use of it. Should be listed as "jack control" in your menu, once it is started open yoshimi then use the connection window to connect it to your audio output.

---

### Post by oxf on 2011-06-29
> **cchhrriiss121212 said:**
> You will need to start jack to make use of it. Should be listed as "jack control" in your menu, once it is started open yoshimi then use the connection window to connect it to your audio output.

OK

Many thanks!

Katya

---

