---
title: "tripple monitor ATI 4200 (onboard) + 6670 PCI"
date: 2013-04-02
forum: Multimedia Software
---

### Post by spinanicky on 2013-04-02
Hi everyone, 

So I have done a bit of research and I am not at a wall. I have two screens working (both plugged into the 6670 card) however can not get my onboard card to 'turn on'.
I know the bios is passing it through alright as the following is in [COLOR="#FF0000"]lspci[/COLOR]
```

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4290]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Turks [Radeon HD 6670]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks HDMI Audio [Radeon HD 6000 Series]

```

I thought that by adding the following it would work yet it doesn't :) 

```

Section "Device"
Identifier  "test"
Driver      "fglrx"
BusID       "PCI:1:05:0"
EndSection
```

Any help on getting the last card working would be greatly appreciated! 

Thanks!

---

### Post by ManamiVixen on 2013-04-02
Are you using the Proprietary ATI Driver?

---

### Post by QIII on 2013-04-02
What version ofUbuntu are you using?

Sometimes cards made by the same OEM will not play well together.  That could be the case in your situation.

---

### Post by spinanicky on 2013-04-02
I had the ATI driver installed.. I now uninstalled it and I can only mirror the two displays. 
Driver: VESA: TURKS
I am using ubuntu 12.04

Thanks for your quick responses guys!

---

### Post by ManamiVixen on 2013-04-02
The onboard 4200 **IS NOT SUPPORTED** by the Proprietary ATI driver, but the 6670 is. So you can use the driver with the 6670, but you will have to kiss the 4200 goodbye or use the open source driver and get weak performance on both chips.

---

### Post by spinanicky on 2013-04-02
Oh thats strange, I thought this was pretty much the same thing. 

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

---

### Post by ManamiVixen on 2013-04-02
So you have 13.1 installed through the Software Sources? Or from Nvidia?

I'm going to be quiet now. QIII knows alot more than me on ATI Drivers, but I was certain 12.04 couldn't run HD 4000 cards or older.

---

### Post by QIII on 2013-04-02
Through 12.04.1 the HD 4000 series cards are supported by the 12.4 driver in the Precise repo.  It is not supported in 12.04.2 and beyond.  The legacy driver may be used with pre HD 5000 GPUs, but it takes patching the kernel and downgrading X Server.

However, the fact that the two are such different models may be one problem.

Is this a desktop or a laptop?

---

### Post by spinanicky on 2013-04-02
I had the fglrx stuff installed. "additional drivers"

---

### Post by QIII on 2013-04-02
Is your version 12.04.2?

lspci may indicate the presence of the onboard GPU, but few mobos allow the use of both onboard and dedicated simultaneously.

---

### Post by spinanicky on 2013-04-02
I am not sure (back on windows right now). I know the installation CD is just 12.04 but I installed all the updates... not sure if that gets me up to 12.04.2

In windows I can use both grafic cards so its not a mobo thing. ;)

---

