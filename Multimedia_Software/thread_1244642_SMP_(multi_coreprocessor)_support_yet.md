---
title: "SMP (multi core/processor) support yet?"
date: 2009-08-19
forum: Multimedia Software
---

### Post by Ouoertheo on 2009-08-19
Hi,

I used to use ubuntu studio a lot until they dropped support for my multicore processor. I was just wondering, does 9.04 support multi core processors yet? I'd like to start using it again, but i need to be sure of that first.

TIA

---

### Post by mcduck on 2009-08-19
> **Ouoertheo said:**
> Hi,

I used to use ubuntu studio a lot until they dropped support for my multicore processor. I was just wondering, does 9.04 support multi core processors yet? I'd like to start using it again, but i need to be sure of that first.

TIA

What you mean that they dropped support for SMP? Sounds rather strange, SMP support has been included in Linux kernel years before there even was any multi-core CPU's available i consumer market.. :D

---

### Post by Ouoertheo on 2009-08-20
Yup, the SMP was dropped after... I think it was Hardy? But yeah, it's not worth installing if it still has no support for my amd64x2.

---

### Post by mcduck on 2009-08-20
> **Ouoertheo said:**
> Yup, the SMP was dropped after... I think it was Hardy? But yeah, it's not worth installing if it still has no support for my amd64x2.

Your processor sure is supported. What makes you think it isn't?

Ubuntu dosn't even have a kernel that wouldn't have SMP support..

---

### Post by Ouoertheo on 2009-08-20
Nope, I've been looking into this for a while but lost track recently. Try a google search on it, heres some links that include the info as well.

[http://www.ubuntu.com/getubuntu/releasenotes/810]("http://www.ubuntu.com/getubuntu/releasenotes/810")
[http://www.linuxjournal.com/content/ubuntu-810-charges-mountain]("http://www.linuxjournal.com/content/ubuntu-810-charges-mountain")

Both mention the lack of support after 8.04 (starting with 8.10).
I suppose I could just install and figure it out for myself, but it'd be nice to get the word from someone who knew. I'm really surprised that this  isnt as big an issue as it should be :p Dual processor support is a total must for these days.

As a note, when you type dmesg | grep "CPU" it says that it only recognizes one cpu, so the processor it's self is recognized, just not the second core.

mckduck, have you a dual core? does it work for you?

---

### Post by mcduck on 2009-08-20
Ah, so you mean that the *realtime kernel* didn't support SMP.. That makes a lot more sense. :)

All the normal kernels have supported SMP all the time, and as far as I know the current realtime kernel should support it as well. At least I can't find any mention anywhere that it wouldn't be supported. And since SMP support is default in Linux if it wasn't supported it definitely should be in the release notes of the current releases if there was any problems with it.

(and yes, I'm running multicore setup. But not with realtime kernel. But if you want, I'll install it and check if it works)

edit: I just installed the rt kernel and tested, all cores working fine. It must have been some issue specific to the 8.10's rt kernel.

---

### Post by Ouoertheo on 2009-08-20
Hooray! Thanks for checking that out for me, very much obliged :) Ill check back in here once I install it and see for myself.

---

### Post by Ouoertheo on 2009-08-24
Yep, the rt kernel worked like a charm with SMP support.

---

### Post by variona on 2009-09-09
@Ouoertheo: did your system 'Freeze'? Which CPU do you have?

As I encountered the 'Freeze' problem, I followed Studio Daves instructions ([http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904](http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904)). Quote:"Following suggestions found in my research I added these kernel boot options to the realtime kernel's entry in /boot/grub/menu.lst:

  nosmp acpi=off pnpbios=off
"
While dismissing smp support, while it hurts in a way to shut down one core, I got rid of the 'Freeze' problem and subjectively Studio seems to have better performance than it had under 8.04. (Talking about jackd, Ardour and Rosegarden)
Maybe load balancing between the cores caused more trouble than it did good?
I'm using an AMD64X2, CPU, nvidea, graphics, 1G RAM, RMEDigi96.

---

