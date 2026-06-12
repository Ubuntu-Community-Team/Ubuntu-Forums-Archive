---
title: "Problem with Restricted DEvices Manager"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by GoJa on 2007-11-17
On this page:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)
they have instructions to setup Nvidia cards.

Part of the instructions state

> How to setup nVidia drivers in 7.04

System > Administration > Restricted Devices Manager
Enable Driver
Apply Changes

and later:

> With the nVidia Driver enabled in the restricted devices manager, we can safely go into the console ..........

When I attempt to go into the restricted devices manager, after I put in my password, a dialog box pops up which tells me:

> Your hardware does not need any restricted drivers.

It only has a close button, when the dialog box closed nothing happens.

I've reinstalled the restricted driver manager package using Synaptic.

lspci shows that I do have a NVidia video card (which other posts ensure me requires a restricted driver).  Synaptic shows me restricted driver packages which I can download and install, but not enable.


Any idea what is going on? How do I enable the driver if I can't get into the restricted devices manager?  How do I get the restricted driver manager to work correctly.

---

### Post by ddrichardson on 2007-11-18
Which nVidia card do you have?

---

### Post by GoJa on 2007-11-18
I have a nVidia 8300 GS.  Brand new Dell system with Fiesty Fawn 7.04 (and I downloaded all the updates ).

> **ddrichardson said:**
> Which nVidia card do you have?

---

### Post by ddrichardson on 2007-11-18
According to [this]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html"), that card is supported in 100.14.11. Ubuntu 7.10 uses 100.14.19 so the card should be picked up. However a quick google shows you aren't the only one with this problem, there's a bug report [here]("https://bugs.launchpad.net/dell/+bug/121163"). There are linked patched debs for this card that you could try. I'd back up xorg.conf first though.

---

### Post by sergiom99 on 2007-12-28
How can I enable restricted drivers from text-mode console?
I cannot but to GUI on my laptop. I installed Kubuntu.

Thanks!

---

### Post by mali2297 on 2008-01-14
> **sergiom99 said:**
> How can I enable restricted drivers from text-mode console?
I cannot but to GUI on my laptop. I installed Kubuntu.

Thanks!

You can try with using the **vesa** driver to get a GUI, change driver with
```

sudo dpkg-reconfigure xserver-xorg

```
Then you might be able to use the restricted manager to get the driver that you really want.

An alternative is to use [envy]("http://albertomilone.com/nvidia_scripts1.html"), it is a script that can be run in text-mode.

---

### Post by sergiom99 on 2008-01-14
Thanks dude, I already managed to do that.
I first installed Envy, but when I downloaded some kernel updates it stopped working so I had to reinstall it. And then it stopped again when I had to recompile ALSA to get the laptop speakers working. 
So after a clean install of Kubuntu I did as you told and its been working since...
Thanks!

---

### Post by GoJa on 2008-01-19
I've read several threads which state that the restricted nVidia drivers need to be uninstalled and then reinstalled anytime a kernel change is made.  I believe the author of envy even has the note of his page telling you to uninstall/reinstall before any upgrade.  So I don't believe that your issues with having to do the reinstall are unique.

I've also found the restriced drivers (in dual monitor mode) to be a bit twitchy.  Once I get them working they are pretty solid as long as I don't make _any_ changes, otherwise weird and bizarre outcomes can be expected.  Even something as simple as changing resolution on one of the screens will cause the other one to 'lose' it.  Usually to the point of needing a reboot to recover.  Haven't figured that one out yet.  It's on my todo list.

---

### Post by sergiom99 on 2008-01-19
Hey,
It didn't happened to me with restricted drivers. i upgraded kernel after installing kubuntu, then reinstalled ALSA and such and never got to do nothing with video drivers (so far... fingers crossed!)

But i had to reinstall envy every time I changed ALSA or kernel until it finally stopped working so I decided to make a fresh install and figured out how to use restricted drivers.
Thanks for your help.

---

