---
title: "AR9285 wireless adapter"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by netmonky on 2010-11-07
Hi All,

looking for some help :-). Upgraded to 10.10 expecting some errors and to be honest not seen many issues - I then tried to connect to my friends wireless and all went wrong :(. 

I have a toshiba nb200 with an inbuilt AR9285 wireless adapter. I can connect to the network but it seems to stop responding to ip traffic for minutes at a time, If I disconnect and re-connect it works again -- can anyone help?

I have driver ath9k version: 2.6.35.23-generic.


Thanks in advance!


Mark

---

### Post by netmonky on 2010-11-07
tried on friends home network and this looks to only be an issue when using wpa. wireless worked ok on 10.4 but not on 10.10... van anyone help?

---

### Post by uncaspi on 2010-11-07
Quote from thread [http://ubuntuforums.org/showthread.php?t=1286503&highlight=ath9k&page=4](http://ubuntuforums.org/showthread.php?t=1286503&highlight=ath9k&page=4)

Solved so far.
rsisto, I have the same VAIO and had the same problem with ubuntu 10.04 and the 2.6.32-22-generic kernel... i tried everything and the only thing that worked was to compile and install compat-wireless-2.6.35-rc2... i know this is not intented for the kernel i have but this solved the issue for me!! i downloaded from linuxwireless and the run the default process: driver-select, make, make install, make unload, /etc/init.d/networking restart and the modprobe ath9k and it worked like a charm!!! the only remaining issue is that after computer restarts the problem comes again, i re-install the module and it works again!... i'm suspending rather than shutting down until i found a solution for that but my wifi is Ok!.

---

### Post by netmonky on 2010-11-08
cool - thanks, I will give this a go!

---

### Post by netmonky on 2010-11-14
Cool :-) .. worked a charm. Many thanks!

---

### Post by Fourcultures on 2011-01-12
Perhaps you worked this out by now but one way to fix it so you don't have to keep reloading the module at every start up is to add the name of the module you want to load on start-up to the modules file in the /etc/ folder. 
I did this with the omnibook module and it worked for me. 
[INDENT][FONT=Courier New][COLOR=#ff0000][SIZE=2]sudo nano /etc/modules[/SIZE][/COLOR][/FONT]
[FONT=Courier New][COLOR=#000000][SIZE=2]Add the line below and save the file. (Note to save press ctrl o, press the enter key then ctrl x).[/SIZE][/COLOR][/FONT]
[FONT=Courier New][COLOR=#ff0000][SIZE=2]omnibook[/SIZE][/COLOR][/FONT]
[/INDENT]Here's the [post]("http://ubuntuforums.org/showthread.php?t=1215665&page=24") I'm quoting from that showed the way:
                   [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]http://ubuntuforums.org/showthread.php?t=1215665&page=24

[/SIZE][/FONT][/COLOR]

---

