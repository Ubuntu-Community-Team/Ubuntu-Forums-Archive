---
title: "Can't get TFT screen to work (&quot;Input Signal out of Range&quot;)"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by lodp on 2007-02-10
Setting up kubuntu 6.10 on my parents' desktop, I've got problems getting the monitor to work.

The desktop uses an old Matrox Mystique 220 card. The Monitor is a cheap flat-screen TFT (Gericom C700). When I use the "mga" driver, which supposedly supports Matrox cards of that type, the monitor turns blue and says "Input signal out of range". I read up a bit, looked up the HorizSync and VertRefresh values for the monitor (H: 24-80, V:56-75), and entered them in xorg.conf. I still get that error, however.

The only way I can get anything displayed is by using the "vesa" driver. However, display is very skippy when you scroll or move windows around. No way to get my parents to drop Windows with this in place :)

I would appreciate any pointers you can give me -- are there any drivers other than mga or vesa that I could try? Shall I try different HorizSync/VertRefresh Values (even though the ones I entered are from the monitor's documentation)?

---

### Post by lodp on 2007-02-11
Seems like this is due to a bug in xserver-xorg. A fixed package has been posted here: [https://launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/58721](https://launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/58721)

there will be a backport to Edgy some day (I hope soon ... this is quite serious for some people).

However, I'm still having problems with the display. Parts of windows disappear when I move them around or scroll down, take a look here: [http://img349.imageshack.us/img349/673/bildschirmphoto1az2.png](http://img349.imageshack.us/img349/673/bildschirmphoto1az2.png)

Could this be related to framebuffering somehow? Any pointers?

---

