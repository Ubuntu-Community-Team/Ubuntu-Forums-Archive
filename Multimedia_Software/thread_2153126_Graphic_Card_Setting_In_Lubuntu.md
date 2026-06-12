---
title: "Graphic Card Setting In Lubuntu"
date: 2013-06-10
forum: Multimedia Software
---

### Post by achilles316 on 2013-06-10
As the title says, where can i find the settings for the graphics in Lubuntu? I have been looking and i can't find anything. The reason i ask is because i want to see what the color, brightness, contrast and other settings are. 

I play 2 games on Facebook (Battle Pirates, Vega Conflict) and while both games look better ( glare of sun and other bright colors are toned down) in Lubuntu, they play better in Windows. This is especially the case since i updated my Bios ( which i didn't know i could do lol) and rolled back my graphic card software cause the newer software made it work worse.

Anyway, i hope someone can help me cause i would like to make the settings in Windows the same as the settings in Lubuntu. That way the colors are more toned down yet the game plays better. 

Thanks for any and all help. I really do appreciate it.

---

### Post by 3rdalbum on 2013-06-10
There is no link between colour intensity and performance, but we may be able to help on both counts (independently).

What graphics card do you have, and what driver are you using?

---

### Post by achilles316 on 2013-06-10
How do i go about checking that? I do know in windows it said that i have an intel graphics card. 

I know it might not change the performance but like i said, the game already plays better in Windows. The problem is that in Windows all the colors (or brightness or contrast) really pop. For example, in vega conflict there is a sun in the background in battles. In Lubuntu it doesn't bother me cause its toned down (like a dull paint is best as i can describe it) but in Windows, that same sun really glares (like glossy paint) and it makes it hard to see what is going on.

Yea i know my graphic card sux, i forgot to have it upgraded when i bought my pc. Will buy a new one soon as i can.

---

### Post by achilles316 on 2013-06-10
Nobody has any ideas on this? There has to be a way to see what the settings are right?

---

### Post by Bashing-om on 2013-06-10
achilles316; Hi !

In order to keep things rolling along:
provide the outputs of terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
apt-cache policy ubuntu-desktop ##if you are running ubuntu; else substitute
xdpyinfo | egrep 'dimensions|resolution'
uname -a

```

[INDENT]just try'n to help
[/INDENT]

---

### Post by Bucky Ball on 2013-06-10
*Thread moved to **Multimedia & Video**.*

Unsure why this was in the other forum. You will improve your chances of getting help by posting in the correct category.

---

### Post by achilles316 on 2013-06-10
> **Bashing-om said:**
> 
sudo lshw -C display
*-display:0 
description: VGA compatible controller
product: 4 Series Chipset Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 03
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:44 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:dc00(size=8)
*-display:1 UNCLAIMED
description: Display controller
product: 4 Series Chipset Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 03
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=0
resources: memory:fe900000-fe9fffff

> lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03)
    Subsystem: Dell Device [1028:0439]
    Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e23] (rev 03)


> apt-cache policy ubuntu-desktop ##if you are running ubuntu; else substitute
ubuntu-desktop:
  Installed: (none)
  Candidate: 1.299
  Version table:
     1.299 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages

> xdpyinfo | egrep 'dimensions|resolution'
 dimensions:    1024x768 pixels (270x203 millimeters)
  resolution:    96x96 dots per inch

> uname -a
Linux viper-Inspiron-560 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


I hope that was done right. 

Oh and it was in the other section cause i am a beginner at Linux.[INDENT]

[/INDENT]

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]achilles316...
And your desk top, as you are not running ubuntu (per "apt-cache policy"), is what ?
You are running intel for graphics... I have no experience with that chip set, so others will have to advice.
[INDENT=2]
just setting up the stage

[/INDENT]


[/COLOR]

---

### Post by achilles316 on 2013-06-11
> **Bashing-om said:**
> [COLOR=#000000]achilles316...
And your desk top, as you are not running ubuntu (per "apt-cache policy"), is what ?
You are running intel for graphics... I have no experience with that chip set, so others will have to advice.[INDENT=2]
just setting up the stage

[/INDENT]


[/COLOR]
Desktop Environment		: LXDE (Lubuntu)

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]achilles316; 

Try and play with this while awaiting those with greater experience.
applications menu ->settings ->appearance ->icons and fonts
See if resetting from the defaults have a desired affect.
[/COLOR][INDENT=2][COLOR=#000000]
best I can do for now

[/COLOR][/INDENT]

---

### Post by achilles316 on 2013-06-11
> **Bashing-om said:**
> [COLOR=#000000]achilles316; 

Try and play with this while awaiting those with greater experience.
applications menu ->settings ->appearance ->icons and fonts
See if resetting from the defaults have a desired affect.
[/COLOR][INDENT=2][COLOR=#000000]
best I can do for now

[/COLOR][/INDENT]

I have been having trouble loading applications in the file manager. Seems the wheel just keeps spinning. Been having alot of trouble with Lubunt, might just go back to windows.

---

### Post by achilles316 on 2013-06-11
> **Bashing-om said:**
> [COLOR=#000000]achilles316; 

Try and play with this while awaiting those with greater experience.
applications menu ->settings ->appearance ->icons and fonts
See if resetting from the defaults have a desired affect.
[/COLOR][INDENT=2][COLOR=#000000]
best I can do for now

[/COLOR][/INDENT]

Thanks for trying to help bud, i really do appreciate it. I think till i get a new graphics card that i will go back to Windows 7. 

I found a Gforce card with 1 gb at Dell.com for 39.99 so will buy it soon. It should be at least twice as good as this piece of junk i have right now lol.

---

