---
title: "problem installing SoundBlaster Live 5.1(emu10k1)"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by blufade on 2007-08-22
hi
i got the following errors while i was installing the module-assistant

> Build of the package alsa-source failed! How do you wish to   &#9474;        
       &#9474; proceed? 

and the build log file gave me this

> for i in control postinst postrm ; do \                                    &#8593; 
 &#9474;         if [ -f debian/$i.orig ]; then \                                   &#9646; 
 &#9474;         mv -f debian/$i.orig debian/$i ; \                                 &#9618; Build of the package alsa-source failed! How do you wish to   &#9474;        
       &#9474; proceed? 
 &#9474;         fi ; \                                                             &#9618; 
 &#9474;         done                                                               &#9618; 
 &#9474; rm -f control-munge                                                        &#9618; 
 &#9474; make mrproper                                                              &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/modules/alsa-driver'                 &#9618; 
 &#9474; rm -f .depend *.o snd.map*                                                 &#9618; 
 &#9474; rm -f /*.ver                                                               &#9618; 
 &#9474; rm -f modules/*.o modules/*.ko                                             &#9618; 
 &#9474; make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'           &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'            &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618; 
 &#9474; rm -f configure-stamp                                                      &#8595; 


i was following instruction on [this page]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

