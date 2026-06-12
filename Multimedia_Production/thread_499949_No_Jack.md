---
title: "No Jack"
date: 2007-07-13
forum: Multimedia Production
---

### Post by Steveway on 2007-07-13
So, I'm a regular Ubuntu user, on my second Partition is PcLinuxOS and I switch continuely between them.
Now, my question is, why is in like no app (xine, arts...) Jack installed.
On PcLinuxOS, those have Jack support but not in Ubuntu, dunno about Ubuntustudio.
Since Jack is one of the more popular Soundservers, it would be a logical thing to have Jack in most programs.
I really don't want to compile arts or xine myself only to have Jack.
So why does Ubuntu "hate" Jack?

---

### Post by fredj on 2007-07-13
Use the synaptic package manager from the System menu to install jackd and qjackctl. They are probably 
not installed by default because they don't work to their full potential without a real time kernel. 
To install the real time kernel read the first (sticky) message at the top of this forum.

---

### Post by Steveway on 2007-07-14
Yes I have it allready installed but to be usable the programs need to be compiled with Jack-support.
And most like xine and arts in the repos arent compiled with jack-support so they don't work with jack on.
On PcLinuxOS they are precompiled with Jack-support.
But why doesn't Ubuntu do this? It's not that it takes like more work, or so.

---

### Post by fredj on 2007-07-15
Yes it does take work and somebody has to do it. If you think its so easy do it yourself!

---

### Post by fredj on 2007-07-16
All they need is Alsa support in order to work under jack and if you hunt around you may find that there
are libraries that enable this.

---

### Post by Steveway on 2007-07-21
Ok, I found one thing.
Jack support in Xine seems to be really new.
That makes it understandable that it isn't in Ubuntu, yet.
But why isn't for example arts not compiled with jack-support enabled?
I'm gonna compile xine soon, with checkinstall.
If anyone wants that deb, i'm gonna post it here after i got it all done.

---

### Post by kayosiii on 2007-07-21
Jack is only supported in the experimental 1.2 branch of libxine... (it is possible to compile it from source - though for me it means that FLAC & WMA playback are broken, but I can use my external firewire sound card with Amarok).

As for arts.... I can't think of anything Arts only that I want to run.

---

### Post by fredj on 2007-07-21
Alsa is far superior to the other linux sound systems so any development effort should be concentrated
on Alsa. It is up to the developers of all audio/video programs to make their software compatible with Alsa.

---

### Post by kayosiii on 2007-07-22
fredj: 

Most pro audio software on linux uses jack - there are good reasons for this. But that is cool because jack will use alsa for supported cards but having jack functionality is important to a lot of us. (especially those of use who have cards not supported by alsa)

---

### Post by Steveway on 2007-07-22
> **fredj said:**
> Alsa is far superior to the other linux sound systems so any development effort should be concentrated
on Alsa. It is up to the developers of all audio/video programs to make their software compatible with Alsa.

Can you connect the output from one application to the input of another with alsa? No? But you can with Jack and with a very low latency.
That is one of the things Jack has over the other soundsystems.
(Didn't start to compile xine, yet.)
EDIT: Ah, yes forgot one thing.
Since OSS is going to be open-source the future for Alsa is unclear, driver-support is on par with Alsa, it is cross-plattform (Alsa is only for Linux) and it has a lower latency.

---

### Post by fredj on 2007-07-22
Steveway
When I said Alsa was a superior sound system, I wasn't excluding Jack from the equation. I use Jack
with alsa but jack is a sound server not a sound sytem.
At present I can't find any reason to prefer OSS to Alsa but I suppose that's because I have never had
a sound card that wasn't supported under Alsa.

---

