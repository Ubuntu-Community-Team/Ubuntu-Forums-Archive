---
title: "Wifi Signal."
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by DevAdv on 2009-04-17
hi, was wondering if i can get some insight on this.

im running a D-Link DWL-G520(rev B) which is an Atheros AR5002.

my wifi will connect, but the signal never goes above 60%, when in winblows i get 95% constant.

i checked iwconfig in a terminal and it says signal 37/70. and 1MB for speed.

ive tried 8.04/8.10/9.04 beta and rc and this happens in all.

is there another driver i could use? 

which is the default on jaunty? ath5k or ath_pci?

if someone could point me in the right direction i would be grateful.

ty. 

Dev.

---

### Post by Ferrat on 2009-04-17
I've had similar problems with my WiFi having any unstable and very slow connection, specially downstream and it seems it has to do with channels, try setting your router to channel 6 static and not "search for best" cause seems the Linux drivers doesn't like all channels. 
13 for ex which my router feels is free from other signals, well that Ubuntu can't even detect it seems, 10-12 even though my router says the "airways are clear" I get noise reduced connection from Ubuntu down to 1-6MBit/s and packetlosses but when I use channel 6 which actually is a noiser according to the router I get a steady 54Mbit connection, signal drops sometimes but I never get packetlosses and my speeds are stable.

---

### Post by DevAdv on 2009-04-17
my router has to be set to channel 5.

so is there a way to change the channel on my D-Link in linux? 

network-manager or iwconfig command?

---

### Post by DevAdv on 2009-04-17
well, i fixed it.

ill post the fix incase someone else has this problem.

i installed linux-backport-modules through synaptic, and blacklisted ath_hal and ath_pci in etc/modprobe.d/blacklist

"sudo gedit /etc/modprobe.d/blacklist"

and add

blacklist ath_hal
blacklist ath_pci

save and reboot.

upon reboot i was connected with 100% signal and it bounced between that and 95%, but the data rate was only 1MB.

so i ran "sudo iwconfig wlan0 rate 54M" to fix that.

good luck to anyone else with this problem.;)

---

