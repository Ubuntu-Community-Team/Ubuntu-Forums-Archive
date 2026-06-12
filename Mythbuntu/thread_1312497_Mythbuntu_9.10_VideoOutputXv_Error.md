---
title: "Mythbuntu 9.10 VideoOutputXv Error"
date: 2009-11-03
forum: Mythbuntu
---

### Post by garry.thorpe on 2009-11-03
Hi,

I installed mythbuntu 9.10 on my faithful Mythbuntu 8.04 running on a Dell Dimension 1100 after a disk crash.  Now I have a video problem; display is jerky.  Worked fine under 8.04.  Details below, any help much much appreciated.  (Had brilliant WAF, but loosing ground.  Thanks.  :- )

Video card info:
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "82865G Integrated Graphics Controller"
        BusID       "PCI:0:2:0"

mythfrontend.log:
2009-11-02 12:34:13.061 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-11-02 12:34:13.061 VideoOutputXv: Falling back to X11 video output over a network socket.
                              *** May be very slow ***
2009-11-02 12:34:13.061 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xa22eef8) visual(0xa22a5c0)
                        depth(24) WxH(1360x768) bpl(4080)
2009-11-02 12:34:13.064 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-11-02 12:34:13.064 VideoOutputXv: Falling back to X shared memory video output.
                              *** May be slow ***

I have googled, and searched, not sure what to do next.  Any pointers appreciated.
Garry

---

### Post by UponFirstListen on 2010-01-31
Old topic, I know, but did you ever find a resolution? I'm getting the same errors: falling back to X11 video output and then falling back to X shared memory video output.

---

