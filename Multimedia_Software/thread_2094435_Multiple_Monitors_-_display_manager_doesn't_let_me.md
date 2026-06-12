---
title: "Multiple Monitors - display manager doesn't let me rearrange"
date: 2012-12-13
forum: Multimedia Software
---

### Post by ArlieS on 2012-12-13
I'm on Unity, trying to configure my collection of monitors. Until this afternoon, I could click on "systems settings", select displays, and click-drag to rearrange the monitors on the screen. This resulted in reasonable behaviour - the mouse could move across boundaries from one to another, and windows could be dragged between them. 

This afternoon I acquired a third monitor. In particular, I'm now on a laptop, with 2 large monitors attached to its docking station -  both rotated 90 degrees, and the laptop screen open. I was initially able to drag monitors around, but various weird things happened, including an all-screens-dark lock up that forced me to reboot. 

Now the only way I can get decent behaviour is to turn off the laptop screen. Even then, the two external monitors overlap in the "displays" screen, and cannot be moved.  

If I disconnect one of the monitors from the docking station physically, by removing the cable, behaviour changes, but things are still flaky. (If I recall correctly, I was able to move the laptop's screen vertically with respect to the external monitor, but not move it from one side to the other. And lots of windows completely disappeared - dragging them around within the "workspace switcher" helped me to regain access to most of them.) 

I'm on 12.04 LTS, desktop installation. (Possibly 12.04.01.) Update manager thinks I have everything up to date - but don't trust that too far, since it's lied to me on other Ubuntu desktop systems.

[Update: One more detail - when I attempt to drag the monitors, most of the time nothing happens. Sometimes they swap places, i.e. they are still overlapping,  but the one that's physically on the left shows the right side of whatever's on my desktop, and I have to move the mouse off the left edge of the leftmost screen to get it to appear on the right one.]

---

### Post by tgalati4 on 2012-12-13
Some graphics cards (or their drivers) are limited to a 2048x2048 "superdesktop".  So when you add a third monitor you exceed this dimension which forces you to shut down one display.

Look in /var/log/Xorg.0.log and ~/.xsession-errors for clues as to what is happening.

Paste the errors that you don't understand.

---

### Post by ArlieS on 2012-12-14
With the laptop screen configured as turned off, there was nothing interesting in either log file, though plenty I didn't understand.

Then I enabled the laptop screen. The result was a mess - but I eventually got the "do you want to keep this" pop up and said "no". This produced a farther mess, with various windows partly or completely off screen, no menu bar on the left side of the displays (it had been enabled), and a popup I can't move to complete visibility, which appears to be the usual popup claiming that some application crashed and asking me whether I want to send an error report. The name of the app. is partly covered, but begins with "Compiz".

I managed to save copies of these two log files while in this state. Possibly I'll have some evidence once I reboot - but this is looking like an error handling BUG, not just a configuration problem - and more serious than just a configuration screen not working  - so can anyone tell me where to report such a thing. Also, can anyone help me figure out where the problem is? IIRC, compiz isn't part of Unity, but part of a package used by Unity.... but for all I know, compiz is an innocent victim of an X deficiency, on one side, or of unity failing to hander error situations sanely.

---

### Post by ArlieS on 2012-12-14
> **ArlieS said:**
> With the laptop screen configured as turned off, there was nothing interesting in either log file, though plenty I didn't understand.

Then I enabled the laptop screen. The result was a mess - but I eventually got the "do you want to keep this" pop up and said "no". This produced a farther mess, with various windows partly or completely off screen, no menu bar on the left side of the displays (it had been enabled), and a popup I can't move to complete visibility, which appears to be the usual popup claiming that some application crashed and asking me whether I want to send an error report. The name of the app. is partly covered, but begins with "Compiz".

I managed to save copies of these two log files while in this state. Possibly I'll have some evidence once I reboot - but this is looking like an error handling BUG, not just a configuration problem - and more serious than just a configuration screen not working  - so can anyone tell me where to report such a thing. Also, can anyone help me figure out where the problem is? IIRC, compiz isn't part of Unity, but part of a package used by Unity.... but for all I know, compiz is an innocent victim of an X deficiency, on one side, or of unity failing to hander error situations sanely.

Now that I've rebooted, and done some research to determine what Ubuntu does with core dumps, I've got some more evidence. But I don't think that belongs here - this should be handled as a bug report against compiz, which received signal 7  (SIGBUS).

I have /var/crash/_usr_bin_compiz.1000.crash which probably has most of what matters for debugging, along with ~/.xsession-errors. 

For what it's worth, the behaviour of windows 7 is even worse - it blue screened, whereas Ubuntu only lost part of its window management system.

---

### Post by tgalati4 on 2012-12-14
Compiz runs 3D graphics with uses more video RAM, so you could be running out of video RAM to run all of those screens.  Try running 2D graphics to get a super desktop.

In a terminal: (and this may not work properly under Unity, so you have been warned.)

```
metacity --replace
```

---

### Post by ArlieS on 2012-12-15
> **tgalati4 said:**
> Some graphics cards (or their drivers) are limited to a 2048x2048 "superdesktop".  So when you add a third monitor you exceed this dimension which forces you to shut down one display.



One of my coworkers believes this is probably the issue. He's running one of the RPM family of distros (possibly scientific linux, possibly CentOS; I don't remember which) on a system given to him somewhat earlier by the same IT department, and simply doesn't use the laptop screen while docked.  On the other hand, laptop vendors change parts and keep the same basic model name, and he's had other graphics problems I've been spared - he has to attach one of his monitors as VGA rather than DVI, or accept serious graphics flakiness. 

At this point the system is working fairly reliably - on linux - and I may just leave things alone. Or I may get ambitious and dig farther, depending on how much time and energy I have.

---

### Post by tgalati4 on 2012-12-18
Also understand that graphics chips have a limitation that the resolution of both (or all three) displays must be a common, internal, clock multiple of each other.  So you might get 800x600 @ 60 Hz to work across all three, but 1920x1080@60 and 1400x1050@55Hz would probably not work at the same time.  This limitation is usually only discovered through trial and error.  Try a small, common resolution across all three at first then try upping the resolution in small increments.

DVI can support higher frequencies and resolutions over VGA.  So using VGA automatically forces you to lower clock speeds, which helps to drive mulitple monitors.

---

### Post by dannyboy79 on 2012-12-18
am I understanding that you have a dock for your laptop that has more then 1 video output? what graphics card and driver are you using? I didn't think there were any graphics cards that could run 3 displays within laptops.

---

### Post by ArlieS on 2012-12-18
> **dannyboy79 said:**
> am I understanding that you have a dock for your laptop that has more then 1 video output? 

Yes. The laptop is a Lenovo Thinkpad T430. 

> **dannyboy79 said:**
>  what graphics card and  driver are you using? 

Good question. I'm not entirely clear on how to determine this. Here are some possibly relevant excerpts from dmesg output. I don't see anything else that makes me think of video, but I'm no expert. 

[    0.726211] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem
,locks=none
[    0.726217] vgaarb: loaded
[    0.726218] vgaarb: bridge control possible 0000:00:02.0

[    0.745371] pci 0000:00:02.0: Boot video device

[   21.197949] fbcon: inteldrmfb (fb0) is primary device
[   21.198026] Console: switching to colour frame buffer device 200x56
[   21.198043] fb0: inteldrmfb frame buffer device

[   21.321574] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNX
VIDEO:00/input/input9
[   21.321619] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

---

### Post by dannyboy79 on 2012-12-18
lspci or lshw will both show you system/hardware/pci info.

---

### Post by tgalati4 on 2012-12-18
I have an older thinkpad t43p with a VGA port on both the laptop and on the dock.  The dock also has a DVI connector.  So, in theory, you could have 3 screens--laptop LCD, VGA, and DVI.  BUT--you are subject to several limits--superdesktop size (usually 2048 by 2048--this might be an xserver limit that could be compiled to be higher); you need a common/multiple-of video clock rate to drive all three displays; and your graphics chip needs to be able to drive all three ports through BIOS/firmware.  Some graphics cards will only support VGA or DVI, but not both.  

I have only done dual-screen, laptop and VGA or laptop and DVI, up to 1920x1080 on the 2nd display and the laptop's native 1400x1050.  I have not attempted to try 3 displays, but now you have my curiosity.

---

