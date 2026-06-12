---
title: "Optimus in 14.04 - for nvidia drivers, still need to blacklist nouveau drivers?"
date: 2014-05-17
forum: Multimedia Software
---

### Post by Remten on 2014-05-17
There are a number of past discussions that recommended blacklisting the default nouveau video drivers before installing nvidia proprietary drives. (An example is [here]("http://ubuntuforums.org/showthread.php?t=2181525&p=12820797#post12820797").)
As of Ubuntu-family 14.04, is it still necessary --or if not necessary, is it advisable-- to do that? If it is, does that apply regardless of whether you are installing via, say, Synaptic package manager, as opposed to downloading the drivers directly from the NVidia website and then installing from the command line?

(I am particularly interested in Lubuntu, but I suppose this applies for all *buntu versions.)

---

### Post by deadflowr on 2014-05-17
I don't run optimus cards, but as to blacklisting the nouveau drivers, I've never needed to, as the system blacklists them when I install the nvidia drivers.
I only install from the repos, so don't know what the .run file does in that regard.

If you are running optimus, look at this
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

---

### Post by Remten on 2014-05-17
Thanks for the reply.

---

