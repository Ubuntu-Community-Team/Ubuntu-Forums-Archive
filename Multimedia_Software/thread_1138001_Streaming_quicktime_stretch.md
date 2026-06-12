---
title: "Streaming quicktime stretch"
date: 2009-04-26
forum: Multimedia Software
---

### Post by D-Dan on 2009-04-26
I found a solution to this problem pre Jaunty, which doesn't work now.

Streaming quicktime played through firefox is stretched, meaning that only a small part of the video actually shows. Using fglrx driver, the solution used to be VidoOverlay "off". However, this now causes a complete system hang as X starts loading, displaying a corrupted screen. I cannot switch to another terminal, and am forced to hard reboot.

The odd thing is, my 2nd PC also has ATI graphics (main PC is Radeon HD4670 and secondary PC is RX1950GT), which I did a distribution upgrade to Jaunty. At the start of the upgrade I received a warning of unsupported graphics, let the upgrade continue anyway, and everything works fine. However, the device driver in xorg.conf on PC2 is "ati" and not "fglrx". Embedded quicktime is fine on PC2.

Is there another fix to this video problem, or any more info on this mysterious "ati" driver?

Oh, the problem is the same whether I use the Totem plugin  or the vlc plugin. vlc's zoom options make no difference. Playing the video directly through vlc gives no problems, and full screen is fine. It's just embedded that's at fault.

TIA

---

