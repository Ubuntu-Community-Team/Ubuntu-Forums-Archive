---
title: "Laptop Lirc over IrDA"
date: 2008-05-10
forum: Mythbuntu
---

### Post by theidealist on 2008-05-10
Hello all,

Let me first begin by saying that MythBuntu is totally, compleletly and in all other ways inconceivably awesome.  Thanks to everyone who made and makes it possible.  This is the first post/help request I've had to make because any other problem I've had enough luck to find answered elsewhere.

My problem is with the lirc module.  I'm trying to use the remote to an old no-name DVD player.  I'm pretty sure the remote is at least transmitting because when I look at the transmitter diode through my digital camera's live preview, I can see it flashing.

The laptop I'm using is an old (circa 2003) Toshiba P1955-S803.  It has irda infrared onboard, and I read [here]("http://www.thinkwiki.org/wiki/How_to_make_use_of_IrDA#LIRC_and_IrDA") that it is possible to make lirc work in such a setup.  I read a few other places that CIR (Consumer InfraRed) over IrDa is not possible.  Does anyone have definitive, up-to-date information on whether this is possible?  Just as good would be anyone chiming in that they do use it, or could never get it work.

So, that's my real question, and now I'll lay out what I've done thus far to try and make it work, and if anyone can offer advise on where to go/what to try next, I'd appreciate it.  I think I'm on the right track, but I don't know what else to try.

When the laptop boots, I can do this:
```
root@mythtv:~# lsmod | grep ir
smsc_ircc2             24096  0
irda                  203068  1 smsc_ircc2
crc_ccitt               3072  1 irda

```
My understanding is that this means irda is up and running.  I don't care about irda in the least so I can remove all of these modules with [FONT="Courier New"]modeprobe -r smsc_ircc2[/FONT].  This works as expected and running the above lsmod command again produces no results anymore.  I also noticed that irattach is running and killed it as well.  Not sure if that's a good idea, but I kind of want to get rid of everything irda so that nothing is getting in the way of lirc.

I then run
```
root@mythtv:~# modprobe lirc_sir
root@mythtv:~# dmesg | tail
[  152.925576] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 2076.016778] smsc_ircc_close(), releasing 0x6f8
[ 2076.016789] smsc_ircc_close(), releasing 0x2f8
[ 2076.123279] NET: Unregistered protocol family 23
[ 2108.426729] irda_init()
[ 2108.426766] NET: Registered protocol family 23
[ 2251.723796] lirc_dev: IR Remote Control driver registered, at major 61
[ 2251.729513] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 2251.729571] lirc_sir: I/O port 0x03e8, IRQ 4.
[ 2251.729586] lirc_sir: Installed.

```
My understanding here is that lirc found something and did something and appears to be happy.  Two new devices now exist in /dev - lirc0 and lircd.

Now I run
```
root@mythtv:~# mode2 -d /dev/lirc0

```
and push buttons on my remove, but nothing happens :( I was hoping to see something, ANYTHING when I pressed them, just to let me know it was picking something up, but it never does.  Eventually I ctrl+c to get out of it.

Can anyone offer me any suggestions?

Thanks,

-Patrick

---

### Post by theidealist on 2008-05-11
.... bump .... anyone got any ideas on this?  Better place to post it even?

---

### Post by theidealist on 2008-05-13
.... bump .... anyone got any ideas on this? Better place to post it even?

---

### Post by theidealist on 2008-05-14
.... bump .... anyone got any ideas on this? Better place to post it even?

---

### Post by superm1 on 2008-05-14
> **theidealist said:**
> Hello all,

Let me first begin by saying that MythBuntu is totally, compleletly and in all other ways inconceivably awesome.  Thanks to everyone who made and makes it possible.  This is the first post/help request I've had to make because any other problem I've had enough luck to find answered elsewhere.

My problem is with the lirc module.  I'm trying to use the remote to an old no-name DVD player.  I'm pretty sure the remote is at least transmitting because when I look at the transmitter diode through my digital camera's live preview, I can see it flashing.

The laptop I'm using is an old (circa 2003) Toshiba P1955-S803.  It has irda infrared onboard, and I read [here]("http://www.thinkwiki.org/wiki/How_to_make_use_of_IrDA#LIRC_and_IrDA") that it is possible to make lirc work in such a setup.  I read a few other places that CIR (Consumer InfraRed) over IrDa is not possible.  Does anyone have definitive, up-to-date information on whether this is possible?  Just as good would be anyone chiming in that they do use it, or could never get it work.

So, that's my real question, and now I'll lay out what I've done thus far to try and make it work, and if anyone can offer advise on where to go/what to try next, I'd appreciate it.  I think I'm on the right track, but I don't know what else to try.

When the laptop boots, I can do this:
```
root@mythtv:~# lsmod | grep ir
smsc_ircc2             24096  0
irda                  203068  1 smsc_ircc2
crc_ccitt               3072  1 irda

```My understanding is that this means irda is up and running.  I don't care about irda in the least so I can remove all of these modules with [FONT=Courier New]modeprobe -r smsc_ircc2[/FONT].  This works as expected and running the above lsmod command again produces no results anymore.  I also noticed that irattach is running and killed it as well.  Not sure if that's a good idea, but I kind of want to get rid of everything irda so that nothing is getting in the way of lirc.

I then run
```
root@mythtv:~# modprobe lirc_sir
root@mythtv:~# dmesg | tail
[  152.925576] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 2076.016778] smsc_ircc_close(), releasing 0x6f8
[ 2076.016789] smsc_ircc_close(), releasing 0x2f8
[ 2076.123279] NET: Unregistered protocol family 23
[ 2108.426729] irda_init()
[ 2108.426766] NET: Registered protocol family 23
[ 2251.723796] lirc_dev: IR Remote Control driver registered, at major 61
[ 2251.729513] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 2251.729571] lirc_sir: I/O port 0x03e8, IRQ 4.
[ 2251.729586] lirc_sir: Installed.

```My understanding here is that lirc found something and did something and appears to be happy.  Two new devices now exist in /dev - lirc0 and lircd.

Now I run
```
root@mythtv:~# mode2 -d /dev/lirc0

```and push buttons on my remove, but nothing happens :( I was hoping to see something, ANYTHING when I pressed them, just to let me know it was picking something up, but it never does.  Eventually I ctrl+c to get out of it.

Can anyone offer me any suggestions?

Thanks,

-Patrick
You will want to make sure that it is attaching to the correct serial port (io/irq)

```
$modinfo lirc_sir
filename:       /lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_sir/lirc_sir.ko
license:        GPL
author:         Milan Pikula
description:    Infrared receiver driver for SIR type serial ports
srcversion:     0056FFB0556C56BF791CDEF
depends:        lirc_dev
vermagic:       2.6.24-16-generic SMP mod_unload 586 
parm:           io:I/O address base (0x3f8 or 0x2f8) (int)
parm:           irq:Interrupt (4 or 3) (int)
parm:           threshold:space detection threshold (3) (int)
parm:           debug:Enable debugging messages (bool)
```
You'll see that they are both possible parameters when loading lirc_sir.  Also, you may need to use setserial to turn on or off these ports from kernel usage.

---

### Post by superm1 on 2008-05-14
Probably should clarify; most IRDA receivers show up like a serial device to the kernel, that's why you may need to fsck around with these

---

### Post by trriss on 2008-05-15
also, i'd like to point out that it is not always possible to use an irda device as a sensor for a remote... sometimes it works, sometimes it doesn't.... I tried it once and never got it to work, and even if it works the range may be very bad, or it might work only at certain angles, or ...


good luck getting it to work anyway!

---

### Post by wild_oscar on 2008-06-13
I have the same issue.

Haven't been able to make mode2 detect anything on my Targa laptop's built in receiver...

---

