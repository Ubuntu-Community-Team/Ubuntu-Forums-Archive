---
title: "HP Pavilion g6 wireless drivers suddenly unrecognized"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by sixela295 on 2011-08-23
I have a HP Pavilion g6. It comes with a button on f12 that toggles the wireless on/ff. I've been running natty on it for about 2, maybe 3 months, and had to configure my wireless drivers upon installation. However, after installing updates recommended by update manager last night, my laptop now neither recognizes the f12 key's toggle action, nor does it seem to recognize the fact that I have any wireless hardware, despite a few restarts/shut downs.
2 things:
1) Did anyone else experience this after installing updates? I haven't had internet access since the 18th, so it's not necessarily something that was released yesterday. If not, what could have possibly happened to cause this?
2) What do I do? I can't remember what I did to configure it.

Wireless Controller: Ralink corp. Device 5390

---

### Post by sixela295 on 2011-08-23
Also, I just tried the tutorials on [http://admaris.com/wp/blog/2011/07/03/ubuntu-on-hp-g6-laptop-tales-from-the-grave/](http://admaris.com/wp/blog/2011/07/03/ubuntu-on-hp-g6-laptop-tales-from-the-grave/) and [http://askubuntu.com/questions/51351/wireless-not-detected-on-an-hp-pavilion-g6](http://askubuntu.com/questions/51351/wireless-not-detected-on-an-hp-pavilion-g6), but neither of them are working. I have neither the HAS_ANTENNA_DIVERSITY_SUPPORT nor the HAS_CFG80211_SUPPORT lines in the config.mk file downloaded from ralinktech.com

---

### Post by praseodym on 2011-08-23
You may compile the driver again because of the kernel upgrade. You dont need "ANTENNA_DiVERSITY" etc., only WPA_Supplicant and Networkmanager support has to be changed to "y"

---

### Post by sixela295 on 2011-08-23
Thanks. I just changed them both, but I'm still getting errors. Is this the right command? Also, I'm using 64-bit, if that's any help.

sixela@chantillylace:~/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ make
make -C tools
make[1]: Entering directory `/home/sixela/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/sixela/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/sixela/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/sixela/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-11-generic-pae/build SUBDIRS=/home/sixela/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
rm: cannot remove `/home/sixela/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/.tmp_versions/rt5390sta.mod': Permission denied
make[1]: *** [crmodverdir] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
make: *** [LINUX] Error 2

---

### Post by praseodym on 2011-08-23
Permission denied means you need "sudo make" or the old-fashioned "root"-mode:

```

sudo su
make
make install
exit

```

---

### Post by sixela295 on 2011-08-23
sudo make worked. Thank you so much!

---

### Post by praseodym on 2011-08-23
Great

You can edit the thread title to mark it "solved"

---

### Post by xpiky28 on 2012-01-04
Hi I have the exact same computer running on Windows 7 and the same problem, it comes and goes, I dont undestand since reply #2 I have to download something?? Can you please make me a simple list of how to solve this. Please!!

---

