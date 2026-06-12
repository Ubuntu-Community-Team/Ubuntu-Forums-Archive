---
title: "How do I install SND-VIRMIDI"
date: 2008-07-12
forum: Multimedia Software
---

### Post by jukingeo on 2008-07-12
Hello All,

I need to work with an application called JOrgan and it requires a sound module called SND-VIRMIDI.  It supposed to allow virtual midi devices to communicate between applications in Ubuntu.  Despite having Ubuntu Studio, this module isn't present and I need to install it.

I looked in Synaptic and in the ADD/REMOVE programs and I couldn't find the module listed in either.

I am wondering if anyone can assist me in loading SND-VIRMIDI on my machine.

EDIT:

I been noticing very few posts in regards to this module, I did notice that even on line, any mention of it has stopped around the the time of the release of Hardy.  So I am guessing perhaps that SND-VIRMIDI has a modern replacement?

I am not sure, I am new here, so I don't know much about this.  

Please advise.

Thank You,

Geo

---

### Post by raboofje on 2009-01-24
For those stumbling upon this thread like me:

snd-virmidi is a kernel module. It is provided in a file like /lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-virmidi.ko and lives in the linux-image package.

You can load this module by typing 'sudo modprobe snd-virmidi' on the command line.

---

### Post by jukingeo on 2009-01-25
> **raboofje said:**
> For those stumbling upon this thread like me:

snd-virmidi is a kernel module. It is provided in a file like /lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-virmidi.ko and lives in the linux-image package.

You can load this module by typing 'sudo modprobe snd-virmidi' on the command line.

Hello,

Wow!  This thread I posted IS old!  At any rate, I was suggested (in other forums as you said, however, it wouldn't work.  As it turned out, back then I had to recompile a kernel to get the Sound Blaster X-Fi to work.  Apparently I may have accidentally told the compiler NOT to install vir-midi.  So without it, it would have never worked.

Since then I have discontinued the use of the SB X-Fi.  While it did work beautifully (via the method posted in my sig below), the problem was that it was a build based on the NON real-time kernel of Ubuntu. We tried to do a recompile with the RT kernel for the ALSA drivers for the X-Fi, but it didn't work.

So I pulled the X-Fi and tried other sound alternatives.  I DID become very frustrated with Ubuntu, and almost dropped it.  BUT, my last attempt at audio in Linux was the charm.  I bought myself an M-Audio Delta 44 and almost instantly all my troubles went away.

Supposedly M-Audio was one of the few companies that offered full support of their product under Linux and as a result it is pretty much Plug-N-Play in Linux.

So that made me VERY happy as now I can use all those nice audio programs that come with Ubuntu Studio...AND use them with the Real Time kernel as well.

Well, thanx for chiming in anyway.  But this is an old outdated post that I long forgot about.

Geo

---

