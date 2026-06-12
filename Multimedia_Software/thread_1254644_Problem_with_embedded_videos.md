---
title: "Problem with embedded videos"
date: 2009-08-31
forum: Multimedia Software
---

### Post by grillosolitario on 2009-08-31
Hello, 

 I'm a Ubuntu 9.04 and firefox 3.023 user. I'm having a problem with embedded youtube videos. I can see them, but the image is a bit noisy. It flashes. The sound is ok. The most strange thing is that the problem only happens when the video is embedded. In youtube web page I can see them all right. It doesn't only happens with youtube; however it doesn't happen with all online video services. For example, I have no problem with 'break' embedded videos. I don't have gnash nor any other plugin but the adobe ones:

$ aptitude search flash
i   adobe-flashplugin               - Adobe Flash Player plugin version 10      
p   flashblock                      - mozilla extension that replaces flash elem
i A flashplugin-installer           - Adobe Flash Player plugin installer       
p   flashplugin-nonfree             - Adobe Flash Player plugin installer (trans
p   flashplugin-nonfree-extrasound  - Adobe Flash Player platform support librar
p   flashrom                        - Universal BIOS/ROM/flash programming utili
p   flashybrid                      - automates use of a flash disk as the root 
p   libroxen-flash2                 - Flash2 module for the Roxen Challenger web
p   m16c-flash                      - Flash programmer for Renesas M16C and R8C 
p   vrflash                         - tool to flash kernels and romdisks to Agen

 Do you know what the problem could be? 

 Thanks in advance,

 Grillo Solitario

---

### Post by baltadt on 2009-09-14
I'm new to this but it sound like one of two problem.

1) flash block might be hampering it or

2) I only have flash player 10 installed and every site works fine for me...hulu, youtube, smallworlds etc.  so maybe all of the flash(etc) you have installed might be the problem.

But don't take my word because I'm still a new also.

---

### Post by mike67114 on 2009-09-14
This is the result of my "aptitude search flash" command:

p   flashblock                      - mozilla extension that replaces flash elem
i   flashplugin-installer           - Adobe Flash Player plugin installer       
i   flashplugin-nonfree             - Adobe Flash Player plugin installer (trans
p   flashrom                        - Universal BIOS/ROM/flash programming utili
p   flashybrid                      - automates use of a flash disk as the root 
c   libflash-mozplugin              - GPL Flash (SWF) Library - Mozilla-compatib
c   libflash0c2                     - GPL Flash (SWF) Library - shared library  
p   libroxen-flash2                 - Flash2 module for the Roxen Challenger web
p   m16c-flash                      - Flash programmer for Renesas M16C and R8C 
p   vrflash   

I am a total newcomer to linux and can only relate my own experience.

I had trouble with flash early on but I used the suggestions in the sticky topics at the top of the multimedia forum page and the problems vanished.
i hope this is helpful.

---

