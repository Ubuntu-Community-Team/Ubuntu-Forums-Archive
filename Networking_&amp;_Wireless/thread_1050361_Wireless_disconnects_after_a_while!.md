---
title: "Wireless disconnects after a while!"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by BazookaAce on 2009-01-25
Hi, 

I'm using Ubuntu 8.10, and my wireless network is disconnecting by itself all the time. Let's take an example: 

I'm surfing the web and it's been fine a couple of days, then BAM! the connection shuts down without any warning. The wireless is still working cause my mobilephone is capable to access the internet. Anyway, when the wireless dies, the computer starts cramping and things starting to slow down, and i can't re-connect. My only option is to shut down the computer, take out the battery, and start all over again. 

This is VERY anoying! My wireless network is an open network since i removed the security, since (again) i had other problems with the network. 

I'm using an Acer Aspire One A150, and i've installed madWifi. 

So! What to do?

---

### Post by Post Monkeh on 2009-01-25
i'd been having the same problem with my laptop (an asus x58l)

i found installing wicd and removing network manager to help a little.  it still disconnects occasionally but it's a lot less often than with network manager

---

### Post by Quarg on 2009-01-25
I use ath5k on my compaq with an atheros card, and it works great. don't really like madwifi.

---

### Post by kevdog on 2009-01-25
I'd first check the system logs to see whether a problem is documented.  I wouldn't jump to conclusions right away that it is a wireless problem.  Wireless might be the first symptom of the problem, not the problem itself.

---

### Post by BazookaAce on 2009-01-25
OK. So here's something that might help: 

**iwconfig:**

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NextGenTel_3E"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:07:00:CC:3D   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-46 dBm  Noise level=-96 dBm
          Rx invalid nwid:265467  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


**System Log: ** (I think it's this?)

Jan 25 13:50:53 steffen-laptop gdm[5384]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.
Jan 25 13:50:53 steffen-laptop gdm[5384]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.
Jan 25 13:50:53 steffen-laptop gdm[5384]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.


edit: LOL, the smileys isn't my work :p

---

### Post by kevdog on 2009-01-25
Seems like a gnome-keyring/Dbus/Network Manager issue.  A few things you could try would be:
1. Temporarily make a manual connection from the command line, that would bypass network manager altogether (temporarily)
2. If #1 works, try WICD instead of network manager to control your wireless connections.

---

### Post by BazookaAce on 2009-01-25
Okay, i'll try that! Thank you so much for helping! :D

Edit: Where's the "Thread solved" thingy again? Can't find it :p

---

### Post by kevdog on 2009-01-26
Not sure the thread is solved?

---

### Post by BazookaAce on 2009-01-26
I don't know? Haha :p I haven't tried your solution yet, but i'll try it a i bit later today :)

---

### Post by KayakJim on 2010-01-03
I'm using 9.04 desktop 64-bit and am having the same problem. I notice that while on FaceBook the disconnects happen more often than if I am on other sites.

After a few attempts to reconnect the network manager just completely quits trying and I have to restart in order to obtain a connection again.

In 8.10 and 9.04 32-bit I never had a problem with my wireless. It is only since moving to the 64-bit version.

---

