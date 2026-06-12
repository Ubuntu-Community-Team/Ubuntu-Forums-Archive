---
title: "ATI --&gt; nVidia card swapout tips ?"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by dhuff on 2007-04-19
OK, had enough grief trying to get hardware 3D working with my ATI graphics card under 6.06 LTS, and have heard that nVidia-based cards seem to be more "Linux friendly."

I can get a 6200 chipset card pretty reasonably (still have an AGP slot, so my choices are somewhat limited). Once I physically swapout the cards, is it *just* a matter of starting up in a failsafe terminal mode and doing a ```
sudo dpkg-reconfigure xserver-xorg
``` or do I need to do something else as well to get basic, 2D XWindows working ? (I think I can figure out how to get 3D working afterwards)

Any hints for getting this to go smoothly ? Thanks :)

---

### Post by dhuff on 2007-04-25
In [another thread]("http://ubuntuforums.org/showthread.php?t=355699"), dpmcoy wrote:
> I swapped out my ATI Radeon 9550 last week for a new Nvidia Ge Force 7600.

It was a lot easier than I expected.

To be perfectly safe, I ran "dpkg-reconfigure xserver-xorg" and reset my video card type to "vesa". I turned it off, replaced the card, and rebooted. Once I did that, I installed the new Nvidia beta drivers through the instructions on one of the forum posts. I restarted the xserver, and everything has been working beautifully since.

---

