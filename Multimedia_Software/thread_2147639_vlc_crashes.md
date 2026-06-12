---
title: "vlc crashes"
date: 2013-05-22
forum: Multimedia Software
---

### Post by bgoleb on 2013-05-22
When i try to play anything with vlc it crashes. I tried to remove ~/.config/vlc, also tried to purge vlc and install it again.

command line output:
```

VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x95e108] main libvlc: Uruchamianie vlc z domy&#347;lnym interfejsem. U&#380;yj 'cvlc' aby u&#380;ywa&#263; vlc bez interfejsu.
MKV/Ebml Parser: m_el[mi_level] == NULL
MKV/Ebml Parser: Up cannot escape itself
MKV/Ebml Parser: m_el[mi_level] == NULL
MKV/Ebml Parser: Up cannot escape itself
[0x7fe2d4001268] xcb_xv vout display error: cannot create X11 window: X11 error 8
[0x7fe2d4001268] xcb_xv vout display error: no available XVideo adaptor
Gen6+ requires Kernel 3.6 or later.
vlc: ../../../../../src/mesa/main/context.c:1545: _mesa_make_current: Warunek zapewnienia `newCtx->Version > 0' nie zosta&#322; spe&#322;niony.
Przerwane (core dumped)

```

---

### Post by alexkarnaukhov on 2013-05-23
Same thing... After last update...
> VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x87f5908] main libvlc: &#1047;&#1072;&#1087;&#1091;&#1089;&#1082; vlc &#1089; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;&#1086;&#1084; &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102;. &#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1081;&#1090;&#1077; 'cvlc' &#1076;&#1083;&#1103; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072; vlc &#1073;&#1077;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;&#1072;.
TagLib: MP4: No audio tracks
TagLib: MP4: No audio tracks
TagLib: MP4: No audio tracks
TagLib: MP4: No audio tracks
[0xafd062c0] xcb_xv vout display error: cannot create X11 window: X11 error 8
[0xafd062c0] xcb_xv vout display error: no available XVideo adaptor
[0xafd062c0] xcb_xv vout display error: cannot create X11 window: X11 error 8
[0xafd062c0] xcb_xv vout display error: no available XVideo adaptor
Gen6+ requires Kernel 3.6 or later.
vlc: ../../../../../src/mesa/main/context.c:1545: _mesa_make_current: &#1055;&#1088;&#1086;&#1074;&#1077;&#1088;&#1086;&#1095;&#1085;&#1086;&#1077; &#1091;&#1090;&#1074;&#1077;&#1088;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077; «newCtx->Version > 0» &#1085;&#1077; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1086;.
&#1040;&#1074;&#1072;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#1086;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074; (&#1089;&#1076;&#1077;&#1083;&#1072;&#1085; &#1076;&#1072;&#1084;&#1087; &#1087;&#1072;&#1084;&#1103;&#1090;&#1080;)


---

### Post by snkmad on 2013-05-26
Same problem here. 
I don't think it's VLC fault. I tried playing minecraft and netflix using the modified wine, and both crashed as well.

I have a Core i5, with an Intel HD 3000 graphics card, so i suppose it's a video driver issue.
It's running Ubuntu 12.04 64-bit, kernel 3.5.0-18 and PPA xorg-edgers for latest video drivers.

---

### Post by alexkarnaukhov on 2013-05-27
Yes, I think this is video driver issue too. I`m have nvidia optimus graphics card, and there is always many problems with it on ubuntu. 
Switching to GNOME interface solve problem with vlc. Damn unity...

Ok, bug with vlc seem has been repaired after today update.

---

### Post by snkmad on 2013-05-28
Unfortunately it didn't fix for me.
glxinfo gives the same error:
> name of display: :0.0
Gen6+ requires Kernel 3.6 or later.
glxinfo: ../../../../../src/mesa/main/context.c:1545: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
Aborted (core dumped)

---

### Post by snkmad on 2013-06-01
xorg-edgers require at least kernel 3.6 in order to work.
"If you are using precise on a 965 or newer intel, be sure to install linux-generic-lts-raring as mesa now requires a 3.6 kernel!"
[xorg-edgers launchpad site.]("https://launchpad.net/~xorg-edgers/+archive/ppa")

The suggested solution:
> sudo apt-get install linux-generic-lts-raring

---

### Post by markcomp77 on 2013-06-06
[quote="snkmad"]The suggested solution:
```
 sudo apt-get install linux-generic-lts-raring
```[/quote]
it works for my ubuntu 12.04 64
thx :)

---

