---
title: "Unable to adjust screen brightness on Toshiba laptop with ATI card"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by cynicaloptimist on 2007-11-04
Hello,
I'm kind of a linux newbie, and I just received a new gateway laptop that came with Vista. So I immediately replaced it with Gutsy Gibbon. It's working, but I have this problem with the screen brightness. Neither the function keys nor the gnome power settings allow me to change the screen brightness. The software appears to 'think' it works, but the screen brightness does not change. I might go blind.

Please help!

---

### Post by quixotic-cynic on 2007-11-05
I have a similar issue with a Toshiba A120 laptop.

I fixed it temporarily by using the vesa driver instead of the ati one by editing /etc/X11/xorg.conf 

However, movies etc don't look as good, so I still have an issue - but that did stop me going blind.

I know feisty fawn didn't have the issue - so if you want to fix it and use ati drivers then downgrading would work (via a reinstall, if you can take it). I'm going to try Debian now instead, but it's probably not for everyone.

---

### Post by Danthe on 2008-05-14
Try this: ctrl+alt+F1 (this will take you to a virtual console.. Then use Fn+F6 to dim the screen brightness or Fn+F7 to brighten it up.  Then use ctrl+alt+F7 to return to your regular graphic user interface (they call it X).

My laptop is a Toshiba Satellite M105-S305, this worked just fine.

In hardy you can use the hotkeys on X, no need to get into the virtual console.

---

### Post by quixotic-cynic on 2008-05-15
Thank you for the reply Danthe.

The problem corrected itself on Hardy, but the hotkeys to adjust brightness are very useful to know for future use.

---

