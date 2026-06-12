---
title: "Do I need a video card?"
date: 2010-05-27
forum: Multimedia Software
---

### Post by ryharv on 2010-05-27
Hello all:

I consider myself moderately proficient with Ubuntu on the software side, but don't know much about hardware.  

What I do know is this: if I am trying to watch video on the computer, like on youtube or hulu's websites, or Hulu's desktop software, video running in a small window seems to play fine, but if I try to run it full screen the video is unacceptably choppy.

If you were me, would you diagnose this as an outdated video card?

Here is (I think) the relevant excerpt from lspci:

[INDENT]

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
	Subsystem: Dell Device 0181
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at e898 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
	Subsystem: Dell Device 0181
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

[/INDENT]

For reference, the rest of my system is a Dell Dimension 4700, 2.8 Ghz Pentium 4, 1.25 GB RAM.

My next question is -- if I am correct that I do need a video card to fix this problem, are there any that the Ubuntu community would recommend as relatively painless experiences to install and work well with Ubuntu?

I appreciate the help.  Thank you!

---

### Post by cascade9 on 2010-05-27
Choppy flash perfromance is probably just as much the lame flash version that linux gets as it could be the video card. Full screen flash has always been an issue with linux. 

That being said, its possibe that a video card will help flash work better.

If you do get a video card, then nVidia is probably easier at the moment. The later nVidia cards also have hardware video decoding, which could help. Probably your best bets are (all have VDPAU, nVidia hardware video decoding)-

8400GS- very cheap, works well. 
GT220- not quite as cheap, better VDPAU. If you watch a lot of video (non-flash, in particular HD content) its probably the better card to have.

*edit- link to the technical specifications for the 4700- 

[http://support.dell.com/support/edocs/systems/dim4700/sm/specs.htm#wp1043338](http://support.dell.com/support/edocs/systems/dim4700/sm/specs.htm#wp1043338)

---

