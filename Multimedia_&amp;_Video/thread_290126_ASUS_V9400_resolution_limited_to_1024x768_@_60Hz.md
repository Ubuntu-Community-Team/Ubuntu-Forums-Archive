---
title: "ASUS V9400 resolution limited to 1024x768 @ 60Hz"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by xp_newbie on 2006-10-31
Device Manager identifies the ASUS V9400 video card also as NV18 [GeForce4 MX 4000 AGP 8X].

/etc/X11/xorg.conf identifies my monitor as "Generic Monitor" and thus provides resolutions of up to 1024x768 only.

But my monitor is a DELL 1100 Trinitron which is capable of at least 1600x1200.

How do I enable the higher resolutions? (with Windows 2000 I get 1600x1200 on this system without any hassle).

Thanks!
Alex

---

### Post by TigerCR1200 on 2006-10-31
In your xorg.conf file you should be able to add the modes under the Section "Screen" section.

I have this problem when I first install. I generally do a "sudo dpkg-reconfigure -phigh xserver-xorg" right off the bat before installing drivers and it usually grabs the correct modes for my monitor.

---

### Post by xp_newbie on 2006-10-31
Thanks, I just did "sudo dpkg-reconfigure xserver-xorg", pressed ENTER whenever I didn't know the answer to a question - and pressed CTRL+ALT+Backspace to log out.

That gave me the desired resolution (1600x1200), but now it has constant noisy lines on the right side of the display (which worsens if I move any window).

This noise does not exist when I run at the same resolution on Windows 2000.

Any idea how to fix this problem?

Thanks,
Alex

---

