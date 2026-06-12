---
title: "natty kernel panics after 30s"
date: 2011-04-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by schmolch on 2011-04-23
I just updated to natty and after a couple of seconds on the dektop or even when i remain in the console i get a kernel panic.

It happens always and at about the same time.

Hardware is a athlon-x2 with 2 nvidia cards.

---

### Post by schmolch on 2011-04-23
It does not freeze if i quickly stop gdm.
But it does still freeze when i start x with nv instead of nvidia.

---

### Post by KegHead on 2011-04-23
Hi!

Can you give a little more info?

What version, computer specs?

KegHead

---

### Post by dino99 on 2011-04-23
its time to do a clean instal or seriously clean this one: gconf-cleaner, bleachbit

of course if you have/had too much non trusted ppas then ....

---

### Post by schmolch on 2011-04-23
Its a athlon x2 5200 on a board with a nvidia chipset.
Nvidia onboard gpu plus pci-e nvidia, both series 7 iirc.
Since it is the kernel that panics i dont think gconf or anything else on the desktop-level could be responsible for that. So that leaves the kernel itself, xorg, and the nvidia drivers.

I would boot the old kernel if someone can tell me how i can make the grub menu visible.

I ran the current ubuntu until i did update-manager -d this morning.
In gdm i chose ubuntu classic failsafe which runs for 5 seconds and then freezes hard. If i switch to the console i can see the panic and when i quickly stop gdm it will not panic.

---

### Post by KegHead on 2011-04-23
Hi!

I tend to agree with a reinstall.

It might be a quicker solution.

KegHead

---

### Post by Quackers on 2011-04-23
Hold down the shift key during boot to see the grub menu.

---

### Post by cariboo on 2011-04-23
Could you paste the output of the following two commands in your next post:

```
lspci | grep VGA
```

and

```
sudo lshw -C display
```

I personally suspect a driver problem.

---

### Post by schmolch on 2011-04-23
Thx guys.

I booted the old kernel (2.6.35) and now everything runs fine.

---

### Post by schmolch on 2011-04-23
Here are the requested system-details.
I forgot that im not even using both nvidia-cards since i got rid of my third monitor. Im still using Xinerama though.

lspci | grep -i VGA
```

02:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)
```

sudo lshw -C display
```

PCI (sysfs)  


  *-display               
       description: VGA compatible controller
       product: G73 [GeForce 7600 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:df000000-dfffffff memory:c0000000-cfffffff memory:de000000-deffffff ioport:ec00(size=128) memory:ddfe0000-ddffffff


```

When the kernel paniced (<- spelling?) i could see something about pci.
I could make a photograph if its of any interest.

---

