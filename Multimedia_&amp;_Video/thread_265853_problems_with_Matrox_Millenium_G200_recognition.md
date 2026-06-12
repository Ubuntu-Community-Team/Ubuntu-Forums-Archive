---
title: "problems with Matrox Millenium G200 recognition"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by stan123 on 2006-09-26
Hello,
I Just installed Ubuntu 6.06, everything is fine but my display card:
I have an old Matrox Millenium G200 AGP card but I can only see the desktop at 640x480 resolution. Obviously it does not recognize the card.

Both in the device manager it appears to have the correct driver for the card, and the xserver-xorg autodetect it immediately. However, somthing is still missing as I cannot see normal resolutions and normal colors.

Thanks for your answer,
Josh.

---

### Post by pseudonym on 2006-09-26
Have a look at section 5 of the problems section [here]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper#head-b5fef156d1e6aba56287648d7adf3902f6b83ca9")
It's nvidia but your problem sounds like it's with your x server settings.

Just to make sure, you should also verify that you are using the 'mga'driver for that video card.

---

