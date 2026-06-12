---
title: "HOWTO: Add realtime module to Ubuntu Feisty kernel (for JACKD or other applications)"
date: 2007-06-30
forum: Multimedia Production
---

### Post by Emblem Parade on 2007-06-30
I'm posting this as an alternative to using Ubuntu Studio's realtime kernel. This seems a much more gentler approach than compiling a new kernel!

Thanks go to Oktyabr for originally posting this on their [blog]("http://oktyabr.wordpress.com/2006/02/20/ubuntu-cleverness-part-5-realtime-lsm/").

```
sudo aptitude install linux-headers-$(uname -r)
sudo aptitude install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a get realtime-lsm
sudo m-a get realtime-lsm-source
sudo m-a build realtime-lsm-source
sudo m-a install realtime-lsm
```

On my machine, I had to enter that last command twice. I also had to reboot. Afterwards, though, I could run JACKD with the -R switch and start producing music, *finally*.

Pretty straightforward, as things go in Linux. It took me *months*, however, to find out how to do this. I really hope Gutsy makes this simpler! I hope this HOWTO helps y'all, and I'd be most happy if more experienced users can comment here on pitfalls or anything else related to this approach. I know, for example, that Ubuntu Studio uses a different approach for realtime support, with an experimental kernel patch.

I know I could just install Ubuntu Studio, but I'm just not too happy with how the team packaged *everything* together. For example, Ubuntu Studio got Ardour 2.0 up and running, but I can't get it from their repositories without installing the whole shebang. I'm far happier with standard Ubuntu's fine-grained packaging, and I wish the Ubuntu Studio team would follow that. (Or at least allow both approaches.)

---

### Post by pirxthepilot on 2007-07-01
Hi there, great post!  This should prove useful to me.  One question: is the realtime-lsm patch the same as Ingo Molnar's realtime preempt patch?  If not, is one better than the other?

Thanks in advance!

---

### Post by Emblem Parade on 2007-07-01
Beats me. That was my dilemma. Hopefully someone who knows more about this can post here.

---

### Post by fredj on 2007-07-05
Of course you can just install the precompiled realtime kernel and Ubuntu studio then if there are any of the
installed programs you don't want to use just go to Apllications -> Add/Remove and untick the ones you don't
want. Comes to the same thing in the end.

---

### Post by gatohumano on 2007-12-02
> **pirxthepilot said:**
> Hi there, great post!  This should prove useful to me.  One question: is the realtime-lsm patch the same as Ingo Molnar's realtime preempt patch?  If not, is one better than the other?

Thanks in advance!

No,its diferent things,the realtime-lsm is to permit a non root user to use jackd i think.
i have a question,it is possible to install the realtime.lsm module in the source kernel before compiling?

---

