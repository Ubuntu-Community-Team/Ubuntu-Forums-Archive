---
title: "Color fringing on Trinitron CRT/ Gutsy"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by dsmithhfx on 2008-02-12
Since installing gutsy I've had a weird color fringing issue on a ~5-yo 17" Trinitron CRT (NEC Multisync FE700+).

The effect is noticeable on the right-hand side of GUI elements, as an uneven red fringe,  vertical portions of black text characters appearing red or disappearing entirely -- the latter effects appear inconsistently, mainly in the desktop, start menus, and GUI elements, and hardly at all within application windows such as Kate, Firefox, Konqueror and Terminal.  Some menus are barely legible because of this issue.

It occurs at all resolutions and refresh rates,  including 1024x768,  in both KDE and Gnome. I am using the generic ATI driver that came with Gutsy, and not the proprietary (or any other drivers). It was noticeable 'out of the box', on the login screen when I first booted Gutsy from the live CD.

I tried messing around with the dpi in xrandr but this had no effect on improving (or worsening) the issue. I also tried different text anti-aliasing settings (including off), again, it made no difference.

This is only happening on the Trinitron (it doesn't occur on a 15" shadow mask CRT) in Gutsy -- it doesn't happen in OS X or Windows (2K, xp), and it didn't happen in Feisty. 

One difference is that in Feisty, I was using a Radeon 7000; with Gutsy I have a 9550 (and a whole new pc, for that matter).

---

### Post by dsmithhfx on 2008-02-22
OK, I guess it was a driver issue, because I installed the proprietary ATI catalyst 8.2 drivers (according to this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually) and the problem has gone away.

---

