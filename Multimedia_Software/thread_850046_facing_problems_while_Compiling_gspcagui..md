---
title: "facing problems while Compiling gspcagui."
date: 2008-07-05
forum: Multimedia Software
---

### Post by Ravi_Chobey on 2008-07-05
Hi All,

This is my first post to this forum.
I am getting the following error while compiling gspcagui package, so that i
can use that board in my Embedded projects.

```
bash-2.05b# make
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c convert
er/cvrt.c
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c encoder
/encoder.c
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c encoder
/huffman.c
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c encoder
/marker.c
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c encoder
/quant.c
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c encoder
/cvrt_frame.c
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c decoder
/decoder.c
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c osd/fon
t.c
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c filter/
rot.c
arm_920t_le-gcc -O2 -DLINUX -I/usr/local/include/SDL -D_GNU_SOURCE=1  -c gui.c
In file included from gui.c:28:
gui_internal.h:22:21: SDL/SDL.h: No such file or directory
In file included from gui.c:28:
gui_internal.h:36: error: parse error before "SDL_Surface"
gui_internal.h:39: error: parse error before "SDLKey"
gui_internal.h:39: warning: no semicolon at end of struct or union
gui_internal.h:41: error: parse error before '}' token
gui_internal.h:41: warning: data definition has no type or storage class
gui_internal.h:70: error: parse error before "SDL_Surface"
gui_internal.h:70: warning: no semicolon at end of struct or union
gui_internal.h:71: warning: data definition has no type or storage class
gui_internal.h:72: error: parse error before '}' token
gui_internal.h:81: error: parse error before "SDL_Surface"
gui_internal.h:81: warning: no semicolon at end of struct or union
gui_internal.h:82: warning: data definition has no type or storage class
gui_internal.h:83: error: parse error before '}' token
gui_internal.h:96: error: parse error before "SDL_Surface"
gui_internal.h:96: warning: no semicolon at end of struct or union
gui_internal.h:97: warning: data definition has no type or storage class
gui_internal.h:98: error: parse error before '*' token
gui_internal.h:98: warning: data definition has no type or storage class
gui_internal.h:99: error: parse error before '*' token
gui_internal.h:99: warning: data definition has no type or storage class
gui_internal.h:100: error: parse error before '}' token
gui_internal.h:107: error: parse error before "SDL_Surface"
gui_internal.h:107: warning: no semicolon at end of struct or union
gui_internal.h:108: warning: data definition has no type or storage class
gui_internal.h:109: error: parse error before '*' token
gui_internal.h:109: warning: data definition has no type or storage class
gui_internal.h:110: error: parse error before '*' token
gui_internal.h:110: warning: data definition has no type or storage class
gui_internal.h:111: error: parse error before '*' token
gui_internal.h:111: warning: data definition has no type or storage class
gui_internal.h:112: error: parse error before '*' token
gui_internal.h:112: warning: data definition has no type or storage class
gui_internal.h:113: error: parse error before '}' token
gui_internal.h:122: error: parse error before "SDL_Surface"
gui_internal.h:122: warning: no semicolon at end of struct or union
gui_internal.h:123: warning: data definition has no type or storage class
gui_internal.h:124: error: parse error before '*' token
gui_internal.h:124: warning: data definition has no type or storage class
gui_internal.h:125: error: parse error before '*' token
gui_internal.h:125: warning: data definition has no type or storage class
gui_internal.h:126: error: parse error before '}' token
gui_internal.h:134: error: parse error before "SDL_Surface"
gui_internal.h:134: warning: no semicolon at end of struct or union
gui_internal.h:135: warning: data definition has no type or storage class
gui_internal.h:136: error: parse error before '}' token
gui_internal.h:140: error: parse error before "SDL_Surface"
gui_internal.h:142: error: parse error before "SDL_Surface"
gui_internal.h:150: error: parse error before "SDL_Surface"
gui_internal.h:153: error: parse error before "SDL_Surface"
gui_internal.h:160: error: parse error before "SDL_Surface"
gui_internal.h:163: error: parse error before "SDL_Surface"
gui_internal.h:172: error: parse error before "SDL_Surface"
gui_internal.h:175: error: parse error before "SDL_Surface"
gui_internal.h:177: error: parse error before "SDL_Surface"
gui_internal.h:186: error: parse error before "SDL_Surface"
gui_internal.h:189: error: parse error before "SDL_Surface"
gui_internal.h:191: error: parse error before "SDL_Surface"
gui_internal.h:200: error: parse error before "SDL_Surface"
gui_internal.h:203: error: parse error before "SDL_Surface"
gui_internal.h:211: error: parse error before "SDL_Surface"
gui_internal.h:217: error: parse error before "key"
gui.c:43: error: conflicting types for 'curseur'
gui_internal.h:82: error: previous declaration of 'curseur' was here
gui.c:66: error: conflicting types for 'padup'
gui_internal.h:108: error: previous declaration of 'padup' was here
gui.c:67: error: conflicting types for 'paddown'
gui_internal.h:109: error: previous declaration of 'paddown' was here
gui.c:68: error: conflicting types for 'padleft'
gui_internal.h:111: error: previous declaration of 'padleft' was here
gui.c:69: error: conflicting types for 'padright'
gui_internal.h:110: error: previous declaration of 'padright' was here
gui.c:70: error: conflicting types for 'padcenter'
gui_internal.h:112: error: previous declaration of 'padcenter' was here
gui.c:72: error: conflicting types for 'togleup'
gui_internal.h:123: error: previous declaration of 'togleup' was here
gui.c:73: error: conflicting types for 'togledown'
gui_internal.h:124: error: previous declaration of 'togledown' was here
gui.c:75: error: conflicting types for 'togleall'
gui_internal.h:125: error: previous declaration of 'togleall' was here
gui.c:139: error: parse error before "SDL_Surface"
gui.c: In function `draw_surface':
gui.c:141: error: `SDL_Rect' undeclared (first use in this function)
gui.c:141: error: (Each undeclared identifier is reported only once
gui.c:141: error: for each function it appears in.)
gui.c:141: error: parse error before "dest"
gui.c:142: error: `dest' undeclared (first use in this function)
gui.c:142: error: `x' undeclared (first use in this function)
gui.c:143: error: `y' undeclared (first use in this function)
gui.c:144: error: `surface' undeclared (first use in this function)
gui.c:146: error: `screen' undeclared (first use in this function)
gui.c: At top level:
gui.c:161: error: parse error before '*' token
gui.c: In function `imgload':
gui.c:163: error: `SDL_Surface' undeclared (first use in this function)
gui.c:163: error: `Object' undeclared (first use in this function)
gui.c:192: error: `SDL_SWSURFACE' undeclared (first use in this function)
gui.c: In function `init_info':
gui.c:202: error: dereferencing pointer to incomplete type
gui.c:203: error: dereferencing pointer to incomplete type
gui.c:204: error: dereferencing pointer to incomplete type
gui.c:214: error: dereferencing pointer to incomplete type
gui.c:215: error: dereferencing pointer to incomplete type
gui.c:216: error: dereferencing pointer to incomplete type
gui.c:217: error: dereferencing pointer to incomplete type
gui.c:218: error: dereferencing pointer to incomplete type
gui.c: At top level:
gui.c:222: error: parse error before "SDL_Surface"
gui.c: In function `draw_info':
gui.c:225: error: `myecran' undeclared (first use in this function)
gui.c:225: error: `Screen' undeclared (first use in this function)
gui.c: In function `free_info':
gui.c:230: error: dereferencing pointer to incomplete type
gui.c:231: error: dereferencing pointer to incomplete type
gui.c:232: error: dereferencing pointer to incomplete type
gui.c: At top level:
gui.c:235: error: parse error before "SDL_Surface"
gui.c: In function `process_info':
gui.c:237: error: `myecran' undeclared (first use in this function)
gui.c:238: error: `chaine' undeclared (first use in this function)
gui.c:241: error: `Screen' undeclared (first use in this function)
gui.c: In function `init_button':
gui.c:260: error: dereferencing pointer to incomplete type
gui.c:261: error: dereferencing pointer to incomplete type
gui.c:262: error: dereferencing pointer to incomplete type
gui.c:263: error: dereferencing pointer to incomplete type
gui.c:265: error: dereferencing pointer to incomplete type
gui.c:267: error: dereferencing pointer to incomplete type
gui.c: At top level:
gui.c:270: error: parse error before "SDL_Surface"
gui.c: In function `refresh_button':
gui.c:272: error: `mybutt' undeclared (first use in this function)
gui.c:272: error: `value' undeclared (first use in this function)
gui.c:273: error: `Screen' undeclared (first use in this function)
gui.c: In function `free_button':
gui.c:278: error: dereferencing pointer to incomplete type
gui.c:279: error: dereferencing pointer to incomplete type
gui.c: At top level:
gui.c:283: error: parse error before "SDL_Surface"
gui.c: In function `draw_button':
gui.c:285: error: `mybutt' undeclared (first use in this function)
gui.c:287: error: `Screen' undeclared (first use in this function)
gui.c: At top level:
gui.c:297: error: parse error before "SDL_Surface"
gui.c: In function `process_button':
gui.c:301: error: `mybutt' undeclared (first use in this function)
gui.c:303: error: `Screen' undeclared (first use in this function)
gui.c:304: error: `message' undeclared (first use in this function)
gui.c:307: error: `value' undeclared (first use in this function)
gui.c: In function `init_potentiometre':
gui.c:337: error: dereferencing pointer to incomplete type
gui.c:338: error: dereferencing pointer to incomplete type
gui.c:339: error: dereferencing pointer to incomplete type
gui.c:340: error: dereferencing pointer to incomplete type
gui.c:341: error: dereferencing pointer to incomplete type
gui.c:342: error: dereferencing pointer to incomplete type
gui.c:344: error: dereferencing pointer to incomplete type
gui.c:344: error: dereferencing pointer to incomplete type
gui.c:346: error: dereferencing pointer to incomplete type
gui.c:346: error: dereferencing pointer to incomplete type
gui.c:346: error: dereferencing pointer to incomplete type
gui.c:349: error: dereferencing pointer to incomplete type
gui.c:352: error: dereferencing pointer to incomplete type
gui.c:354: error: dereferencing pointer to incomplete type
gui.c:355: error: dereferencing pointer to incomplete type
gui.c:357: error: dereferencing pointer to incomplete type
gui.c:359: error: dereferencing pointer to incomplete type
gui.c:361: error: dereferencing pointer to incomplete type
gui.c:361: error: dereferencing pointer to incomplete type
gui.c:361: error: dereferencing pointer to incomplete type
gui.c:363: error: dereferencing pointer to incomplete type
gui.c: At top level:
gui.c:369: error: parse error before "SDL_Surface"
gui.c: In function `draw_potentiometre':
gui.c:372: error: `mypot' undeclared (first use in this function)
gui.c:372: error: `Screen' undeclared (first use in this function)
gui.c: At top level:
gui.c:378: error: parse error before "SDL_Surface"
gui.c: In function `refresh_potentiometre':
gui.c:383: error: `mypot' undeclared (first use in this function)
gui.c:385: error: `value' undeclared (first use in this function)
gui.c:390: error: `Screen' undeclared (first use in this function)
gui.c: In function `free_potentiometre':
gui.c:396: error: dereferencing pointer to incomplete type
gui.c:397: error: dereferencing pointer to incomplete type
gui.c: At top level:
gui.c:404: error: parse error before "SDL_Surface"
gui.c: In function `process_potentiometre':
gui.c:414: error: `mypot' undeclared (first use in this function)
gui.c:417: error: `yp' undeclared (first use in this function)
gui.c:418: error: `message' undeclared (first use in this function)
gui.c:429: error: `Screen' undeclared (first use in this function)
gui.c: In function `init_control':
gui.c:453: error: dereferencing pointer to incomplete type
gui.c:454: error: dereferencing pointer to incomplete type
gui.c:455: error: dereferencing pointer to incomplete type
gui.c:456: error: dereferencing pointer to incomplete type
gui.c:457: error: dereferencing pointer to incomplete type
gui.c:458: error: dereferencing pointer to incomplete type
gui.c:459: error: dereferencing pointer to incomplete type
gui.c:460: error: dereferencing pointer to incomplete type
gui.c:461: error: dereferencing pointer to incomplete type
gui.c:462: error: dereferencing pointer to incomplete type
gui.c:463: error: dereferencing pointer to incomplete type
gui.c:463: error: dereferencing pointer to incomplete type
gui.c:463: error: dereferencing pointer to incomplete type
gui.c:472: error: dereferencing pointer to incomplete type
gui.c:476: error: dereferencing pointer to incomplete type
gui.c:478: error: dereferencing pointer to incomplete type
gui.c:479: error: dereferencing pointer to incomplete type
gui.c:479: error: dereferencing pointer to incomplete type
gui.c:480: error: dereferencing pointer to incomplete type
gui.c:482: error: dereferencing pointer to incomplete type
gui.c:484: error: dereferencing pointer to incomplete type
gui.c:485: error: dereferencing pointer to incomplete type
gui.c:486: error: dereferencing pointer to incomplete type
gui.c:486: error: dereferencing pointer to incomplete type
gui.c:486: error: dereferencing pointer to incomplete type
gui.c:486: error: dereferencing pointer to incomplete type
gui.c:487: error: dereferencing pointer to incomplete type
gui.c:495: error: dereferencing pointer to incomplete type
gui.c: In function `free_control':
gui.c:508: error: dereferencing pointer to incomplete type
gui.c:509: error: dereferencing pointer to incomplete type
gui.c:510: error: dereferencing pointer to incomplete type
gui.c:511: error: dereferencing pointer to incomplete type
gui.c: At top level:
gui.c:515: error: parse error before "SDL_Surface"
gui.c: In function `draw_control':
gui.c:519: error: `mycontrol' undeclared (first use in this function)
gui.c:522: error: `Screen' undeclared (first use in this function)
gui.c: At top level:
gui.c:551: error: parse error before "SDL_Surface"
gui.c: In function `process_control':
gui.c:559: error: `mycontrol' undeclared (first use in this function)
gui.c:574: error: `yp' undeclared (first use in this function)
gui.c:579: error: `message' undeclared (first use in this function)
gui.c:590: error: `Screen' undeclared (first use in this function)
gui.c: At top level:
gui.c:630: error: parse error before "SDL_Surface"
gui.c: In function `refresh_control':
gui.c:632: error: `mycontrol' undeclared (first use in this function)
gui.c:632: error: `value' undeclared (first use in this function)
gui.c:633: error: `masq' undeclared (first use in this function)
gui.c:634: error: `Screen' undeclared (first use in this function)
gui.c: In function `init_pad':
gui.c:650: error: dereferencing pointer to incomplete type
gui.c:651: error: dereferencing pointer to incomplete type
gui.c:652: error: dereferencing pointer to incomplete type
gui.c:653: error: dereferencing pointer to incomplete type
gui.c:654: error: dereferencing pointer to incomplete type
gui.c:655: error: dereferencing pointer to incomplete type
gui.c:656: error: dereferencing pointer to incomplete type
gui.c:657: error: dereferencing pointer to incomplete type
gui.c:658: error: dereferencing pointer to incomplete type
gui.c:659: error: dereferencing pointer to incomplete type
gui.c: In function `free_pad':
gui.c:663: error: dereferencing pointer to incomplete type
gui.c:664: error: dereferencing pointer to incomplete type
gui.c:665: error: dereferencing pointer to incomplete type
gui.c:666: error: dereferencing pointer to incomplete type
gui.c:667: error: dereferencing pointer to incomplete type
gui.c:668: error: dereferencing pointer to incomplete type
gui.c: At top level:
gui.c:671: error: parse error before "SDL_Surface"
gui.c: In function `draw_pad':
gui.c:673: error: `mypad' undeclared (first use in this function)
gui.c:673: error: `Screen' undeclared (first use in this function)
gui.c: At top level:
gui.c:677: error: parse error before "SDL_Surface"
gui.c: In function `process_pad':
gui.c:683: error: `valx' undeclared (first use in this function)
gui.c:683: error: `mypad' undeclared (first use in this function)
gui.c:684: error: `valy' undeclared (first use in this function)
gui.c:704: error: `Screen' undeclared (first use in this function)
gui.c:724: error: `message' undeclared (first use in this function)
gui.c: In function `init_togle':
gui.c:748: error: dereferencing pointer to incomplete type
gui.c:749: error: dereferencing pointer to incomplete type
gui.c:750: error: dereferencing pointer to incomplete type
gui.c:751: error: dereferencing pointer to incomplete type
gui.c:752: error: dereferencing pointer to incomplete type
gui.c:752: error: dereferencing pointer to incomplete type
gui.c:753: error: dereferencing pointer to incomplete type
gui.c:754: error: dereferencing pointer to incomplete type
gui.c:755: error: dereferencing pointer to incomplete type
gui.c:757: error: dereferencing pointer to incomplete type
gui.c:758: error: dereferencing pointer to incomplete type
gui.c:760: error: dereferencing pointer to incomplete type
gui.c:761: error: dereferencing pointer to incomplete type
gui.c:762: error: dereferencing pointer to incomplete type
gui.c:763: error: dereferencing pointer to incomplete type
gui.c: In function `free_togle':
gui.c:768: error: dereferencing pointer to incomplete type
gui.c:769: error: dereferencing pointer to incomplete type
gui.c:770: error: dereferencing pointer to incomplete type
gui.c:771: error: dereferencing pointer to incomplete type
gui.c: At top level:
gui.c:774: error: parse error before "SDL_Surface"
gui.c: In function `draw_togle':
gui.c:776: error: `mytogle' undeclared (first use in this function)
gui.c:779: error: `Screen' undeclared (first use in this function)
gui.c: At top level:
gui.c:796: error: parse error before "SDL_Surface"
gui.c: In function `process_togle':
gui.c:801: error: `y' undeclared (first use in this function)
gui.c:801: error: `mytogle' undeclared (first use in this function)
gui.c:826: error: `Screen' undeclared (first use in this function)
gui.c:831: error: `message' undeclared (first use in this function)
gui.c: At top level:
gui.c:919: error: parse error before "key"
make: *** [gui.o] Error 1
bash-2.05b# apt-file search SDL.h
bash: apt-file: command not found 
```

Anybody have faced this type in there projects.Please help me out.
I have tried some other applications also but for them also i am getting errors.
I need to make my USB webcam to work in ARM9 based board.

Regards,
Ravi

---

