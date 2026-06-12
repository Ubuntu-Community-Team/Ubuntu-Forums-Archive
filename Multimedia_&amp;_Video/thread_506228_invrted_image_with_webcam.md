---
title: "invrted image with webcam"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by olilo on 2007-07-21
Hi everybody,

I've just bought a Philips SPC200NC webcam.

It works well with one exception: the image is inverted (flipped upside down).

The only solution I found to correct this problem is hanging by the feet but it's not very easy to type on the keyboard

Here is the kernel modules I'm using

```

% lsmod | egrep -i 'video|spca'
gspca                 607824  0 - 
videodev               28160  2 ov511,gspca
v4l2_common            25216  1 videodev
v4l1_compat            15236  1 videodev
video                  16388  0 
usbcore               134280  4 ov511,gspca,uhci_hcd

```

Do you know what I can do to correct this problem ?

Tell me if you need additional informations.

Thank you.

PS: please excuse my bad english. I'm from ther french speaking part of  Belgium.

---

### Post by nggonline on 2007-10-01
same problem with me - ubuntu 7.04, camera Philips spc300n/20
Someone help!

---

