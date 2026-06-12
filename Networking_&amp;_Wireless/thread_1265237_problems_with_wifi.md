---
title: "problems with wifi"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by MOHASHU on 2009-09-13
hi. i am a still new at using linux and im still trying to get the hang of it. i was trying to install madwifi drivers for my chipset so as to configure its wifi but all in vain. i have read many posts in this forum and googled many sites but still no progress i dont know if i can get any help here. i was following the "madwifi firsttime how to"
[U]step 1
[/U]$ sudo apt-get install build essential[U]
output
[/U]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build
[U]step 2
[/U]$ ifconfig ath0 down or $ config wifi0 down
_output_
ath0: ERROR while getting interface flags: No such devicewifi0: ERROR while getting interface flags: No such device[U]
step3 
[/U]abdullahi@ubuntu:~/Desktop/madwifi/scripts$ ./madwifi-unload[U]
output
[/U]bash: ./madwifi-unload: No such file or directory
_step4_
abdullahi@ubuntu:~/Desktop/madwifi$ sudo make
_output_
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/abdullahi/Desktop/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.o
/home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/abdullahi/Desktop/madwifi/net80211] Error 2
make[1]: *** [_module_/home/abdullahi/Desktop/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2
[U]
step 6[/U]
abdullahi@ubuntu:~/Desktop/madwifi$ make install
_output_
sh scripts/find-madwifi-modules.sh 2.6.28-11-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
        make -C $i install || exit 1; \
    done
make[1]: Entering directory `/home/abdullahi/Desktop/madwifi/ath'
test -d //lib/modules/2.6.28-11-generic/net || mkdir -p //lib/modules/2.6.28-11-generic/net
install ath_pci.ko //lib/modules/2.6.28-11-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/abdullahi/Desktop/madwifi/ath'
make: *** [install-modules] Error 1
abdullahi@ubuntu:~/Desktop/madwifi$ abdullahi@ubuntu:~/Desktop/madwifi$ make install
bash: abdullahi@ubuntu:~/Desktop/madwifi$: No such file or directory
abdullahi@ubuntu:~/Desktop/madwifi$ 
_ step 7_
abdullahi@ubuntu:~/Desktop/madwifi$ modprobe ath_pci
_output_
WARNING: Could not open '/lib/modules/2.6.28-11-generic/volatile/ath_hal.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-11-generic/volatile/wlan.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.28-11-generic/volatile/ath_pci.ko': No such file or directory


i know i am definitely doing something wrong or i am missing something. will really appreciate if someone can point me in the right direction and tell me what i am doing wrong. thank you for taking your time reading my long question thread.:)

---

### Post by chili555 on 2009-09-13
You will never successfully complete steps 2-7 until you fix step 1. Whenever you encounter an error, stop and fix it because all subsequent steps *will* fail.> step 1
$ sudo apt-get install build essential
output
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package buildThe name of the package is build[COLOR="Red"]-[/COLOR]essential.

---

### Post by MOHASHU on 2009-09-15
> **chili555 said:**
> You will never successfully complete steps 2-7 until you fix step 1. Whenever you encounter an error, stop and fix it because all subsequent steps *will* fail.The name of the package is build[COLOR="Red"]-[/COLOR]essential.
THANKS CHILLI555. will tryit and give you feedback.

---

### Post by chili555 on 2009-09-15
If you get stuck on subsequent steps, post back and we'll do our best to get you going.

---

### Post by MOHASHU on 2009-09-18
Hi. thanks for all your support. i managed to get one error fixed. thanks . the build-essential worked. 
step2 though also generated errors..as follows
_command_
abdullahi@ubuntu:~$ cd Desktop
abdullahi@ubuntu:~/Desktop$ cd Madwifi
bash: cd: Madwifi: No such file or directory
abdullahi@ubuntu:~/Desktop$ cd madwifi
abdullahi@ubuntu:~/Desktop/madwifi$ cd scripts
abdullahi@ubuntu:~/Desktop/madwifi/scripts$ ./madwifi unload
bash: ./madwifi: No such file or directory
abdullahi@ubuntu:~/Desktop/madwifi/scripts$ cd ..
abdullahi@ubuntu:~/Desktop/madwifi$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/abdullahi/Desktop/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
/bin/sh: cannot create /home/abdullahi/Desktop/madwifi/ath/modules.order: Permission denied
make[3]: *** [/home/abdullahi/Desktop/madwifi/ath/modules.order] Error 2
make[2]: *** [/home/abdullahi/Desktop/madwifi/ath] Error 2
make[1]: *** [_module_/home/abdullahi/Desktop/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2
abdullahi@ubuntu:~/Desktop/madwifi$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/abdullahi/Desktop/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.o
/home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/abdullahi/Desktop/madwifi/net80211] Error 2
make[1]: *** [_module_/home/abdullahi/Desktop/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2
abdullahi@ubuntu:~/Desktop/madwifi$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.28-11-generic 

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
        make -C $i install || exit 1; \
    done
make[1]: Entering directory `/home/abdullahi/Desktop/madwifi/ath'
test -d //lib/modules/2.6.28-11-generic/net || mkdir -p //lib/modules/2.6.28-11-generic/net
install ath_pci.ko //lib/modules/2.6.28-11-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/abdullahi/Desktop/madwifi/ath'
make: *** [install-modules] Error 1
abdullahi@ubuntu:~/Desktop/madwifi$ cd scripts
abdullahi@ubuntu:~/Desktop/madwifi/scripts$ ./madwifi unload
bash: ./madwifi: No such file or directory
abdullahi@ubuntu:~/Desktop/madwifi/scripts$ ls
find-madwifi-modules.sh  get_arch.mk  madwifi-unload.bash  make-release.bash
abdullahi@ubuntu:~/Desktop/madwifi/scripts$ ./madwifi-unload
bash: ./madwifi-unload: No such file or directory
abdullahi@ubuntu:~/Desktop/madwifi/scripts$ sudo makae
sudo: makae: command not found
abdullahi@ubuntu:~/Desktop/madwifi/scripts$ sudo make
make: *** No targets specified and no makefile found.  Stop.
abdullahi@ubuntu:~/Desktop/madwifi/scripts$ cd ..
abdullahi@ubuntu:~/Desktop/madwifi$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/abdullahi/Desktop/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.o
/home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/abdullahi/Desktop/madwifi/net80211] Error 2
make[1]: *** [_module_/home/abdullahi/Desktop/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2

its a bit long. i really appreciate your help. plz assist me to get through. its a bit frustrating.thanks.

---

### Post by chili555 on 2009-09-19
I'm sorry, but my talent, if I have any, ran out right about here:> /home/abdullahi/Desktop/madwifi/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':Can you give me a link to download the package you are trying to build so I can try it on my machine, please?

---

### Post by MOHASHU on 2009-09-24
Thanks chilli. But im not sure where i downloaded it.anyway, really appreciate u taking ur time n thanks for your help. Dont know what i will do ...

---

