---
title: "Intel HD Graphics Driver"
date: 2011-08-29
forum: Multimedia Software
---

### Post by swindoro on 2011-08-29
Hi,

I am new to Linux and had just recently installed Ubuntu 11 on a system with Intel i5-2400 Sandy Bridge, which has an integrated HD Graphics feature.

Where can I get drivers for the integrated HD graphics? When I connect it to my HDTV, I have 2 problems:
1. The picture spills out of the screen and I cannot see the edges of the OS window. Intel supports Windows and has the capability of resizing the monitor scale.
2. The picture quality is poor, video playback is very grainy and washed up. Running it on Windows 7 looks good. 

Thanks.

---

### Post by realzippy on 2011-08-29
Drivers for Intel graphic cores are part of the kernel.
Which one do you use?

```
uname -a
```

---

### Post by swindoro on 2011-08-30
Hi,

Typing uname -a shows:

"... Ubuntu 2.6.8.38-8-generic #42...."

Image shows up on TV, it's just that it has bad resolution and wrong dimension. Is there a utility to manually resize the dimension at least?

Thanks.

---

### Post by realzippy on 2011-08-30
Maybe on the TV itself,means it's menu.
Search for a "overscan" or "autoscan" option...

---

### Post by swindoro on 2011-08-31
Hi,

Well, there is a size option for pre-set shrink but it's not quite what I'm looking for. Any other source, like DVR, DVD player or even my HTPC with Windows 7 on it can work fine. Windows 7 has the Intel HD Grapchic driver utility where I can select the appropriate resolution and manual horizontal and vertical scaling. I asked Intel if they have Linux support and they said no, it's up to the open community.

At this point, the graphic is pretty much useless. The GUI buttons are not in the visible area of the screen and movie playback runs at a horrendous quality.

Thanks.

---

### Post by BicyclerBoy on 2011-08-31
Support for Sandybridge is relatively new. If you used the xorg-edgers launchpad ppa you would be much closer.

Then the biggest boost to video decode/playback will come from VA-API.

I suspect that kernel 3.x.x is required to take full advantage of SB.

---

### Post by realzippy on 2011-08-31
@swindoro

Here 2.6.38 works on sandybridge,although I run 3.0.1-030001-generic....
Maybe you want to install it.

Can you show output from

```
xrandr -q
```

(with TV/LCD connected and running of course)

---

