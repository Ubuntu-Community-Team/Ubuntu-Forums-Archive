---
title: "Ubuntu does not detect the external screen on my MacBook Pro?"
date: 2013-05-04
forum: Multimedia Software
---

### Post by bruninho on 2013-05-04
Hi all,

I posted this on askubuntu.com, but since I did not receive any answer I thought I might take a chance on this forum.

I just installed Ubuntu 13.04 on my MacBook Pro 13" Retina.  Everything  works fine except that Ubuntu does not detect my external  screen, which  is plugged through a DVI to VGA adapter. 
 On System Settings - Displays, only the laptop screen appears - no   sign of the external screen whatsoever even after clicking on Detect   Displays. Note that the external screen is always plugged in, including   during the boot process.

This MacBook comes with an Intel graphics card, as confirmed by a lspci | grep VGA:[INDENT]VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)[/INDENT]
 
sudo lshw -c video gives:[INDENT]   *-display    
   [/INDENT]
[INDENT=2]description: VGA compatible controller    
product: 3rd Gen Core  processor Graphics Controller 
   vendor: Intel Corporation    
physical  id: 2    
bus info: pci@0000:00:02.0 
   version: 09    
width: 64 bits     
clock: 33MHz    
capabilities: msi pm vga_controller bus_master cap_list  rom    
configuration: driver=i915 latency=0    
resources: irq:47  memory:a0000000-a03fffff memory:90000000-9fffffff ioport:2000(size=64)  
[/INDENT]

Any idea of how I could fix this??

  Thanks

---

### Post by gordintoronto on 2013-05-04
It's the DVI to VGA adapter.

---

### Post by bruninho on 2013-05-05
After a quick googling, I believe you! There are so many answers though, I find it hard to filter the relevant information. Do you think it is a problem between Ubuntu and the DVI output, or the DVI-VGA converter also brings specific problems?

---

### Post by bruninho on 2013-05-05
my bad, this is a thunderbolt port, not a dvi port.
After some research it seems that thunderbolt ports won't work on linux. Is that true?

---

### Post by gordintoronto on 2013-05-05
Others say that the Thunderbolt port works with recent versions.

The Apple site says: "VGA output using Mini DisplayPort to VGA Adapter."

---

### Post by bruninho on 2013-05-08
ok I bought an HDMI cable and that solved the problem

---

### Post by frapell on 2013-05-09
I have a macbook air, and after upgrading to 13.04, the display settings no longer detects external monitors (it was working perfectly fine with 12.10)

I'm using the VGA adapter, not an HDMI

Is there a bug reported somewhere for this issue? I couldn't find any...

I think this is something driver/kernel related issue, but just in case, I'm on Kubuntu (kde 4.10.2)

---

### Post by moustaki on 2013-05-17
Same issue here - had to revert to 3.5.0-27 for the time being, and it seems to do the trick.

---

### Post by fwendt on 2013-09-11
> **frapell said:**
> Is there a bug reported somewhere for this issue?

Yes, it's now recently reported here: please go check the "affects me too" if you're affected by this bug and want to see it fixed. I very rarely use VGA, but some clients are still stuck in the 20th century ;-)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1222734](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1222734)

---

### Post by q-tuane on 2013-10-24
I'm having the same problem on a Dell XPS14z. I followed the bug topic above and they say the external monitor returns to works with the not yet released kernel version 3.12 (currently RC6). I have just installed this 3.12 RC6 kernal on my machine and the mini display port (thunderbolt) to VGA adapter is reconized by xrandr as "eDP1 connected" but I have no signal on the external monitor. Adapter works fine on Windows though (same notebook). I can't imagine how to fix it anymore....

---

### Post by fwendt on 2013-10-25
> **q-tuane said:**
> I'm having the same problem on a Dell XPS14z. I followed the bug topic above and they say the external monitor returns to works with the not yet released kernel version 3.12 (currently RC6). I have just installed this 3.12 RC6 kernal on my machine and the mini display port (thunderbolt) to VGA adapter is reconized by xrandr as "eDP1 connected" but I have no signal on the external monitor. Adapter works fine on Windows though (same notebook). I can't imagine how to fix it anymore....

I'm running 3.11 and that works fine for me.

---

