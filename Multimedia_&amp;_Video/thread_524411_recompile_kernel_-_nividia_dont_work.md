---
title: "recompile kernel - nividia dont work"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by adam_r on 2007-08-13
after i recompile my kernel - the restricted modules and the nividia-glx dont work with the new one - i'm guessing there still installed on the old one. 

how do i get the restricted modules and the nivida-glx to reinstall on the new kernel? (2.6.22.2) ?

---

### Post by tseliot on 2007-08-13
Make sure you have paravirtualisation disabled in the new kernel (if not you'll have to recompile it).

You won't be able to use the restricted-modules with recompiled kernels but you can use either module-assistant or [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") (use it at your own risk).

However if paravirtualisation is on the installation of the driver will fail

---

### Post by adam_r on 2007-08-13
and if i just recompile the ubuntu linux-generic kernel? (2.6.20-16)
i still cant use restricted modules??

because envy will solve only the nividia.. but my wireless is there too... (i hate ndiswrapper)
i dont think it's worth giving up restricted modules just for the stupid "brightness up" button on my keyboard...

---

### Post by tseliot on 2007-08-13
> **adam_r said:**
> and if i just recompile the ubuntu linux-generic kernel? (2.6.20-16)
i still cant use restricted modules??

why are you recompiling your kernel?

---

### Post by adam_r on 2007-08-13
i got asus G1 laptop,

so all the acpi support i found (lapasus and acpi_asus modules) are supported only in 2.6.21 + 
also adding a new key list is only on 2.6.21 and above...

i thought i can wait for gusty... but if cant recompile gutsy as well it wont really help.. the problem is i dont want to give up restricted modules because accept ACPI everything else works great! and i know i will screw it up if i start messing around with envy modules-assistant ndiswarrper etc...

---

### Post by tseliot on 2007-08-13
> **adam_r said:**
> i thought i can wait for gusty... but if cant recompile gutsy as well it wont really help.. the problem is i dont want to give up restricted modules because accept ACPI everything else works great! and i know i will screw it up if i start messing around with envy modules-assistant ndiswarrper etc...
Gutsy will ship with kernel 2.6.22 therefore you won't have to recompile anything.

As regards Feisty, you will have to use either module-assistant or install the drivers from source with a recompiled kernel.

---

### Post by EndPerform on 2007-08-13
Envy is dead-easy to use and won't mess with anything.  If you do custom kernel recompiles, the restricted modules will not work since they are compiled against the compiled kernel in the repositories.  As soon as you compile your kernel, you cannot use the modules in the repository.  Unfortunately that's the way things go.  

So, your options are:

1) Use the precompiled modules and kernel; No ACPI fix.

2) Use your custom-compiled kernel, and learn how to install the Nvidia drivers and possibly wireless drivers.

The modules you use will work in Gutsy, as it is using a 2.6.22 kernel, but if the modules you found require you to recompile your kernel anyway, you're still going to be in the same boat.

---

### Post by adam_r on 2007-08-13
well, i'm going to backup the Hole damn partiton... and try to install the rest my self...

should i uninstall nividia-glx and restricted modules before i move to the new kernel and install envy + ieee ?
and where is the paravirtualisation in the config?

---

### Post by adam_r on 2007-08-13
i'm gonna do a fresh install of feisty on a diffrent partition and try out the kernel there, i'm too afraid to touch my system...

---

### Post by tseliot on 2007-08-13
> **adam_r said:**
> should i uninstall nividia-glx and restricted modules before i move to the new kernel and install envy + ieee ?
No

> **adam_r said:**
> and where is the paravirtualisation in the config?
If you're using the recompiled kernel just type:
```
cat /boot/config-`uname -r` | grep PARAVIRT

```

---

