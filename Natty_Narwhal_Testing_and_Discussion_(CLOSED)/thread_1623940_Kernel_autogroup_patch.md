---
title: "Kernel autogroup patch"
date: 2010-11-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2010-11-17
Nice news... Isn't they...?
And, it seems it works.
I did not compile yet but I'm using some patched kernels now, just for the fun of it... :)

---

### Post by VMC on 2010-11-17
> **zika said:**
> Nice news... Isn't they...?
And, it seems it works.
I did not compile yet but I'm using some patched kernels now, just for the fun of it... :)

I'm thinking your referring to the Fast Desktop patch as explained [here]("http://blogs.computerworld.com/17371/the_linux_desktop_may_soon_be_a_lot_faster").

The patch explained(?!) [here]("http://marc.info/?l=linux-kernel&m=128978361700898&w=2").

This is the first time I came across any info on the autogroup patch. 

I wasn't sure what you were referring to so by accident I came across the patch while reading the LXer News.

---

### Post by zika on 2010-11-17
Sorry, I was not precise enough...
But, nevertheless, we **are** talking about the same patch...

---

### Post by moviemaniac on 2010-11-18
I'm already using this patch (since yesterday). Patched 2.6.37-rc2 with it and I'm absolutely amazed by the improvements. Couldn't see any negative effects, just positive ones - like being able to watch BD-movies while compiling the kernel in the background or much better - subjectively felt - responsiveness in everyday-applications with BOINC steaming ahead in the background. I can also confirm (subjectively, not tested) webpages to load faster. Very nice indeed.

---

### Post by dino99 on 2010-11-18
is there a ppa with this patched kernel ?

---

### Post by Asraniel on 2010-11-18
for 10.10 too if possible :)

---

### Post by zika on 2010-11-18
Currently I'm using liquorix 2.6.36 ... :)
Even though this patch should be useful for those that use lot of tty, I think I get snappier desktop, better flow and snappier web pages. I did not make enough time to compile 2.6.37 with only that change so I could be sure what is responsible for my feeling and better measurements...
It is not important, though, we are looking into a better future... :)

---

### Post by VMC on 2010-11-18
> **zika said:**
> Currently I'm using liquorix 2.6.36 ... :)
Even though this patch should be useful for those that use lot of tty, I think I get snappier desktop, better flow and snappier web pages. I did not make enough time to compile 2.6.37 with only that change so I could be sure what is responsible for my feeling and better measurements...
It is not important, though, we are looking into a better future... :)

I added that liquorix to my repo for Lucid and it IGN's it.
What is the source you used for sources.list ?

thanks.

---

### Post by zika on 2010-11-18
> **VMC said:**
> I added that liquorix to my repo for Lucid and it IGN's it.
What is the source you used for sources.list ?

thanks.[http://liquorix.net/](http://liquorix.net/)

---

### Post by JDorfler on 2010-11-18
Hey Zika, you find anything broken when you installed this?  I'm just wondering.  I'd like to give a whirl, but I don't want to break anything.

---

### Post by marl30 on 2010-11-18
I just read about this on this blog, and I want it. However, the instructions on the blog is not noob friendly so I'm not getting anywhere trying to make this work: [http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

---

### Post by VMC on 2010-11-18
> **zika said:**
> [http://liquorix.net/](http://liquorix.net/)

That's exactly the link I used. At first the keyring errored out, but I got that to work. I put #/etc/apt/sources.list.d/liquorix.list
deb [http://liquorix.net/debian](http://liquorix.net/debian) sid main
on my sources.list but nothing happened.

---

### Post by zika on 2010-11-18
> **JDorfler said:**
> Hey Zika, you find anything broken when you installed this?  I'm just wondering.  I'd like to give a whirl, but I don't want to break anything.
No guarantee. If I have noticed something wrong, believe me, I would have reported... :)
It's just a kernel... :)

---

### Post by zika on 2010-11-18
> **VMC said:**
> That's exactly the link I used. At first the keyring errored out, but I got that to work. I put #/etc/apt/sources.list.d/liquorix.list
deb [http://liquorix.net/debian](http://liquorix.net/debian) sid main
on my sources.list but nothing happened.
Update.
Install linux*liquorix*... 2 files... It is the same as if You were to install Ubuntu kernel, just without _all.deb... :)
I have &#8222;deb [http://liquorix.net/debian](http://liquorix.net/debian) sid main future&#8220; ...

I think the current names are: linux-headers-2.6.36-0.dmz.13-liquorix-amd64 and linux-image-2.6.36-0.dmz.13-liquorix-amd64, in my case...

---

### Post by VMC on 2010-11-18
> **zika said:**
> Update.
Install linux*liquorix*... 2 files... It is the same as if You were to install Ubuntu kernel, just without _all.deb... :)
I have &#8222;deb [http://liquorix.net/debian](http://liquorix.net/debian) sid main future&#8220; ...

I think the current names are: linux-headers-2.6.36-0.dmz.13-liquorix-amd64 and linux-image-2.6.36-0.dmz.13-liquorix-amd64, in my case...

I know I'm missing something here. This is all I got at sources.list:

```
deb http://liquorix.net/debian sid main
```

EDIT: When I update, I get the following:
```
Hit http://liquorix.net sid Release.gpg
Ign http://liquorix.net/debian/ sid/main Translation-en_US                                                                                                   
Hit http://liquorix.net sid Release                                                                                                                          
Ign http://liquorix.net sid/main Packages                                                                        
Ign http://liquorix.net sid/main Packages                                                                       
Hit http://liquorix.net sid/main Packages                            

```

---

### Post by cariboo on 2010-11-18
I just did[ Lennart's]("http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html") solution on my netbook running Unity. It does feel faster, and it's much easier than compiling a new kernel. :)

---

### Post by plun on 2010-11-18
> **cariboo907 said:**
> I just did[ Lennart's]("http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html") solution on my netbook running Unity. It does feel faster, and it's much easier than compiling a new kernel. :)

Yup also running it but LennartP is hard on Linus...;)

[http://marc.info/?l=linux-kernel&m=128993935321081&w=2](http://marc.info/?l=linux-kernel&m=128993935321081&w=2)

I am running on a i3 laptop with an Intel SSD and I cannot see any differences.....

Must load up an 1080p movie and a heavy Compiz rebuild at the same time
and retest  ..:D

---

### Post by zika on 2010-11-18
Just to do restart... :)
Thank You...
We will see if it collides with liquorix kernel... :)

It works with 2.6.37-999...
It works with liquorix kernel, also. It is optimized in more other ways than just this, so...

---

### Post by vade on 2010-11-18
Any experiences on using this and the brain **** scheduler together, or are they mutually exclusive?

---

### Post by amano on 2010-11-18
It is funny to read that Linus and that Poettering guy are completely in love: [http://marc.info/?l=linux-kernel&m=128992756502756&w=2](http://marc.info/?l=linux-kernel&m=128992756502756&w=2)

And Peter Zijlstra as well :popcorn:

---

### Post by Starks on 2010-11-18
Linus' reasoning against the userspace implementation as suggested by Poettering is pretty sound. Putting things in the kernel makes implementation and usage more universal.

---

### Post by psusi on 2010-11-18
It is an optimization for a silly load ( running 64 threads at once with far fewer cpu cores ) that has been blown absurdly out of proportion by Phoronix.

---

### Post by Starks on 2010-11-19
As they usually do.

They're a Linux tabloid.

---

### Post by MacUntu on 2010-11-19
> **Starks said:**
> They're a Linux tabloid.

And there's enough kernel drama to write about. :P

---

### Post by psusi on 2010-11-19
> **Starks said:**
> 
They're a Linux tabloid.

Good description... I hadn't thought of that one when trying to classify them.

---

### Post by ruik on 2010-11-22
This just got included in the Natty kernel:


> [ Tim Gardner ]

  * [Config] CONFIG_SCHED_AUTOGROUP=y

  [ Upstream Kernel Changes ]

  * sched: automated per session task groups


---

### Post by zika on 2010-11-22
> **ruik said:**
> This just got included in the Natty kernel:Nice! I've noticed that in mail...

---

