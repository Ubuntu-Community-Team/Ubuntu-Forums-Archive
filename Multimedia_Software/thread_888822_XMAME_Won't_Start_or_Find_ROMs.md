---
title: "XMAME Won't Start or Find ROMs"
date: 2008-08-13
forum: Multimedia Software
---

### Post by nckinfn04 on 2008-08-13
This is the error I get. The ROMs are in the correct folder in the ROMpath defaulted and specified.

> nick@extubuntu-newstyle:~$ xmame dkong
GLERROR: cannot access GLU library libGLU.so
GLERROR: dlerror() returns [libGLU.so: cannot open shared object file: No such file or directory]
Use of OpenGL mode disabled
XDGAOpenFramebuffer failed
Use of DGA-modes is disabled
info: trying to parse: /etc/xmame/xmamerc
error: unknown option history_file, on line 13 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option mameinfo_file, on line 14 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option fuzzycmp, on line 33 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option skip_disclaimer, on line 35 of file: /etc/xmame/xmamerc
   ignoring line
info: trying to parse: /home/nick/.xmame/xmamerc
info: trying to parse: /etc/xmame/xmame-x11rc
info: trying to parse: /home/nick/.xmame/xmame-x11rc
info: trying to parse: /etc/xmame/rc/dkongrc
info: trying to parse: /home/nick/.xmame/rc/dkongrc
xmame: could not connect to socket
xmame: No such file or directory
LIRC disabled
loading rom 0: c_5et_g.bin                     
loading rom 1: c_5ct_g.bin                     
loading rom 2: c_5bt_g.bin                     
loading rom 3: c_5at_g.bin                     
loading rom 4: s_3i_b.bin                      
loading rom 5: s_3j_b.bin                      
loading rom 6: v_5h_b.bin                      
loading rom 7: v_3pt.bin                       
loading rom 8: l_4m_b.bin                      
loading rom 9: l_4n_b.bin                      
loading rom 10: l_4r_b.bin                      
loading rom 11: l_4s_b.bin                      
loading rom 12: c-2k.bpr                        
loading rom 13: c-2j.bpr                        
loading rom 14: v-5e.bpr                        
done
c_5et_g.bin  NOT FOUND
c_5ct_g.bin  NOT FOUND
c_5bt_g.bin  NOT FOUND
c_5at_g.bin  NOT FOUND
s_3i_b.bin   NOT FOUND
s_3j_b.bin   NOT FOUND
v_5h_b.bin   NOT FOUND
v_3pt.bin    NOT FOUND
l_4m_b.bin   NOT FOUND
l_4n_b.bin   NOT FOUND
l_4r_b.bin   NOT FOUND
l_4s_b.bin   NOT FOUND
c-2k.bpr     NOT FOUND
c-2j.bpr     NOT FOUND
v-5e.bpr     NOT FOUND
ERROR: required files are missing, the game cannot be run.


Thanks for your help.

---

### Post by markekeller on 2008-08-13
It looks like you have a couple different problems.  The first five lines basically are telling you that you don't have OpenGL installed.  You should - if you've got an ATI or nVidia graphics card, install the driver for it via Hardware Drivers in the administration menu, or otherwise, install the package libglu1-mesa-dev.

The rest of the errors are telling you that the ROM is in the wrong place.  The default location for xmame to look for ROMs is /usr/share/games/xmame/roms, so that's where you need to put your ROM zip.  If you want to make it look somewhere else for ROMs (for example, in a subdirectory of your home folder), then you have to edit the /etc/xmame/xmamerc file.

If after putting your ROM in the right place you still get this error, it could be that the ROM is not compatible with your version of xmame.  This seems unlikely, but you can test it by running ```
mame -verifyroms dkong
```.

Hope that helps!

---

### Post by nckinfn04 on 2008-08-14
Thanks so much! You actually saved me from Windows MAME!

---

### Post by Akuma_s on 2011-04-21
Excellent post, actual solution for xmame in Ubuntu 9.04 ;)

---

