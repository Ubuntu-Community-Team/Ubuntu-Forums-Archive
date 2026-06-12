---
title: "Installed new sound card (Xonar DX), now the graphics fail..."
date: 2009-04-02
forum: Multimedia Software
---

### Post by PureW on 2009-04-02
Hello, I've just plugged my new Asus Xonar DX into the motherboard. And it plays wonderful music just as I had read it would in Ubuntu 8.10.

But I have two problems, one minor and one pretty major. Lets start with the major one:

Immediately after starting the computer after inserting the Xonar DX, I was informed that the graphics failed and I had the option to start in low-graphics mode, reconfigure the graphics and a third choice.

I'm writing this in low-graphics mode now. The first thing I checked was that the drivers for my Nvidia 6800LE graphics card were still installed. They weren't so I installed version 177 which was the recommended version. I restarted but there was no difference, I still had to boot in low-graphics mode.

*I wonder if this could be related to my motherboard which is a Asrock Dual-sata2 with both agp- and pci-express busses. My graphics card is using the agp-bus. It is just a hunch though. I ve read that Xonar DX should work immediately in Ubuntu 8.10.*

The soundcard works great, but it was an unpleasant side-effect that my graphics are no longer working. Which brings me into problem #2 which is only a minor problem. The volume manager is extremely sensitive, between 80% and 88% is the full scale, from very low sound volume to very high. And that's a bit problematic.

Logs:
[lspci -v]("http://bennehag.com/upload/upl/lspci.txt") Comment: *I think  PCI bridge: PLX Technology, corresponds to the Asus Xonar DX, since Asus just put a PCI-Express to PCI bridge onto the Xonar D1 chip.*

---

### Post by PureW on 2009-04-02
I solved it. The low-graphics thing anyway.

The problem was "(EE) No devices detected", and some googling lead me to the /etx/X11/xorg.conf file.

Apparantly the pci-adress of the graphics card was changed when I inserted the soundcard. So I switched addres from 4:00:0 to 5:00:0 which was the correct addres and after a restart it worked.

---

