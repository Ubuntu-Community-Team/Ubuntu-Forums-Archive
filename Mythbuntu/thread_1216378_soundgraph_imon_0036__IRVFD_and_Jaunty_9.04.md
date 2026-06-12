---
title: "soundgraph imon 0036  IR/VFD and Jaunty 9.04"
date: 2009-07-18
forum: Mythbuntu
---

### Post by stowaway on 2009-07-18
I have been trying to get this vfd for awhile.. I followed the instructions as outlined here:
[http://ubuntuforums.org/showthread.php?t=1041258&highlight=mode2&page=3](http://ubuntuforums.org/showthread.php?t=1041258&highlight=mode2&page=3)

Excuse my ignorance im a noob to linux.
I have installed Myhtbuntu 9.04 I have IR/VD 15c2:0036.
I choose soundgraph Imon PAD IR/VFD for my remote during install.
I have a fresh install of mythbuntu. no extra programs installed yet


Quote:
Originally Posted by joshoekstra  
Now it's even easier, still not out-of-the-box but still doable:
apt-get install lirc-modules-source with requisites, 

with requisites?

I did:
apt-get install lirc-modules-source 
i hope that will include requeistes?


Quote:
Originally Posted by joshoekstra  
download this lirc_imon.c which is the 1.33 of the imon-driver and place it in /usr/src/lirc-0.8.4a/driver/lirc_imon instead of the original one. 

done!
sudo cp lirc_imon.c /usr/src/lirc-0.8.4a/driver/lirc_imon


Quote:
Originally Posted by joshoekstra  
Then try sudo dpkg-reconfigure lirc-modules-source, it will rebuild the modules.  

easy enough?
dpkg-reconfigure lirc-modules-source
done!


Quote:
Originally Posted by joshoekstra  
After that stop lircd and lcdproc(/etinit.d/lirc[LCDd] stop)  

a bit confused?
michael@MediaPC:/usr/src/lirc-0.8.4a/drivers/lirc_imon$ sudo lircd stop
lircd: there seems to already be a lircd process with pid 2840
lircd: otherwise delete stale lockfile /var/run/lircd.pid

deleted that file..
I dont have lcdproc installed.. dont care about the VFD.. let me know if this is essential?


Quote:
Originally Posted by joshoekstra  
and sudo rmmod lirc_imon lirc_dev,  

michael@MediaPC:/var/run$ sudo rmmod lirc_imon lirc_dev

(just went to next line. no response)


Quote:
Originally Posted by joshoekstra  
reload module with sudo modprobe lirc_imon. Check in dmesg if the version number is 0.5. 

michael@MediaPC:/var/run$ sudo modprobe lirc_imon
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
michael@MediaPC:/var/run$ 

??

I now seem to have LCD0 LCD1 LIRC0 LIRC1 in my /dev folder so this is good news.
I untared the conf files and copied them to the /etc/init.d and /etc/lirc

Still get no response from my remote in mythtv tho? not sure where to go from here?
i should mention i dont have the original remote. i use a logitech unversal remote. i have loaded antec fusion 480 remote into it tho.. I also loaded mce remote just to test.. 
Any help is much appreciated!

---

