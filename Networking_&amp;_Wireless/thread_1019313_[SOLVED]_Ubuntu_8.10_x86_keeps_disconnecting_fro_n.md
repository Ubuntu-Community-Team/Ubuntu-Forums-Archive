---
title: "[SOLVED] Ubuntu 8.10 x86 keeps disconnecting fro network"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by swoody on 2008-12-23
Well I have a 64bit 8.10 machine that continually drops the network connection. It worked fine as the 32bit version, but then I reinstalled my OS as the 64bit version, and now it's buggy. It won't even stay connected long enough for me to run the update-manager. Also, when it drops the connection I have to reboot the computer to be able to reconnect to the network. My wireless card is an Atheros AR5800. Any and all help is GREATLY appreciated! Thank you all :)

---

### Post by superprash2003 on 2008-12-23
post output of
ifconfig
iwconfig

 when you face the disconnection...

---

### Post by daneck on 2008-12-29
I'll be watching this one.  I've got the same problem, except it's my wired connection that keeps dropping.  I did 2 clean installs with 64bit version with the same outcome.  I've got another box with the 32bit Server installed with no problems at all, so I'm thinking the same thing you are...64bit version is buggy. MCP55 nVidia (on-board) on an Asus M2NBP-VM CSM.

---

### Post by swoody on 2008-12-31
Sorry, but I have had other problems as well with the 64bit version, and after rebooting the computer a couple times my entire installation gets to the point that it won't boot up, so I'll be staying with the 32bit version for some time now :)

---

### Post by daneck on 2009-01-01
I'm still sticking with the 64bit version.  I thought my problem was mysteriously solved, but then I turned on an XP box that a DWA-160 USB N-Wireless adapter is used to connect to my DIR-655 router...Started to get the constent disconnects on my Ubuntu 8.10 box that is connected via wired LAN.  Once I removed the wireless adapter from the XP box my connection stays solid.  Looks like the problem is either with the router or the adapter, or a combination of the two.

Once I figure out what the problem is I'll post my findings.  I reinstalled the nVidia drivers and still no problems, so at this point I'd have to give Ubuntu 65bit and the nVidia drivers a clean bill of health.

Hope everyone has a safe and happy new year!

daneck

---

### Post by cbl016 on 2009-01-22
Hey daneck did you ever figure this out? 

I too am having a similar problem. I have a power mac g5 with ubuntu 8.04 installed on it. This machine constantly gets disconnected from the network. I also have a windows vista laptop on the same network. 

I installed wicd because I thought it might help but it actually made it worse. With Network Manager my computer would automatically reconnect to the network but with wicd it gets disconnected and I have to manually click on the connect button to get it to reconnect to the network.

---

### Post by daneck on 2009-01-25
Sorry for the delay in getting back to this thread, but it's been a rather busy few weeks.

It turns out the the problem (for me at least) is all the extra software installed with the DWA-160 USB N-Wireless adapter.  Initially I didn't give it any thought, and figured that the features of the network monitoring stuff would be nice on the wife's PC.  However, while going through a checklist for doing a 'clean' reinstall of the adapter one of the steps is to turn off the wireless security features in the program.  Turns out that it never was inabled, and the DIR-655 router isn't supported with the DLINK adapter's included software (sounds like somethink out of a Microsoft novel).

I don't have any Macs on the network, but my guess would be that DLINK installs the extra software for the Macs also.

Once I uninstalled everything and did a reboot I reinstalled the drivers ONLY.  I am allowing XP to manage the wireless connections, and so far (knock on wood) I've been up and running for about 2 weeks with zero connectivity problems both for the wireless and the wired connections.

My 'guess' is that the security features on the DLINK included software package was sending some kind of signal to the router causing it to reset every 10 minutes. The constent resetting of the router would explain the wired network disconnects also.

Good luck, and please let us know if you get your problem resolved by uninstalling any extra software.  I'm sure there are others that will run into this type of problem and not even think that an XP box would cause problems for Linux/Unix boxes on the network.

Later Days!

---

### Post by cbl016 on 2009-01-26
I too was able to solve my network disconnects. It turns out that even with active programs running, my computer was trying to go to sleep. It would go down for a second and then it would come right back up again. This would cause the machine to disconnect from the network. With Network Manager it would reconnect but with wicd it would stay disconnected.

I simply set the computer to never go to sleep and so far I haven't had any more problems. 

It was a simple solution but it took me a while to figure out because I never thought my computer would be going to sleep with running programs.

---

