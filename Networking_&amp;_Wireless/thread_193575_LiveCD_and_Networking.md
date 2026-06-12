---
title: "LiveCD and Networking"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by Anophele on 2006-06-10
Do someone know why do the hell casper with the 23Networking script in /usr/share/initramfs-tools/casper/scripts/casper-bottom erase /etc/network/interfaces settings for l0, eth0,eth1,eth2, ath0 and wlan0 at boot ? 

Thanks for help

---

### Post by Anophele on 2006-06-10
To be more specific i had some pieces of information which were lacking in my firs post 

- i use -persitent switch in the boot command line to activate the persistence feature and the custom settings are saved in a USB stick (w/o that my question is meaningless) 
- as far as i know so far this feature works for i see Desktop settings, files saved in /home/... zone well restored. 
- but Network settings are not  
-/etc/network/ is restored for there is old interfaces~ file, but actual interfaces file is erased (superseeded) to default settings by ...
-/usr/share/initramfs-tools/scripts/casper-bottom/23networking (as far as i understand)  at the very moment when the message "Preconfiguring networking...." is displayed at boot
-my hardware is well detected, at least for eth0, before that moment. I add this precision for i read in /usr/share/doc/casper/changelog 

quote
asper (1.48) dapper; urgency=low

  * Write /etc/network/interfaces entries for eth0, eth1, eth2, ath0 and
    wlan0 if there's no hardware detected for them; as it may be plugged
    in after boot.

 -- Scott James Remnant <scott@ubuntu.com>  Wed, 26 Apr 2006 12:31:38 +0100
/quote

---

### Post by Anophele on 2006-06-15
LiveCD...   (Wireless) Networking... and boot speed up 

To close that case i answer myself and write down the way i found to get it working to be read by whom it might help.

The context doesn't appear in the former posts, the question was more specific, but here it is : my goal was to use a secured wireless connection from my Latop to my AP (like many).The wireless adapter is a Linksys PCMCIA WPC54G(S) and, less important the Latop a Dell D610. 

But the tricky part was to make it working using a LiveCD with the persistent feature on in order to get reconnected at each boot of the LiveCD. 

So i read the wiki pages corresponding to my problems : 

 [https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide](https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide)

   very usefull to understand the whole background of the issue 
 
 [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

  where i found how to get rid of and blacklist native Linux Bcm43xx driver

 [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

  in order to use the closed source Linksys Driver 
 
 [https://wiki.ubuntu.com/WifiDocs/WPAHowTo](https://wiki.ubuntu.com/WifiDocs/WPAHowTo)

 and /usr/share/doc/wpa_supplicant/README.modes
 
  in order to secure the wireless connection 


I won't explain the whole process (details are in the above documents) but only the "workarounds" i used in my case. 

As a start after booting from a clean LiveCD (with persistent parameter) i applied the steps (choose the relevant ones !!!) in the above documents and succeded to connect.

For the security side i used both wpa_supplicant modes (read /usr/share/doc/wpa_supplicant/README.modes) both working, but as in in Dapper /etc/wpa_supplicant/ and wpa_suppliant.conf are not provided the first mode is quite obsolete. So i put wpa configuration parameters in /etc/network/interfaces (second mode). 


BUT, at each following boot, no connection.

Was it a security problem ?, a wireless power problem ?, ... etc ...   
   
I finally found  that /etc/network/interfaces was each time reset to default settings : 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


instead of being restored by persistence, and a great part of my tuning was lost. 

To understand I digged into the boot process to find the cause which turned to be /usr/share/initramfs-tools/casper/scripts/casper-bottom/23networking. 

So I posted my question. Thanks for the answers !!!

Meanwhile i looked for a solution, read more documents and posts about Live Debian, networking problems (numerous) in Dapper's recent spead ...

I still don't understand what is the use of the above script. Seems it a been added or more precisely modified to prevent a stall situation at boot in some cases (in mine it spoil my settings). I didn't find a way to get rid of it or of its execution for it is called quite early (by casper and/or initramfs) when no later coming (resorded) tuning seem to be effective yet. But in this case my settings should be restored too. Why r'nt they ? 

Maybe someone could explain what is the actual order of the boot and what come first : casper scripts execution or persitence settings restore ??? 

A way would have been to Remaster the LiveCD (there are posts about that), "unsquashing" the filesystem , tuning , "resquashing" ... too hard for me. 

So to solve the problem i wrote a script called /etc/init.d/networkingO mainly a copy /etc/init.d/networking where calls to ifdown are replaced by a backup (simple cp) of /etc/network/interfaces to /etc/network/interfaces0 and all calls to ifup by a restore of /etc/network/interfaces0 to /etc/network/interfaces. 

With the add of links to the script : S39networking0 in rcS.d  S36networking0 in rc0.d and rc6.d, it is called a startup with a start parameter to restore the /etc/network/interfaces before the interfaces are configured by /etc/init.d/networking start, and called at shutdown with a stop parameter to save /etc/network/interfaces after the interfaces have been stoped by /etc/init.d/networking stop.    

It should have worked, but have not completly. I do not describe the whole process of finding why, but it turned out that interfaces network are "wake up" earlier than expected (S40networking) by S10udev (hotplug hardware ?) with false parameters (not yet restored), which screw up later call to ifup by S40networking. The corresponding slight correction was to move S39networking0 to S09networking to restore /etc/network/interfaces before first use.

And that's it ! 


Network connection is restored at boot and there is no more pause due to unanswered dhcp requests timeouts.



While reading a bit more it appeared to me that the general evolution of the OS, made the use of /etc/networking/interfaces more and depreciated. A lot of network (and other) problems seemed to be caused by these different ways of dealing with the configuration from a version to another, and no maintained backward compatibility (like erasing a important file former versions rely on !!!)  

So i reluctantly looked toward Network Manager. In a same system 3 ways (files, (gksu)network-admim, NetworkManager) to configure wireless networks... how could that work ??? 

It turned out to DONT work, together i mean. NetworkManager prevents himself from managing wireless interfaces (no wifi right-click menu) when wireless parameters are set in /etc/network/interfaces directly or by network-admin. 

With a clean /etc/network/interfaces regarding wireless settings (and in network-admin), NetworkManager takes care ofyour Wlans. But you got to type your password each time you connect which one can love or not. 


So to put it in a nutshell, in a case similar to mine you've got two solutions :

1) Rely on scripts with the correction explain above to get connected directly at boot. 

2) Rely on GUI with Network Manager for instance, to connect on a per session basis, and in this case you should clear /etc/interfaces/network and even remove calls to /etc/init.d/networking scriptto prevent the network from being called up to early with dummy parameters causing pauses in boot.     


HTH

---

