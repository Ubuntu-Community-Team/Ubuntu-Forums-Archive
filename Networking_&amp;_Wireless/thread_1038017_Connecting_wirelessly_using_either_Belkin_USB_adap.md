---
title: "Connecting wirelessly using either Belkin USB adapter or Atheros built in card,"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by MattBlackLamb on 2009-01-12
Hello, I have a PcSpecialist laptop running Ubuntu 8.10 which has a built in Atheros Wifi card (Ar242x according to lspci) which I have been trying to get working on & off since I got the computer in November 2008. I have tried various solutions and none of them have worked, at the moment if I want Network Manager to even have a wireless option I need to open a terminal & type ```
sudo modprobe ath_pci
``` as I am unable to edit the startup file. NDISWrapper is installed and has a working driver, but that doesn't give me a Wireless option in Network manager.

The other option I have is a belkin USB adapter that a friend gave me about 2 years ago (model: F5D7050 E). Again, this has NDISWrapper drivers that according to belkin's website are for the right revision. The problem with the USB adapter is that when it's plugged in it isn't recognised, none of the lights go on and it doesn't appear in lsusb. 

Obviously it's slightly neater to get the internal card working but I'm easy either way as long as I can connect to the internet. I have read the NDISWrapper troubleshooter at the top of the networking forum and tried a few things, but none of them really pointed me anywhere. 

Thanks for any help :)

---

### Post by MattBlackLamb on 2009-01-14
I have now swapped to Wicd and I still have the same problem, any answers would be appreciated. I have tried many things to remedy this and if I weren't seeing similar ideas carried out in slightly different ways I wouldn't have posted this thread.

I am quite new to linux, I have only been using it since last november when I got the laptop.

Thanks in advance for any help.

---

### Post by ASchweitzer on 2009-01-14
Ubuntu may have detected your hardware wrong. If you have Windows dual-booted, run it and double-check your hardware. Also, give this a read:

[http://ubuntuforums.org/showthread.php?t=816780&highlight=atheros+AR5007EG]("http://ubuntuforums.org/showthread.php?t=816780&highlight=atheros+AR5007EG")

it's a guide to using madwifi drivers, with which you may have success. Check their hardware compatibility list.

---

### Post by MattBlackLamb on 2009-01-14
I don't have a dualt-boot machine so I have to go with what Ubuntu tells me.

I have followed the instructions in the thread you linked me to and I got as far as getting rid of ndiswrapper but ```
sudo ndiswrapper -e net5211
sudo modprobe -r ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgtk
```
didn't work, here is the output from terminal:

```

$ sudo ndiswrapper -e net5211
couldn't delete /etc/ndiswrapper/net5211: No such file or directory
$ sudo modprobe -r ndiswrapper
WARNING: /etc/modprobe.d/blacklist line 47: ignoring bad line starting with 'The'
$ sudo apt-get remove --purge ndiswrapper-common-utils ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common-utils

```

---

### Post by ASchweitzer on 2009-01-14
You've entered the command wrong, I think.
It's
```
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgt
```
while you have
```
sudo apt-get remove --purge ndiswrapper-common-utils ndisgtk

```

once you've run this it should clear your computer of ndiswrapper. from there you can start messing with madwifi. 
[http://madwifi-project.org/wiki/Chipsets]("http://madwifi-project.org/wiki/Chipsets")
looks promising, listing 2425 and 2424 chipsets as working. Either of these could be the 242x lspci is speaking of.

Just thought of this: are you running 32 bit or 64 bit? You'll need to use 64 bit drivers with 64 bit ubuntu under ndiswrapper.

---

### Post by MattBlackLamb on 2009-01-15
I'm running 32 Bit, I did notice that the walkthrough is for 64 bit. I'll give it a go & see how it pans out.

Edit:

I copy & pasted your command into terminal & is said:
```

sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgt
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not installed, so not removed
E: Couldn't find package ndisgt

```

I decided to have a look in Synaptic Package Manager and ndisgt wasn't in the list after I searched for ndiswrapper. I did get ndisgtk, ndiswrapper-utils-1.9, and ndiswrapper-common which I guess are the packages I need to get rid of...

---

### Post by MattBlackLamb on 2009-01-17
Sorry to double post but I still haven't got anywhere with this. Should I remove the packages using synaptic as the terminal commands don't seem to work?

---

### Post by ASchweitzer on 2009-01-17
The easiest is to do a fresh install, if that's an option. Or do a second install, if you have enough space, to play with things. If not, use synaptic to get rid of ndiswrapper, and then try madwifi.

---

### Post by MattBlackLamb on 2009-01-17
A fresh install didn't appeal to me & I don't think I have the know-hoe to partition my disk & keep my current install secure so I removed Ndiswrapper using Synaptic. 

That solution didn't work for me, here's the output from iwconfig:
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Sitecom"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Anduu (the walkthrough's writer) did say that it was for 64 bit ubuntu which may be why it hasn't worked.

---

### Post by ASchweitzer on 2009-01-17
under madwifi *ath0* should be your wireless interface. Can you not connect using the Network Manager or anything?

---

### Post by MattBlackLamb on 2009-01-18
Wireless is enabled under Network Manager, but it doesn't show any wireless networks, despite the fact that there is one there as my PC (running XP) uses it.

---

### Post by MattBlackLamb on 2009-01-20
Sorry for another double post, but i anyone has any suggestions that might help get it working then please let me know. 

Wireless is enabled under network manager it just can't see any wifi networks, I have had the laptop in other places & it had the same problem so it's not just my network. 

Any help will be greatly appreciated and I'd like to thank ASchweitzer for helping me this far.

---

