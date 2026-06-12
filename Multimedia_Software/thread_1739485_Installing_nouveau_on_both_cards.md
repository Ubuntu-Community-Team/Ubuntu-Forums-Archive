---
title: "Installing nouveau on both cards?"
date: 2011-04-26
forum: Multimedia Software
---

### Post by Kareeser on 2011-04-26
Hi all,

My laptop is a Dell XPS 1340, it contains an integrated 9400M, and a discrete G210m. In trying to get vgaswitcheroo working with these cards, it seemed that every time I tried to switch outputs, my computer would freeze.

```

cd /sys/kernel/debug/vgaswitcheroo
sudo chmod 777 switch
echo DIS > switch    # Same with DDIS, same with OFF

```

It seems like what would happen if vgaswitcheroo turned off the driver (nouveau) powering the card on PCI bus 3 (the 9400M), and attempted to turn on the driver powering the G210m, which doesn't exist.. I think? Can somebody confirm?

Here is an lshw output:
```

julian@haydn:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GT218 [GeForce G210M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:ae000000-aeffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:4000(size=128) memory:af000000-af07ffff
  *-display
       description: VGA compatible controller
       product: C79 [GeForce 9400M G]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: b1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:18 memory:ac000000-acffffff memory:b0000000-bfffffff memory:ca000000-cbffffff ioport:5000(size=128) memory:c0000000-c001ffff

```

I'm led to believe the **UNCLAIMED** in the G210m section means that nouveau doesn't want to talk to it... which is annoying me. Is there some special way to get nouveau to work with the second card?

---

### Post by AikenDrum on 2011-05-06
Hi, 

I've been trying to work out the same thing with my XPS - identical to yours.  I can successfully turn on or off the G210 card with the acpi_call/test_off.sh  scripts which you've probably seen.  All that really does is let you cut the power consumption / heat generation down - you're still stuck using the 9400M card.

I started down the same path you are on,  but am having issues getting the nouveau driver to work *at all* (the Xorg.0.log for the session shows nouveau listing the devices it will work with - but it just fails to find any)  - possibly because I'm well due a clean install and something I've done/installed over the last 2 years / upgrades / updates is b0rking the driver.  Strangely the old nv driver works fine - as does the restricted nvidia driver with the BUSID specified in your xorg.conf

Anyway - sorry I couldn't contribute anything useful for you - but you're not alone :)  Once I get the nouveau driver working again I can help the switcheroo / nouveau projects with some testing / info I guess.

Cheers,

---

