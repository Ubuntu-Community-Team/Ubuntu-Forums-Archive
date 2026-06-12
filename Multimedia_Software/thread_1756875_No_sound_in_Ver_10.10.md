---
title: "No sound in Ver 10.10"
date: 2011-05-12
forum: Multimedia Software
---

### Post by Marc Blum on 2011-05-12
I've been trying to get my sound system to work for a long time with no success. Lately I've trying to do it by using the sticky at the beginning  of this forum. I followed all the steps; They showed me  that I had a HDA ATI SB card in my computer, but no sound module which of course explains why I don't have sound. Now I said I followed all the instructions in the sticky, but only uu to a point. And that point is as follows: The command: [sudo module-assistant a-i   alsa-source] runs for a little while (a few seconds) then stops and produces the error copied below. 

for i in control postinst postrm ; do \                                     
 &#9474;         if [ -f debian/$i.orig ]; then \                                    
 &#9474;         mv -f debian/$i.orig debian/$i ; \                                  
 &#9474;         fi ; \                                                              
 &#9474;         done                                                                
 &#9474; rm -f control-munge                                                         
 &#9474; make mrproper                                                               
 &#9474; make[1]: Entering directory `/usr/src/modules/alsa-driver'                  
 &#9474; rm -f .depend *.o snd.map*                                                  
 &#9474; rm -f modules/*.o modules/*.ko                                              
 &#9474; make[2]: Entering directory `/usr/src/modules/alsa-driver/include'          
 &#9474; rm -f .depend core *.o sndversions.h modules/*.ver modules/*.stamp          
 &#9474; make -C sound clean                                                         
 &#9474; make[3]: Entering directory `/usr/src/modules/alsa-driver/include/sound'    
 &#9474; rm -f *.h 

What can I do to get the source file compiled so it will do what I need to do to get my sound system working?

---

