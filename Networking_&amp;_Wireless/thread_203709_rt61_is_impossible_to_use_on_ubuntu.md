---
title: "rt61 is impossible to use on ubuntu"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by Zahlerstreik on 2006-06-25
seriously. ive tried every tutorial on this site for the rt61 wifi card. nothing works. i also haev a USB rt2500. doesn't work either. sure, ubuntu coems with the drivers, but then WHY DOESNT IT work? has anyone gotten thiers to work on dapper 6.06 v 2.6.x-amd64 ? it seems like there is just no hope. not even ndiswrapper is working for me. (then again i am a noob) 
if your rt61 card works please let me know how you did it.

my card is a gigabyte GN-WI01GS

---

### Post by darkshadow on 2006-06-25
Your problem is most likely that you are doing amd64 as I have got it to work perfect under the exact same setup except 32bit for a cousin . You have to make absolutely sure you have 64 bit drivers for both native and for ndiswrapper.

Best chance is 64 bit windows drivers with ndiswrapper

I used this tutorial but the supplied files are 32 bit only [http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

---

### Post by darkshadow on 2006-06-25
I just typed "rt61 64bit drivers" into google and think I found what you need for ndiswrapper. I doubt the native Linux will work since they seem 32bit only

Use the second down for your rt61 and third for 64bit rt2500usb
[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

double check you only use the x64 drivers

---

### Post by he11 on 2006-06-25
i have the same problem man, but my card is a belkin card. ive done everything as well, ndiswrapper isnt working for me, manually configuring isnt working and using the network utility isnt working..... if i figure anything out ill make sure to post here with what i did

---

### Post by Zahlerstreik on 2006-06-26
how would i go about uninstalling the current drivers?
also my ndiswrapper is messed. when i do depmod ndiswrapper i get a fatal error saying that the ndiswrapper module could not be found :/

---

### Post by he11 on 2006-06-26
you can uninstall the drivers with ndiswrapper, the command is: 
sudo ndiswrapper -e <driver name>
idk what to do about that fatal error stuff though

---

### Post by mpa on 2006-06-26
Yah, I am having the same problem. Tried tons of HOWTOs but none of them could make my card get ip address from the router (through dhcp). In fact, after 3 weeks of frustration, I switched to Win XP completely (heresy !), what can I say, Windows+Internet is better than Ubuntu+No Internet. I think I am gonna try OpenBSD though since my card, Digitus DN-7006GA is listed as supported by OBSD.

---

### Post by Rob18 on 2007-07-12
I got mine to work with wlanassistant

---

### Post by kevdog on 2007-07-12
With all ra chipsets (61, 73, 2500, etc), its probably better to install the latest drivers known as serialmonkey legacy drivers.  You will need to download, compile, and install these drivers (which isnt a big deal!!).

The best thread I can point you to is a thread entitled HowTo: Serial Monkey rt73.  The author is deprius.  You will have to search for this thread.  He references the rt73 chipset, however the entire process will work for you, except for the fact that were "73" is referenced you need to substitute "63".

Find the thread -- its excellent and well written.

---

