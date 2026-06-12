---
title: "Two tuners, one remote?"
date: 2009-04-27
forum: Mythbuntu
---

### Post by xfred on 2009-04-27
In the process of recent upgrading and subsequent downgrading I decided to install a second tv tuner card in my mythbuntu box.  Both tuner cards are winfast DTV2000H cards.  The problem is that 8.10 seems to choose at random which card will be used for detecting signals from the remote control, which is problematic as I only really have room for the one IR receiver shoehorned discreetly behind a convenient hole in the front of the case.

Is there any way to force mythbuntu to use just one or the other for this (esp. given that the cards are identical)?  Or will radical hardware surgery be required?

---

### Post by SiHa on 2009-04-27
If your LIRC devices are /dev/input/event*n*, you could try Garry Parker's tip [[COLOR="Blue"]here[/COLOR]](http://parker1.co.uk/mythtv_tips.php) - Make the LIRC Device Static'. It worked for my two Hauppauge cards, which used to switch randomly at each reboot.

---

### Post by xfred on 2009-04-28
Thanks - I've actually followed that advice before to make the event static (had to with one card way back to get the remote working at all as it was randomly swapping its event number).  But it still seems to assign randomly.

Both cards have the same vendor ID (tested by switching cards around and using udevinfo), so I'm guessing that whichever one the kernel sees last is the one that gets linked to irremote (irremote can't point to two devices at the same time), and I'm further guessing that this order is itself random.  Hence when I power up I have a 50/50 chance of irremote being pointed at the relevant event/card.

Actually... I just had a thought.  Does anyone know if any of these (quoting from the website linked above):
>     SYSFS{class}=="0x040000"
    SYSFS{device}=="0x8800"
    SYSFS{irq}=="209"
    SYSFS{local_cpus}=="1"
    SYSFS{modalias}=="pci:v000014F1d00008800sv00000070sd00009002bc04sc00i00"
    SYSFS{subsystem_device}=="0x9002"
    SYSFS{subsystem_vendor}=="0x0070"
    SYSFS{vendor}=="0x14f1"
is a function of which PCI socket I plugged my card into?  Because if it is I'm guessing that I could probably use that in my rules to assign the shortcut irremote to a specific card and my solve the problem.

---

### Post by SiHa on 2009-04-29
I'd be looking at the {modalias}line myself.

Can you do a```
cat /proc/bus/input/devices

```
then for the two events that you get list the udevinfo, and look for something that's different.

If the first stage only yields one event number, then maybe you need to try the brute-force method of doing the above for one card, then rebooting until it swaps and get the info for the second card?

I seem to remember having to do something similar because I have two (different) hauppauge cards so couldn't use the vendor ID.

---

### Post by xfred on 2009-07-04
Sorry for the long gap - other commitments.  Anyhow, I've just tried my approach but have run into a small snag.  Here's the (relevant) output of cat /proc/bus/input/devices for one session:

```
I: Bus=0001 Vendor=107d Product=6f2b Version=0001
N: Name="cx88 IR (WinFast DTV2000 H ver."
P: Phys=pci-0000:01:01.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010007 80000190 4801 1e0000 4400 100000 1000
0ffc

I: Bus=0001 Vendor=107d Product=6f2b Version=0001
N: Name="cx88 IR (WinFast DTV2000 H ver."
P: Phys=pci-0000:01:02.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:01:02.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010007 80000190 4801 1e0000 4400 100000 1000
0ffc
```

And here's the same thing after a reboot:
```
I: Bus=0001 Vendor=107d Product=6f2b Version=0001
N: Name="cx88 IR (WinFast DTV2000 H ver."
P: Phys=pci-0000:01:01.2/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:01:01.2/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010007 80000190 4801 1e0000 4400 100000 1000
0ffc

I: Bus=0001 Vendor=107d Product=6f2b Version=0001
N: Name="cx88 IR (WinFast DTV2000 H ver."
P: Phys=pci-0000:01:02.2/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:01:02.2/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010007 80000190 4801 1e0000 4400 100000 1000
0ffc
```

Note that the only difference is in the Phys line, but as that changes with each reboot I can't do the obvious thing and add it to my rules line.

Guess I'll have to look at the modalias idea you mention.  Will check back if I run into further problems.

---

### Post by SiHa on 2009-07-04
Just one thought - may be completely up the wrong tree.

Can you manually assign IRQ's in your BIOS setup? I have no idea why the physical slots seem to swap at boot, but it could be because of the auto-assigned IRQs?

If that doesn't work, you could try a serial receiver. I think you can pick them up on eBay or make one yourself. I'm using a homebrew receiver on both my machines, they're not hard to make as long as you can solder.

---

### Post by xfred on 2009-07-10
I thought about the BIOS idea, but decided against it as I already have to dive into the bios to turn on wake on PCI whenever the power goes down for more than an hour or so - any more setting and the spousal acceptance factor becomes a major concern.  So in the end I decided to give up on making the software work correctly and went with a simpler version of your hardware solution: I drilled two holes in discrete locations in the front of the case, cut off the plastic surrounds of the two IR modules so they'd fit snuggly behind these, and used some bits of black plastic to make it look professional.  Not an elegant solution maybe, but somehow satisfying in it's bluntness ;).

---

### Post by SiHa on 2009-07-10
I like your style...

---

