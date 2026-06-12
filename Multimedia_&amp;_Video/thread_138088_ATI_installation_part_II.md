---
title: "ATI installation part II"
date: 2006-03-01
forum: Multimedia &amp; Video
---

### Post by cabber on 2006-03-01
Here is my set up:

Motherboard- Asus A8N-SLI socket 939
CPU- Athlon 64 X2 4400+
1 gig DRAM
Windows XP - 250G HD
Ubuntu - 37G HD
video card - Radeon X1800XT
Monitor - Dell 24 inch widescreen LCD

Here is my isssue:

When I initially installed Ubuntu everything was smooth until the loading process.  I received this error:

**XIO: Fatal IO Error 104 (connection reset by peer) on Xserver ":0.0" after 0 request (o known processed) with o events remaining.**

After reading through several post, I did this:
sudo dpkg-reconfigure xserver-xorg

set driver to 'vesa', and was able to boot into the OS.  From here, I went through this process:  
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

When I rebooted, I get the same error above, and have to switch back to the VESA driver to get into Ubuntu.

Would someone be so kind as to take me on as a Project?  I'll pay close attention and stay positive...I think:D

---

### Post by cabber on 2006-03-01
Well, I think I have thrown in the towel for now on Ubuntu.

By no means is this indented to trash anyone.  I have heard/seen tremendous success from several of you with it.  I do appreciate the knowledge. 

I guess I find it overly frustrating that I am using everyday computer hardware (Athlon 64, Radeon video card, SATA drives, LCD Monitors, etc.) and it takes an entire community to figure out how to make these function properly. And in the end,  I found the only answer for me was to use the VESA driver and look at a generic display of the OS.   

Thanks.

---

### Post by torx on 2006-03-03
^i can't help but agree with you. But still you have to understand that Ubuntu is a unstable distro, which means that everyone is suppose to JUST work. If you want a stable system with little bugs, you'll have to look elsewhere. For me, i'm still bugged down by ATI driver, but i don't game on my Ubuntu so it's less of an issue to me.

---

