---
title: "HD Video Issue - Intel Haswell-ULT graphics."
date: 2014-06-26
forum: Multimedia Software
---

### Post by Robert_Hubbard on 2014-06-26
Hi I am new to ubuntu but decided to give a go because I was tired of windows.  Its okay but im having some issues.  For one I cant watch anything streaming in hd.  Second the battery life is really bad if the screen is not on the dimmest setting.  I can hear the fan constantly going.  I have tried to add additional drivers from the software and updates section but it said there were no additional drivers.  I am almost ready to give it up on ubuntu which is a shame because I really enjoy the customization.  Any help would be greatly appreciated.

```

*-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:63 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

---

### Post by coffeecat on 2014-06-26
> **Robert_Hubbard said:**
> For one I cant watch anything streaming in hd.  Second the battery life is really bad if the screen is not on the dimmest setting.  I can hear the fan constantly going.  I have tried to add additional drivers from the software and updates section but it said there were no additional drivers.

I wouldn't be surprised if the HD streaming and poor battery life are related and are to do with the video driver. Let's see what you have. Sorry about asking for terminal output but this is the quickest and easiest way to get the information we need. Open a terminal and run this command:

```
sudo lshw -c video
```

You'll be prompted for your password. Don't worry if nothing appears to be happening as you type it in. It is going in, simply not being echoed to the screen. Copy and paste the output into your post between [noparse]```
 and 
```[/noparse] tags. You can highlight the output with your mouse, right-click -> copy.   

> **Robert_Hubbard said:**
>  I am almost ready to give it up on ubuntu which is a shame

Yes, that would be a shame, but I believe the problem is with your specific video card/driver combination and you would have a different experience with different hardware. I have no problem with HD streaming, fan or battery life with a couple of laptops. But let's see what your specific hardware is before making a judgement.

---

### Post by Robert_Hubbard on 2014-06-28
I updated my original post.  It does seem a little strange that it is saying vga.

---

### Post by coffeecat on 2014-06-28
You have an intel GPU and are using the default i915 driver. There is no other, which is why you weren't offered anything in Additional Drivers. The Intel chipset is "Haswell-ULT" which I have no experience of, but googling and searching these forums suggests that it is a problematic video device in Linux. Which is a great shame. Most Intel graphics devices just work in Ubuntu. 

I'll edit your thread title to include "Haswell-ULT". That might attract someone with experience of this who can give more constructive advice than I am able.

---

### Post by mc4man on 2014-06-28
could be that you are running on lvmpipe which is basically worthless

check this for 1st line ( OpenGL renderer string: ,  & last line ( Unity 3D supported: 
```
/usr/lib/nux/unity_support_test -p -f
```

---

### Post by Robert_Hubbard on 2014-06-28
When I entered:
```

/usr/lib/nux/unity_support_test -p -f

```

This was the output:
```

OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL version string:  3.0 Mesa 10.1.3


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes

```

---

### Post by mc4man on 2014-06-28
Well then your good as far as unity & intel driver support.
If I happen upon any report about performance with that particular Intel ggraphics will let you know.
As mentioned it's too bad, the 4200 I used to have & the 4600 I now have work perfectly.

---

