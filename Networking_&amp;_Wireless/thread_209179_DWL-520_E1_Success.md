---
title: "DWL-520 E1 Success"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by thehotshxt on 2006-07-04
After working for 2 days to get my wireless DWL-520 Rev E1 up and running, I tried several methods to no avail.

first:
[http://ubuntuforums.org/showthread.php?t=198568](http://ubuntuforums.org/showthread.php?t=198568) did not help because it would not actually attach to my card, it installed the hostap drivers, and i found the firmware as described in the wiki and edited the /etc/network/interfaces to provide the address of the firmware, but dmesg | grep wlan0 kept giving me errors about "no PRI f/w"  i even downloaded the alternate firmware rf010803 as i saw elsewhere as a solution.  so after buggering around this way to no avail, i decided to try ndiswrapper.

second:
ndiswrapper... ahh, such a beautiful workaround that with the version 1.8 driver caused it to freeze my system completely everytime i specified my ESSID, or went into the GUI to configure the network there.

so the successful way:
first i added to /etc/modprobe.d/blacklist 
    blacklist hostap_pci
in addition to the other 3 that were blacklisted from the above article

i installed the headers and all additional files that i needed to install ndiswrapper 1.19 (newest stable as of July 1 on sourceforge) after "sudo ndiswrapper -e netprism"-ing the old wrap.

i then:
sudo ndiswrapper -i /home/myname/dlink/NETPRISM.inf  
[i put all the xp drivers in that directory]
[i then edited the /etc/network/interfaces to include:
        auto wlan1
        iface wlan1 inet dhcp
        wireless-essid myhomenetwork
]
sudo modprobe ndiswrapper

then:
sudo ndiswrapper -m

i'm not sure if there is anything left behind that i should clean up?  doing an iwconfig only shows wlan1 (with the hostap drivers it was showing 2 other interfaces, wifi0 and wlan0 which are not here anymore)?

i'm sending this post as the first thing i did after getting it up and running, i hope it may help others, but if anyone knows if i need to clean anything up to keep things 'tidy', let me know.

cheers

---

### Post by greenwom on 2006-07-13
are you wrappering netprism.inf or the XP drivers?

I had my E1 working under the wiki with Dapper and then it stopped working after a new kernel upgrade and a samba server install // after reboot it stopped working.

no Pri FW errors and "Mac port enabling errors"  

I'm kind of stucl on the box with out a connection

---

### Post by thehotshxt on 2006-07-13
actually with the newest kernel update, mine had stopped working as well, i just reverted back and was just now going to give it another shot... will let you know how it goes.  :)

---

### Post by thehotshxt on 2006-07-13
but yes, i was wrappering the netprism.ini file from the XP directory of the E1 driver archive.

netprism.ini
prismnds.sys
and
prismnic.cat 

were the files i required.

---

### Post by thehotshxt on 2006-07-13
success.  kernel 2.6.15-26-386.

i updated ndiswrapper to 1.20rc1 from the sourceforge page, then:

> sudo modprobe ndiswrapper

> sudo modprobe -l still showed netprism

and i just sent this, so it's working.

funny that you asked about the driver though, cause now i'm not 100% sure if i used the xp driver or if i used the root driver.  i'm not about to break something that is working, so... you tell me :)

---

### Post by greenwom on 2006-07-13
did yo uhave any special dependancies with the new ndiswrapper?  I have to download and burn so as not to move the big rig..

---

### Post by thehotshxt on 2006-07-14
no special dependencies that i know of... i just downloaded the source, sudo make, sudo make install and that was it..

---

### Post by stupidkid on 2006-12-22
Nice, thanks for this. I was about to give up until I remembered to try a newer version of ndiswrapper.

---

