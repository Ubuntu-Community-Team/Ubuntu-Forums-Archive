---
title: "ATI Driver, Video, Java and OpenGL Problem"
date: 2008-06-01
forum: Multimedia Software
---

### Post by furuno on 2008-06-01
Uhh, currently i'm having a hard time with my Hardy Heron. Before i've installed my ATI driver, it plays video and run openGL program (written with java and JOGL/JSR) well (altough in low FPS). But after installed it video play is flickered heavily unless it is played in fullscreen mode, which also not every time it works. OpenGL program also won't run (see the Java error below).

Some source says that i have to enable "TexturedVideo" in the xorg.conf "Device" section. Did that and now the video is won't even plays. Sometime the mplayer is crash... Or i did this the wrong way? What i did was add this line :
option "TexturedVideo" "on"

What should i do to overcome this problem? I don't know *that* much about linux...

Problem screenshots :
[[IMG]http://img520.imageshack.us/img520/6087/problem1zj8.th.jpg[/IMG]](http://img520.imageshack.us/my.php?image=problem1zj8.jpg)
Uhh, eye destroying...

[[IMG]http://img528.imageshack.us/img528/6224/problem3tv0.th.jpg[/IMG]](http://img528.imageshack.us/my.php?image=problem3tv0.jpg)
mplayer crashed...

[[IMG]http://img528.imageshack.us/img528/6103/problem4mk6.th.jpg[/IMG]](http://img528.imageshack.us/my.php?image=problem4mk6.jpg)
Java error...

[[IMG]http://img528.imageshack.us/img528/6703/problem2cs3.th.jpg[/IMG]](http://img528.imageshack.us/my.php?image=problem2cs3.jpg)
Informatics screenshots...

Information about my computer :
H/W : AMD Athlon X2 4000+, ECS AMD690GM-M2, 2GB DDR2 800, ATI Radeon HD 2400 Pro, LG L177WSB 17" Wide LCD (1440x900 @ 60Hz)
OS : Ubuntu 8.04 64-bit, Windows XP Pro SP2
xorg.conf : No change after sudo aticonfig --initial -f
Java : JRE 6 update 6
NO INTERNET CONNECTION :(
I have extra desktop effects enabled though...

Another question : 
1.) Why is the audio volume is not as loud as when i'm in Windows?
2.) What audio player that has good dsp effects?

Thanks before!

---

### Post by furuno on 2008-06-03
Sorry for bumping this thread... I really need a help...

---

### Post by Pjotr123 on 2008-06-03
Try this:
- disable visual effects (take some load off your video card)
- apply this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Does this help?

---

