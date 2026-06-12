---
title: "wireless connetion on Inspiron E1505."
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by cjjoy1980 on 2010-01-23
Hi 
  I have installed karmic on my inspiron E1505.  Everything is working fine except the wireless connectivity. 

 I have been following the below thread for getting wireless to work. I am stuck at step -3 (compiling - DISWRAPPER) .

  [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)


Getting the below compilation error:

root@cp:/home/cp/wireless/ndiswrapper-1.55# make distclean
make -C driver clean
make[1]: Entering directory `/home/cp/wireless/ndiswrapper-1.55/driver'
rm -f *.o *.ko .*.cmd *.mod.c *.symvers modules.order *~ .\#*
rm -f *_exports.h win2lin_stubs.h
rm -rf .tmp_versions
make[1]: Leaving directory `/home/cp/wireless/ndiswrapper-1.55/driver'
make -C utils clean
make[1]: Entering directory `/home/cp/wireless/ndiswrapper-1.55/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/cp/wireless/ndiswrapper-1.55/utils'
rm -f *~
rm -fr ndiswrapper-1.55 ndiswrapper-1.55.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/cp/wireless/ndiswrapper-1.55/driver'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/cp/wireless/ndiswrapper-1.55/driver'
make: *** [distclean] Error 2


can please anyone help me in this who has installed it. 

Thanks

---

### Post by cjjoy1980 on 2010-01-24
I realised that ubuntu repository has ndiswrapper.

Installed it using the below command:
aptitude install ndisgtk

Was also able to install my wireless driver. 

I install wifi-radar as my Network manager.  I can see the wifi connections but cannot connect to it.. 


I get this error when i try to connect

Error for wireless request "Set Encode" (8B2A) :
    invalid argument "WEP".
2010-01-24 10:56:31,974: connect_to_network: DHCP client not found, please set this in the preferences.
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1525, in connect_profile
    self.connection.connect_to_network(profile, self.status_window)
  File "/usr/sbin/wifi-radar", line 472, in connect_to_network
    waiting = dhcp_proc.poll()
UnboundLocalError: local variable 'dhcp_proc' referenced before assignment


Any suggestions please..

---

### Post by Black Kelpie on 2010-02-11
*bump*
I have the same problem on my desktop running 9.10 on D-Link. Keeps coming bakc with "essid:off/any" and AP:no associated". Any help would be appreciated.

---

