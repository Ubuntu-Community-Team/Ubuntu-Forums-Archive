---
title: "Where's kernel 2.6.35 rc4?"
date: 2010-07-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-07-03
Hi,
it's been like 3 weeks already since the last release while usually it only takes a week between releases. Anyone knows what's the matter?

---

### Post by renkinjutsu on 2010-07-03
If you look at [http://kernel.org]("http://kernel.org")
you'll see that rc4 hasn't even been released yet

---

### Post by kahumba on 2010-07-03
> **renkinjutsu said:**
> If you look at [http://kernel.org](http://kernel.org)
you'll see that rc4 hasn't even been released yet
That's what I mean - why hasn't it yet been released.

---

### Post by renkinjutsu on 2010-07-03
According to phoronix, there were some pretty severe regressions that made it all the way into the rc3 kernel. Maybe the kernel devs are just being more cautions this time around. Also, thought i read somewhere that Torvalds was on vacation or something?

think it was here > [http://lkml.org/lkml/2010/6/7/269]("http://lkml.org/lkml/2010/6/7/269")

---

### Post by kahumba on 2010-07-03
Yeah, but it seems he's been back since at least June 28th for I found his post on the main lkml page:
[http://lkml.org/lkml/2010/6/28/187]("http://lkml.org/lkml/2010/6/28/169")
among his other replies.

---

### Post by MacUntu on 2010-07-03
> **kahumba said:**
> Yeah, but it seems he's been back since at least June 28th for I found his post on the main lkml page:
[http://lkml.org/lkml/2010/6/28/187]("http://lkml.org/lkml/2010/6/28/169")
among his other replies.

Sorry, OT, but HAHA - Linus really should publish a book with some of his polite mail conversations. :D

---

### Post by Reiger on 2010-07-03
Well on the one hand it doesn't sound very nice, on the other hand he is completely right. Only fiction authors have a valid reason for passing negative timer offsets to a machine, and only as long as that happens in books; the rest are simply bugs.

Or read: [http://lkml.org/lkml/2010/6/28/187](http://lkml.org/lkml/2010/6/28/187)

---

### Post by MacUntu on 2010-07-03
No, no, I really like his straight way of saying things. Besides, I've read enough not so nice things from Mr. Drepper, so it's a fair fight I guess. :KS

---

### Post by kahumba on 2010-07-03
> **MacUntu said:**
> No, no, I really like his straight way of saying things. Besides, I've read enough not so nice things from Mr. Drepper, so it's a fair fight I guess. :KS
OT: Yes, I did read too, so I also agree, that guy is sometimes very rude (seems to have attitude problems) and wrong, afaik _he_ was one of the reasons why Debian moved to eglibc.

---

### Post by Starks on 2010-07-04
I love kernel drama.

---

### Post by TerminX on 2010-07-04
> **MacUntu said:**
> No, no, I really like his straight way of saying things.
Me too.  It's often less of an effort for both parties involved in an argument if someone is blunt about the reality of things when the opposing view is clearly wrong.

I'm not saying it's okay to act like a pompous *ss, just that it's less energy spent for all parties involved for someone to take 30 seconds and just get over it when their feelings/ego/pride are hurt, versus wasting a bunch of time coming up with nice ways to say things that take twice as long to get your point across.

---

### Post by moviemaniac on 2010-07-04
Well, dayly git-snapshots have resumed about a week ago. usually RCs are a week to 10 days apart so it's a safe bet we'll see rc4 in a few days. It might take longer this time around because of the buildup of requests during Linus' absence - but rc4 definitely is around the corner.

OT: I had started collecting Linus' "funnier" responses quite some time back - I guess I need to continue doing so :D

---

### Post by plun on 2010-07-05
RC4 is here......

Linus message, seems satisfied.
[http://lkml.org/lkml/2010/7/4/130](http://lkml.org/lkml/2010/7/4/130)

Ubuntu Mainline:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc4-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc4-maverick/)

No problem running this kernel with my laptop.

---

### Post by dino99 on 2010-07-07
hm im not so lucky: installed it on my desktop, it boot without problem but cant use mouse and keyboard at all when gdm popup.
i've played with acpi, apic, lapic, irqpoll, nomodeset on the boot line and desinstalled irqbalance too, but same problem.

nvidia from x-swat used

---

### Post by MacUntu on 2010-07-07
Will compile it with a custom config, cause I'm seeing the same with the Ubuntu mainline kernel: PC = keyboard not working, notebook = keyboard and touchpad not working.

Edit: custom config => -rc4 working. Hmmm...

---

### Post by MacUntu on 2010-07-07
> **dino99 said:**
> hm im not so lucky: installed it on my desktop, it boot without problem but cant use mouse and keyboard at all when gdm popup.
i've played with acpi, apic, lapic, irqpoll, nomodeset on the boot line and desinstalled irqbalance too, but same problem.

nvidia from x-swat used

Are they connected via PS/2? I attached a keyboard to the "dead" notebook via USB and it worked fine.

---

### Post by dino99 on 2010-07-07
> **MacUntu said:**
> Are they connected via PS/2? I attached a keyboard to the "dead" notebook via USB and it worked fine.

yes in fact ps2 + usb adapter

---

### Post by MacUntu on 2010-07-07
**Edit:**

The PPA's config has "CONFIG_X86_MRST=y" which turns off "CONFIG_SERIO_I8042", which is needed for standard AT keyboards and PS/2 mice - "CONFIG_X86_MRST" is now "n" in the Maverick kernel, so I guess we'll soon see this fixed in the PPA. :)

---

### Post by dino99 on 2010-07-07
mouse/keyboard freeze seems to be related to config/udev issues: BUS_I8042

[https://wiki.kubuntu.org/X/InputConfiguration](https://wiki.kubuntu.org/X/InputConfiguration)

---

### Post by dino99 on 2010-07-08
but the latest 999 work as expected with x-swat ppa (no freeze)

---

### Post by MacUntu on 2010-07-08
Yes, it's fixed in 201007071232 (was bad in 201007051223). :)

---

