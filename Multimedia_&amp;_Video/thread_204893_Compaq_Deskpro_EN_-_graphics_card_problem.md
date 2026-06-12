---
title: "Compaq Deskpro EN - graphics card problem?"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by pt78 on 2006-06-27
Hallo,
anybody having problems with Intel I815 integrated graphics card? I tired to test Dapper on Compaq Deskpro 667 (small form factor) (upgraded to 933) with my Belinea 102035W. I'm getting some strange stripes on my screen. Resolution is 1280x1024@60 (manually limited to 60). I tried different resolutions with the same result. I tried the same resolution in w2k and I do not experience such effects. I tried also SLAX (gives me 1600x1200@60) and again no problems - using same driver (i810). See enclosed file for detils. Any ideas?

EDIT: memtest was just fine.

Thx.

---

### Post by cavalier on 2006-08-08
I've got a similar machine, 733 MHz in speed, that's been nothing but trouble. I can't even get Ubuntu Dapper to get past the installation screen. I hit enter to start a standard desktop install and it locks up with a single horizontal stripe across the screen.

I'm going to try it with an old Hoary disk I have around. It might be better with a text-only install.

ETA: Not entirely good news, but potentially useful to you: I just got Fedora Core 5 to install without any trouble, but had the vertical lines that you're seeing. Changed the refresh rate from the default 60Hz to the much nicer 85Hz, and they went away.

---

### Post by MartinT on 2006-08-31
I had the same problem. HW: Compaq Destop EN, PIII/933. I solved it by editing /etc/X11/xorg.conf. In section "Screen" I wrote DefaultDepth 16 (was 24).

I found it by comparation of xorg.conf with Knoppix 5.0 DVD running. Then I red in "man 4 i810": DRI for i810 driver is working only for 16bit dept and it looks like it was the problem.

Try it

Martin

---

