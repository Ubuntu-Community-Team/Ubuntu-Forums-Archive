---
title: "ndiswrapper v 1.0 &amp; DWL-122, help needed."
date: 2005-02-11
forum: Networking &amp; Wireless
---

### Post by puelly on 2005-02-11
Hello All,

I am a relative linux newbie and I am trying to weene myself of the "other" OS but its impossible to do if I can't get my wireless adapter to work.

I have installed the ndiswrapper deb from source and I have used "ndiswrapper -i netprisim.inf" and according to the logs and ndiswrapper, the driver is installed and the hardware present.

However when I use "iwconfig" it lists all the interfaces but says that wlan0 has no wireless extensions.  Also when i use "ifconfig" the wlan0 interface is but the is no entry for the MAC address (All zeros).

I have been researching this for a while and can't find a solution.  Can someone please help me out or point me to a FAQ or HOWTO that I may have missed.

Thank you.

mac

---

### Post by el_mexicano_europeo on 2005-04-07
I also have a wireless card and it works perfectly.

i think you are missing this step:

1.) sudo modprobe ndiswrapper

2.) you might have to change your ESSID with "iwconfig wlan0 essid xxxx"

and that's it.

make sure you are using ndiswrapper 1.1 (not antyhing else because it can crash the system)

i hope this helps.

---

### Post by tidalwav1 on 2005-04-09
[QUOTE=el_mexicano_europeo]I also have a wireless card and it works perfectly.

i think you are missing this step:

1.) sudo modprobe ndiswrapper

2.) you might have to change your ESSID with "iwconfig wlan0 essid xxxx"

and that's it.

make sure you are using ndiswrapper 1.1 (not antyhing else because it can crash the system)

i hope this helps.[/QUOTE]
 Nah, I'm actually having the same problem. running 'ndiswrapper -l' says driver present, hardware present, but it doesn't load up the card (dmesg says nothing about wlan0.) This is very interesting...I can't get anything to work with ndis, but I was able to get everyhint working with linux-wlan-ng being implemented by a tiny shell script I 'wrote' (see [http://ubuntuforums.org/showthread.php?t=25676)](http://ubuntuforums.org/showthread.php?t=25676)). Still, it'd be nice to have ndiswrapper work.

---

### Post by puelly on 2005-04-14
[QUOTE=el_mexicano_europeo]I also have a wireless card and it works perfectly.

i think you are missing this step:

1.) sudo modprobe ndiswrapper

2.) you might have to change your ESSID with "iwconfig wlan0 essid xxxx"

and that's it.

make sure you are using ndiswrapper 1.1 (not antyhing else because it can crash the system)

i hope this helps.[/QUOTE]

thanks for the help. got it working with ndiswrapper so far. (fingers crossed here). how do i get the ndis module to be loaded on default?

---

### Post by tidalwav1 on 2005-04-14
[QUOTE=puelly]thanks for the help. got it working with ndiswrapper so far. (fingers crossed here). how do i get the ndis module to be loaded on default?[/QUOTE]

I'm pretty sure if you type 'sudo ndiswrapper -m' it will load on boot.

---

### Post by az on 2005-04-14
Any module in /etc/modules is loaded on boot.

---

### Post by puelly on 2005-04-14
[QUOTE=azz]Any module in /etc/modules is loaded on boot.[/QUOTE]

thanks for tip. tried that but it didn't work. I find ndiswrapper with the DWL-122 to be too unstable.  Works sometime-ish.  I'm gonna try the wlan-ng again, seem to be having better results with that.

---

