---
title: "Can't use virtual resolution."
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by zuencap on 2007-12-08
Hi,
I'm resending this post since I didn't get any response from desktop environment forum. Maybe it was wrong place for this subject.
I like virtual resolution, I like to work on a large desktop even if I can't see all of it.
For many year I configured my linux desktop with virtual resolution happily (on fedora and ubuntu feisty). When I upgrade my feisty installation to gutsy, gdm starts to refuse using virtual resolution but switches to maximum real resolution. And after login gnome uses that resolution. I can switch to wirtual resolution by:
xrandr -s 1600x1200
I have added this command to "Startup Programs". It sometimes works, sometimes not. When it doesn't, I had to log out and re-log in until it works. It's irritating.
There is no problem with kdm so I don't think that my xorg.conf file is wrong.

---

### Post by bingoUV on 2007-12-08
run your command(xrandr) from terminal command line, and see if it gives any error.

---

### Post by zuencap on 2007-12-11
Here is the output:

erdem@parvi-laptop:~$ xrandr --verbose -s 1600x1200
 SZ:    Pixels          Physical       Refresh
*0   1280 x 800    ( 330mm x 210mm )  *60
 1   1280 x 768    ( 330mm x 210mm )   60
 2   1024 x 768    ( 330mm x 210mm )   60
 3    848 x 480    ( 330mm x 210mm )   60
 4    800 x 600    ( 330mm x 210mm )   60
 5    720 x 576    ( 330mm x 210mm )   60
 6    720 x 480    ( 330mm x 210mm )   60
 7    640 x 480    ( 330mm x 210mm )   60
 8    640 x 400    ( 330mm x 210mm )   60
 9    640 x 350    ( 330mm x 210mm )   60
 10   512 x 384    ( 330mm x 210mm )   60
 11   400 x 300    ( 330mm x 210mm )   60
 12   320 x 240    ( 330mm x 210mm )   60
 13   320 x 200    ( 330mm x 210mm )   60
 14  1600 x 1200   ( 330mm x 210mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
Setting size to 14, rotation to normal
Setting reflection on neither axis

erdem@parvi-laptop:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1600 x 1200
default connected 1280x800+0+0 (0x7d) normal (normal) 0mm x 0mm
        Identifier: 0x7c
        Timestamp:  -938460748
        Subpixel:   horizontal rgb
        Clones:
        CRTC:       0
        CRTCs:      0
  1280x800 (0x7d)   61.4MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   48.0KHz
        v: height  800 start    0 end    0 total  800           clock   60.0Hz
  1280x768 (0x7e)   59.0MHz
        h: width  1280 start    0 end    0 total 1280 skew    0 clock   46.1KHz
        v: height  768 start    0 end    0 total  768           clock   60.0Hz
  1024x768 (0x7f)   47.2MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   46.1KHz
        v: height  768 start    0 end    0 total  768           clock   60.0Hz
  848x480 (0x80)   24.4MHz
        h: width   848 start    0 end    0 total  848 skew    0 clock   28.8KHz
        v: height  480 start    0 end    0 total  480           clock   60.0Hz
  800x600 (0x81)   28.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.0KHz
        v: height  600 start    0 end    0 total  600           clock   60.0Hz
  720x576 (0x82)   24.9MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   34.6KHz
        v: height  576 start    0 end    0 total  576           clock   60.0Hz
  720x480 (0x83)   20.7MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock   28.8KHz
        v: height  480 start    0 end    0 total  480           clock   60.0Hz
  640x480 (0x84)   18.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   28.8KHz
        v: height  480 start    0 end    0 total  480           clock   60.0Hz
  640x400 (0x85)   15.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   24.0KHz
        v: height  400 start    0 end    0 total  400           clock   60.0Hz
  640x350 (0x86)   13.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   21.0KHz
        v: height  350 start    0 end    0 total  350           clock   60.0Hz
  512x384 (0x87)   11.8MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   23.0KHz
        v: height  384 start    0 end    0 total  384           clock   60.0Hz
  400x300 (0x88)    7.2MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   18.0KHz
        v: height  300 start    0 end    0 total  300           clock   60.0Hz
  320x240 (0x89)    4.6MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   14.4KHz
        v: height  240 start    0 end    0 total  240           clock   60.0Hz
  320x200 (0x8a)    3.8MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   12.0KHz
        v: height  200 start    0 end    0 total  200           clock   60.0Hz
  1600x1200 (0x8b)  115.2MHz
        h: width  1600 start    0 end    0 total 1600 skew    0 clock   72.0KHz
        v: height 1200 start    0 end    0 total 1200           clock   60.0Hz

erdem@parvi-laptop:~$ xrandr --verbose --fb 1600x1200
screen 0: 1600x1200 420x315 mm  96.76dpi

---

