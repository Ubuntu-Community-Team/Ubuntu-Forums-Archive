---
title: "Forcing VGA from an ATI RV516 display controller"
date: 2008-09-29
forum: Multimedia Software
---

### Post by adriandown on 2008-09-29
Hello,

I'm trying to get a VGA signal from my VGA-compatible video card, but the video card is currently only outputting a DVI signal.  The following lines from running lspci at the terminal may be relevant:
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)
On the "Hardware Drivers" panel under the "System -> Admin" menu, I see only "ATI accelerated graphics driver", which is not checked as enabled but is listed as "in use."  I am using Ubuntu 8.04.  This graphics card seems strange in that there is no dedicated DVI or VGA output, but rather a single output that requires an adapter to connect to either DVI or VGA.  The adapters that I have are splitters that go from this weird output to either two VGA outputs or two DVI outputs (I have two different splitters, one for each output type).

Here's the whole story on this issue.  I previously spent an entire day trying to configure multiple monitors on this graphics card/OS.  Originally, the graphics card was outputting only a DVI signal, and nothing I did with drivers or configuration files had any success.  Eventually, in frustration, I tried plugging the a VGA cable from the second monitor into the built-in video card VGA output.  The computer totally freaked out and wouldn't boot all the way to the operating system.  Instead, I would get to a black screen with a fixed-width text message saying that I was trying to boot in an unsupported graphics configuration.  I was instructed to remove the offending cord from the VGA output and restart the computer.

After doing so, I found that the computer was outputting VGA from the universal output that used to be outputting DVI.  I eventually, with much much more frustration and effort than should be required, managed to hack the configuration files to get a workable dual monitor setup (although the resolution of one of the monitors wasn't quite right, I decided to leave well enough alone and live with it).

I recently moved the computer to a new location and have to change one of the monitors that was part of the original dual monitor configuration.  I found that after moving the computer, which involved unplugging the monitors, I am only able to get a DVI signal from the computer.  I have tried reproducing the same failure that caused the switch to VGA before (i.e. sticking a VGA cord in the built-in video card), but still I can only get a DVI signal from the box.  The problem with this is that one of the monitors that I now want to use in the dual monitor setup only has a VGA connection (previously, both monitors had both types of connections so either type of output would have been fine).

This problem is kind of convoluted, but hopefully I have explained enough to give a decent picture of what's going on.  Please let me know if there's any information I can provide that would be useful in diagnosing and/or fixing the problem here.  I've been a Mac user for a long time and just recently have had to start using a Dell box with Ubuntu at work, so I'm new to both Ubuntu and monitors that don't magically work correctly straight out of the box.

Any thoughts, advice, or further questions are appreciated.  Thanks very much,
Adrian

---

