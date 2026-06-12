---
title: "Madwifi installation problem"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by sakibd2k on 2009-07-02
Hi all,

I am using Ubuntu 4.3.2 on toshiba laptop A135 which has wireless NIC chipset of atheros AR242x.
       
I  install kismet and aircrack-ng but cannot run kismet it shows error as i dont have
driver for this wireless nic to go rf Monitor mode. I recognized that mine not supporting as monitor mode by following error message.

mushfiq@mushfiq-laptop:~$ sudo kismet
[sudo] password for mushfiq: 
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.


So  i went to install madwifi-0.9.4  which i found to be latest or downloadable.

while installing this madwifi driver after issuing command 
make       there was 2 error

---------------------------------------------
-----------------------------------------------
make[3]: *** [/home/mushfiq/Desktop/madwifi/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/mushfiq/Desktop/madwifi/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/mushfiq/Desktop/madwifi/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

and after make install  command it says

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

How is there already madwifi but not in monitor mode?
Can anyone help me and guide to run kismet, aircrack-ng and airsnort in ubuntu
by installing a driver for monitor mode  after all this have been done?
Please give a guide line,  if any more information require please also tell me

Mushfiq

---

### Post by oaxacamatt1 on 2009-07-09
Yo,
I am geting this same type of error messages when I tried to build the madwifi drivers from madwifi-0.9.4.

Did you ever figure it out and get a solution?
Cheers,
Matt


-----------------------------------------------
make[3]: *** [/home/mushfiq/Desktop/madwifi/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/mushfiq/Desktop/madwifi/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/mushfiq/Desktop/madwifi/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

---

### Post by Bohemenian on 2009-08-18
Can't confirm that's my exact error, but it's something like that, and I'd love to see some help with this. 
Anyone with the knowledge around?

---

### Post by chili555 on 2009-08-21
@sakibd2k

There is nothing you have posted that suggests your driver will not go into monitor mode. The essential issue is this:> FATAL: Please configure at least one packet source. Kismet will not function if no packet sources are defined in kismet.conf or on the command line. Please read the README for more information about configuring Kismet.Did you read the README?

Perhaps this post will help:  [http://ubuntuforums.org/showpost.php?p=7085522&postcount=6](http://ubuntuforums.org/showpost.php?p=7085522&postcount=6)

I suggest you correct this and re-run kismet to see if you have an error.

Also, if you get an error at 'make' there is no reason to proceed to 'sudo make install.' It will never work.

---

### Post by Bohemenian on 2009-08-22
Ok, turns out I didn't really need Madwifi, but the default ath9k worked the way I wanted it to. Thanks for your reply, though.

---

### Post by Cuba71 on 2009-08-22
I have same A135 with same card and it works great with native ath5k driver

---

