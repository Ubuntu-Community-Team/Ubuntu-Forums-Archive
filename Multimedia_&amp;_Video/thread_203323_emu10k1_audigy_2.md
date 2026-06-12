---
title: "emu10k1 audigy 2"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by conosc on 2006-06-25
I'm new to linux today and was trying to get my sound card installed "audigy 2 platinum" and i found a web page that told me where the driver was. [http://files.printf.dk/guides/audigy2.htm](http://files.printf.dk/guides/audigy2.htm)
but any time i try the commands such as "cvs, or make"  in the konsole it says  
bash: make command not found
or 
bash: cvs command not found
also in there read me they use the make command also. which I'm sure i just am doing one step wrong but I'm lost 
so if anyone knows how i can get this emu10k1 driver installed or knows a better way PLEASE HELP.

---

### Post by KYAAngel on 2006-06-25
This module should already be installed on your computer.  Try issuing the following command and see if sound starts working.

sudo modprobe snd_emu10k1

---

