---
title: "nvidia-glx-legacy package description vague"
date: 2008-07-03
forum: Multimedia Software
---

### Post by Harry66 on 2008-07-03
[http://packages.ubuntu.com/hardy/nvidia-glx](http://packages.ubuntu.com/hardy/nvidia-glx),
[http://packages.ubuntu.com/hardy/nvidia-glx-new](http://packages.ubuntu.com/hardy/nvidia-glx-new),
 and
[http://packages.ubuntu.com/hardy/nvidia-glx-legacy](http://packages.ubuntu.com/hardy/nvidia-glx-legacy) 
are a bit vague about which should be used for which card. (Like what does _newer_ chipsets, _newer_ GeForce, _older_ GeForce mean, exactly?)

Does legacy mean all chipsets referred to here: 

[http://www.nvidia.com/page/legacy.html](http://www.nvidia.com/page/legacy.html)

?

(I'm having problems getting either driver working for my GeForce4 MX420, which I'm *guessing* from nvidia's site is a legacy card.)

Many thanks,

Harry

---

### Post by kostkon on 2008-07-03
> **Harry66 said:**
> [http://packages.ubuntu.com/hardy/nvidia-glx](http://packages.ubuntu.com/hardy/nvidia-glx),
[http://packages.ubuntu.com/hardy/nvidia-glx-new](http://packages.ubuntu.com/hardy/nvidia-glx-new),
 and
[http://packages.ubuntu.com/hardy/nvidia-glx-legacy](http://packages.ubuntu.com/hardy/nvidia-glx-legacy) 
are a bit vague about which should be used for which card. (Like what does _newer_ chipsets, _newer_ GeForce, _older_ GeForce mean, exactly?)

Does legacy mean all chipsets referred to here: 

[http://www.nvidia.com/page/legacy.html](http://www.nvidia.com/page/legacy.html)

?

(I'm having problems getting either driver working for my GeForce4 MX420, which I'm *guessing* from nvidia's site is a legacy card.)

Many thanks,

Harry
Indeed, the desciptions of these 3 packages (*nvidia-glx-legacy*, *nvidia-glx*, *nvidia-glx-new*) are a little vague.

You can find a full list [here]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html"). You can see the cards divided in three categories. The first for the *nvidia-glx-new*, the second for the *nvidia-glx* and the third for the *nvidia-glx-legacy* driver, obviously.

---

### Post by Harry66 on 2008-07-04
> **kostkon said:**
> Indeed, the desciptions of these 3 packages (*nvidia-glx-legacy*, *nvidia-glx*, *nvidia-glx-new*) are a little vague.

You can find a full list [here]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html"). You can see the cards divided in three categories. The first for the *nvidia-glx-new*, the second for the *nvidia-glx* and the third for the *nvidia-glx-legacy* driver, obviously.

Thanks for replying. My last ubuntu was Dapper, where the nvidia drivers just *worked *. Now I get a blank screen on bootup, and I get the impression the driver situation hasn't really settled down in Hardy - things seem really confused.

So if I understand correctly, my GeForce 4 MX 420 is described as legacy, but is supported by the nvidia-glx driver, the nvidia-glx-legacy driver being for reeeeally old cards, and nvidia-glx-new being for..... "newer" cards. 

(This would be good because I have tried completely uninstalling nvidia-glx and installing nvidia-glx-legacy (using synaptic, and I checked there were no hidden dot files in /lib/linux-restricted), but Hardware Manager only seems to know about nvidia-glx...)

However this thread ( [[COLOR="Blue"]NVIDIA GeForce 4 mx 420 > xorg.conf[/COLOR]]("http://ubuntuforums.org/showthread.php?t=815246") ) seems to indicate I should use nvidia-glx-legacy.

(I'm tempted to get a cheap PCI 5200 card (5 year old PC, no PCI-E ) like a [[COLOR="Blue"]Inno3d fx5200[/COLOR]]("http://www.inno3d.com/products/GRAPHIC_card/gf_fx/5200.htm") if it would help, but I have a fairly weak PSU, and I've found it hard to get a beefier one for the form-factor - so I would want a card that's light on power )

But if I could get it going with my existing card, that would be best - until I upgrade the whole PC)

Thanks for your help,

Rgds,
Harry.

---

### Post by nick_h on 2008-07-04
> So if I understand correctly, my GeForce 4 MX 420 is described as legacy, but is supported by the nvidia-glx driver, the nvidia-glx-legacy driver being for reeeeally old cards, and nvidia-glx-new being for..... "newer" cards.

Correct. You should use the nvidia-glx driver.

The link given by kostkon is a good reference.  You can check the id number using the following command:
```
lspci -nn
```

---

### Post by Harry66 on 2008-07-04
> **nick_h said:**
> Correct. You should use the nvidia-glx driver.

Cool. Now I just have to debug the config I suppose. conf and logs attached, if anyone would like to have a look, I'd appreciate it

> **nick_h said:**
> The link given by kostkon is a good reference.  You can check the id number using the following command:
```
lspci -nn
```

```
$ lspci -nn | grep -i nvid
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 MX 420] [10de:0172] (rev a3)
```

---

### Post by nick_h on 2008-07-04
Your xorg.conf looks OK and the log file you attached has no errors in it.

---

