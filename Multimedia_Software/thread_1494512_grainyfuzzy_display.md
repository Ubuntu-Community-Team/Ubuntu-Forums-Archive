---
title: "grainy/fuzzy display?"
date: 2010-05-27
forum: Multimedia Software
---

### Post by owners4life5 on 2010-05-27
ok so i have lucid lynx installed on my emachines desktop. the problem is that the display is edgy/scratchy/grainy/et cedra.... i am pretty much new to ubuntu and was wondering if anyone could help me and/or provide a step-by-step guide on how to fix this. i'll provide any component or hardware details if needed...

thanks
:popcorn:

---

### Post by owners4life5 on 2010-05-27
ok so i have lucid lynx installed on my emachines desktop. the problem is that the display is edgy/scratchy/grainy/et cedra.... i am pretty much new to ubuntu and was wondering if anyone could help me and/or provide a step-by-step guide on how to fix this. i'll provide any component or hardware details if needed...

thanks
:popcorn:

---

### Post by owners4life5 on 2010-05-27
ok so i have lucid lynx installed on my emachines desktop. the problem is that the display is edgy/scratchy/grainy/et cedra.... i am pretty much new to ubuntu and was wondering if anyone could help me and/or provide a step-by-step guide on how to fix this. i'll provide any component or hardware details if needed...

thanks
:popcorn:

---

### Post by fredbird67 on 2010-05-27
My gut instinct here is that this sounds like a hardware problem.  Do you also have Windows installed, and if so, does it look OK?

---

### Post by Defrector on 2010-05-27
Would you describe the display as being extremely sharp, like you can plainly see the squares making up the image? Would you describe the image on Windows to be relatively blurry? Or is it vice versa?

---

### Post by owners4life5 on 2010-05-27
well i DID have xp installed, and just completely installed ubuntu. but the hardware isn't the case, because xp displayed perfectly fine. and no, i don't literally see the squares, just when i open menus, or swap windows, it kind of 'glitches' and gets grainy

---

### Post by owners4life5 on 2010-05-28
Hello,

I have a eMachines Desktop with SiS for my display driver.
in a nutshell, it is horrible. what should i do? i can't enable compiz, do special effects, or even watch a movie. it's very upsetting, and i have no clue how to update it, or anything. their website is horrible, and i can't find anything. any help is greatly appreciated.

thanks

---

### Post by owners4life5 on 2010-05-28
Hello,

I have a eMachines Desktop with SiS for my display driver.
in a nutshell, it is horrible. what should i do? i can't enable compiz, do special effects, or even watch a movie. it's very upsetting, and i have no clue how to update it, or anything. their website is horrible, and i can't find anything. any help is greatly appreciated.

thanks
:popcorn:

---

### Post by overdrank on 2010-05-28
Hi and please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by owners4life5 on 2010-05-28
great... now i look reaallly intelligent :)

help on ANY of these subjects would still be appreciated.... so thanks i guess

---

### Post by spelingchampeon on 2010-05-28
Well, lets seeeeee.

You have an eMachines desktop, but you dont say what model, or motherboard, or anything to give us something to go on. 

Check this link out: [http://ubuntuforums.org/showthread.php?t=799070]("http://ubuntuforums.org/showthread.php?t=799070")

It has a link to check your video card to see if the problem lies there, or elsewhere. 

If your motherboard supports an AGP card, you could always buy a new or used video card and install it. There are many posts about many different machines, so you could look to see what everyone is using (that works) and see if that doesnt get you to where you want to be video-wise. 

The more memory your video card supports, the less taxing on your cpu...

---

### Post by owners4life5 on 2010-05-28
well, i followed the link and ran compiz-check and this is what i get in the terminal

```
brian@brian-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)
 Driver in use:         sis
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use

```

so yep. i am not exactly sure what to do.

and like i said earlier:
>  i'll provide any component or hardware details if needed...

i'll give you specs. i didn't know if anyone needed any or not. so here:

off-the-top-of-my-head info:
eMachines 2686
AMD 64 Athlon X2 processor

and from lspci in terminal:
```
brian@brian-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Ethernet Adapter
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 IDE interface: Silicon Integrated Systems [SiS] Device 0183 (rev 01)
00:0a.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

```

thanks again for trying to help. hopefully someone can help me solve this "problem"

---

### Post by owners4life5 on 2010-05-29
*bump*

im going to be without internet access so if i dont reply within a week, im not ignoring you

---

### Post by owners4life5 on 2010-07-20
well, i swapped to the vesa driver and this solved the problem... so thanks.. i guess

---

