---
title: "post karmic wireless issues all solved"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by cybergalvez on 2009-11-02
All my wireless issues have been fixed! After installing Karmic my Atheros wireless stopped working.  looking around, madwifi is no longer needed as ath5k is in the restricted kernel.

looked in the various blacklist files and sure enough ath5k was blacklisted (most likely by madwifi when I originally installed it).
rebooted and nothing still no wifi, so I added ath5k to the end of /etc/modules rebooted and now network manager sees my wireless and I can connect to the Internet.  Only problem is its does not connect until after I've logged in.  I have a shared printer connected to this computer so it needs to have the network connect when the computer turns on, which I was able to do by editing the /etc/network/interfaces file prior to karmic. Now that no longer seems to work.  
Installed wicd (followed these instructions [http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu](http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu)) set up the wireless connection and Wow now it just works! 
wicd is fantstic, works much better then network manager! and it connects when the computer boots!

---

### Post by david.m.bailey on 2009-11-04
How do you find this "blacklist"?  I am new to Ubuntu and have never tried the Terminal or command line for anything.  I hate to say it, but it would probably be an undertaking for me to find THAT let alone manipulate it!
 
Thanks!

---

### Post by cybergalvez on 2009-11-04
look in /etc/modprobe.d there are several files there are several blacklist files there, just look through them

---

### Post by fevemo on 2010-02-28
I enter etc/modprobe.d and I see something called blacklist-ath_pci.conf i can open it but I dont know how to delete it or edit it because it it read only, the same thing happens when I try to ad ath5k ad the end of modules, could someone help (I'm new to ubuntu)

---

### Post by bkratz on 2010-02-28
Look at this post, he is doing somewhat the same thing (it does require the terminal though).


[http://ubuntuforums.org/showpost.php?p=8896751&postcount=3](http://ubuntuforums.org/showpost.php?p=8896751&postcount=3)

---

