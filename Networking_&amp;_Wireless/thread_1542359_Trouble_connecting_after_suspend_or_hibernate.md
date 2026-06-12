---
title: "Trouble connecting after suspend or hibernate"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by Aisteru on 2010-07-30
I have had trouble connecting to wifi after suspending or hibernating. 

I avoided the problem by simply not using hibernate, but I do not like having such a nifty feature unusable.

I tried some suggestions I read on the forums, (disabling networking before hibernating, others I think, I do not remember what now) but nothing I tried worked, until I tried wicd. It seemed to connect when gnome network manager would not. I un-installed gnome network manager, but then wicd would fail to connect, with an error of one kind or another (bad password or unable to obtain ip address). 

After getting unduly grouchy, I plugged in a cat5 cable & was, after a restart or two, able to reinstall gnome network manager. 

Now, if i try to connect with both at once after hibernating, it works. I think there should be another solution, but do not yet know enough to figure it out myself. 

My relevant specs are:

Ubuntu 10.04
hp g60-443cl laptop
Artheos AR928X Wireless Network Adapter


Any help would be much appreciated, thank you.

---

### Post by Aisteru on 2010-10-29
Bump!

---

### Post by macem29 on 2010-10-29
no help unfortunatly, but I have the same issue, also Atheros wireless, WICD installed and scanned fine, continuous bad password error when connecting, back to gnome manager, buggy, but can connect, and suspend or hibernate kill connectivity, hard reboot required to get connected again, luckily the pc boots to a usable state in 30 seconds or this would be a real nuisance...gave up messing with it as it seemed to create more issues and never fixed that one, hopefully it will be addressed in an update...10.04 gnome desktop

---

### Post by not_a_phd on 2010-10-29
Same issue and symptoms on a eee901 running 10.10. Really interesting symptoms:
   -When running generic rt2800 and rt2x00 drivers, system would 
    connect and reconnect after suspend to WEP network.
   -Running those same drivers, system would *not* connect to WPA 
    network.
   -After blacklisting rt2800 and rt2x00 drivers, system would 
    connect to WPA network with rt2860sta driver, but would not
    reawaken after suspend, and would not connect to a WEP network.

Had to compile and install vendor ra2860sta driver to get single
driver configuration to connect to WEP (and hopefully WPA - haven't
tested yet). 

With vendor driver, system will not resume connection after suspend. I am looking for the forum HOWTO that describes how to 
script a driver shutdown before suspend...

---

### Post by walt.smith1960 on 2010-10-29
I'm having the same problem with a NetGear WNA1100 USB. WiFi is working perfectly when I suspend.  On resuming there's no sign of life from the adapter even though "enable networking" & "enable wireless" are both checked in Network Manager. Doing a network restart seems to have no effect.  I've just started disabling networking before suspending.  I have only gone through 6 or so cycles so it's too early to declare victory but so far I can reconnect without a system restart. What I find interesting is I un-check "enable networking" prior to suspending.  When I unsuspend, the WiFi connection reconnects without my checking "enable networking".  I've also had Network Manager de-select "enable networking" for no apparent reason.  I wonder if these behaviors are related?  I think making disable networking part of the suspend process will help with this problem.  I don't know how to do that, however.

---

### Post by dineshs on 2010-10-30
Have you tried
[http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)
(postcount #3 use sudo before commands)

---

### Post by Aisteru on 2010-10-31
Well, something strange happened. The problem seems to be gone now. I turned off Wicd, then tried suspending/hibernating, and nm-applet connected after a few tries. I disabled wicd starting @ boot, rebooted, still was able to connect! suspended/hibernated again, & was still able to connect! I will be leaving Wicd installed, just in case I have trouble again. 

My guess as to why the problem went away is that maybe an update fixed it, but that is just a guess.

Thank you, everyone! :-D

---

### Post by Aisteru on 2010-11-02
Today, after several cycles of hibernating/suspending, I woke my computer & was unable to connect to wifi, even with both network managers running. I tried turning off the wifi adapter (using the hardware button), & disabling networking from Network Manager, but nothing changed. After restarting, it could connect again. I suspended it again, & was able to connect again. I really don't get it.

---

