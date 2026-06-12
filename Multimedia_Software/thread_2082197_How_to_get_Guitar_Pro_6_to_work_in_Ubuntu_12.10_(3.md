---
title: "How to get Guitar Pro 6 to work in Ubuntu 12.10 (32-bit)"
date: 2012-11-08
forum: Multimedia Software
---

### Post by Antoon Stessels on 2012-11-08
I noticed after upgrading to Ubuntu 12.10 that Guitar Pro 6 wouldn't launch anymore. After looking around on the internet, I found the solution.

All credit goes to Mathieu Bourotte ([http://getsatisfaction.guitar-pro.com/arobas_music/topics/guitar_pro_6_not_working_after_upgrade_to_ubuntu_12_10](http://getsatisfaction.guitar-pro.com/arobas_music/topics/guitar_pro_6_not_working_after_upgrade_to_ubuntu_12_10)) for supplying us with the solution. 

Follow these easy steps. 

1) hold down ALT + F2 and type in 'gksudo nautilus' to launch nautilus as the root user.
2) go to /lib/i386-linux-gnu and copy the file 'libz.so.1.2.7' into the /opt/GuitarPro6 folder
3) in the same folder, find 'lib.so.1' and rename it to 'lib.so.1(bis)'
4) rename the file you just copied into the folder to 'lib.so.1'.
5) GP6 should launch now!

Just spreading the word. ;-)

---

### Post by Finn bjerke on 2013-01-14
**[SIZE="3"]MUCH BETTER SOLUTION link dont copy[/SIZE]**


Rename or delete  ./opt/guitar pro/libz.so.1 and replace it with a softlink to ./lib/i386-linux-gnu/libz.so.1   that way you will not screw up dependencies in the system. 

how to do it: 
Press windows button and write gksudo nautilus
enter your codeword for Ubuntu
now you can navigate using nautilus and change things you are now root administrator (close to god if you like)
go to ./lib/i386-linux-gnu (this is a folder) using nautilus find the file named libz.so.1 rightclick on it.
Make a shortcut or what ever its called in your language. 
Cut the shortcut out and insert it in the guitar pro folder thus:
click on libz.so.1 then press ctrl+x
go to ./opt/guitar pro using nautilus
delete the local libz.so.1 or rename it libz.so.1(bis)
Then  pres ctrl+v (inserting the shortcut file from the previous position ./lib/) 
reboot while tuning guitar.... (fast Ubuntu rebooting)

If thangs go wrong its your problem not mine, however I hope it helps go play guitar now and have fun.

---

### Post by deprima on 2013-07-08
Hi I just saw your answer on how to get Guitar Pro 6 to work in ubuntu as I have the same problem it was of interest to me. I follewd the first two instructions and i then get a box asking RUN and I am unsure as to what I should type.
 I tried typing the program name and clicking ok, the box disappears and nothing else happens.I also tried typing /lib/i386 gnu again nothing happens. Perhaps you could advise what I am doing wrong as I can not find folder ./lib/i386?

---

