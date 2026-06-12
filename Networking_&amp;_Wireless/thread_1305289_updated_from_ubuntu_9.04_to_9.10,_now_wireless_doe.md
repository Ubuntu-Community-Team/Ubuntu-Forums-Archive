---
title: "updated from ubuntu 9.04 to 9.10, now wireless doesn't connect"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by ffoeg on 2009-10-29
If I go to system->preferences->network connections, I see the entry for my wireless network. The settings are fine. But on the toolbar, the Network Manager doesn't have any wireless options.
When I go to Administrator->system testing, and I run a test on my adaptors, both adaptors (wired and wireless) are detected. No problems found.
When I go to system, administration, hardware drivers, there are no proprietary drivers that need to be enabled.
How do I get Network Manager to allow wireless connections to be managed?
Thanks

---

### Post by ffoeg on 2009-10-29
My wireless adaptor details are: Atheros Communications Inc. AR5212 802.11abg NIC

---

### Post by ffoeg on 2009-10-29
when I run  lshw -C network
I see adaptor details, but it says "network UNCLAIMED"

actually, here's what it says:
t:1840(size=32)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:df3f0000-df3fffff

---

### Post by ffoeg on 2009-10-29
if I do iwconfig

here's what I get:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

virbr0    no wireless extensions.

---

### Post by dummy910 on 2009-10-29
I haven't had to use this with any of the upgrades I've completed today, but in 9.04 and earlier I always do this with atheros wireless cards.
```
sudo apt-get install linux-backports-modules-[color=red]jaunty[/color]
```
then REBOOT

[color=red]*[/color] you would replace jaunty with [color=red]karmic[/color] to do this on a 9.10 install, or [color=red]hardy[/color] for an 8.10 etc

---

### Post by ffoeg on 2009-10-29
I appreciate your input dummy910, but that didn't fix the problem. After the install and reboot, my interfaces are where they were before. But thank you.

---

### Post by hilltop_yodeler on 2009-10-29
> **ffoeg said:**
> My wireless adaptor details are: Atheros Communications Inc. AR5212 802.11abg NIC

I have the same exact Atheros card and am having the same problem with fresh 9.10 install.  Never have had troubles with this before.  Ideas would be most appreciated.  Thanks!

---

### Post by hilltop_yodeler on 2009-11-04
> **hilltop_yodeler said:**
> I have the same exact Atheros card and am having the same problem with fresh 9.10 install.  Never have had troubles with this before.  Ideas would be most appreciated.  Thanks!

I've tried the solutions listed at the following locations and have not been successful.

[http://ubuntuforums.org/showthread.php?t=1312627]("http://ubuntuforums.org/showthread.php?t=1312627") 
[http://ubuntuforums.org/showthread.php?t=1312160]("http://ubuntuforums.org/showthread.php?t=1312160")

I reverted to a 9.04 installation and found that my AR5212 wireless card was also not recognized.  I plugged in an 8.04 live-cd and wireless worked great.  I guess that's what I had installed on there previously.  

The laptop that I am having these difficulties with is a Lenovo ThinkPad X60.  This machine is only a few years old and I am shocked that the wireless adapter is no longer supported by Ubuntu.  

Also, it has been suggested numerous times on the forum that you edit your /etc/modprobe/blacklist-ath_pci.conf file so that the line that reads "blacklist ath5k" is commented out.  As it turns out, I don't have this line in my blacklist file; instead, I have a line that reads "blacklist ath_pci", which I have commented out.  I've also tried adding the blacklist ath5k line.  Any changes that I have made to config files have always been followed up with a system restart.  No luck.

Anyone have suggestions?  I'm really close to reverting back to 8.10 since I know that it works.  Your help is much appreciated.  Thanks!

```
$ lspci
Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
```

---

### Post by justfred on 2009-11-04
Do you know if there is way to trace how a wireless connection is set up (as in making first contact, negotiating a channel, etc ...).

I have intermittent problems with two pc's where the connection does not happen although the access point is visible with reosonable signal strenght and I have connected before.

One is a Lenovo T60 laptop the other one is old (amd 1200, packard bell with a D-link usb wifi adapter) destop pc. Both run 9.04 (the 64 bit version for the laptop). There are 2 different access points : one is WPA the other one is an open access point.

I just have no clue why a connection succeeds or not ...

---

### Post by hilltop_yodeler on 2009-11-05
> **hilltop_yodeler said:**
> I've tried the solutions listed at the following locations and have not been successful.

[http://ubuntuforums.org/showthread.php?t=1312627]("http://ubuntuforums.org/showthread.php?t=1312627") 
[http://ubuntuforums.org/showthread.php?t=1312160]("http://ubuntuforums.org/showthread.php?t=1312160")

I reverted to a 9.04 installation and found that my AR5212 wireless card was also not recognized.  I plugged in an 8.04 live-cd and wireless worked great.  I guess that's what I had installed on there previously.  

The laptop that I am having these difficulties with is a Lenovo ThinkPad X60.  This machine is only a few years old and I am shocked that the wireless adapter is no longer supported by Ubuntu.  

Also, it has been suggested numerous times on the forum that you edit your /etc/modprobe/blacklist-ath_pci.conf file so that the line that reads "blacklist ath5k" is commented out.  As it turns out, I don't have this line in my blacklist file; instead, I have a line that reads "blacklist ath_pci", which I have commented out.  I've also tried adding the blacklist ath5k line.  Any changes that I have made to config files have always been followed up with a system restart.  No luck.

Anyone have suggestions?  I'm really close to reverting back to 8.10 since I know that it works.  Your help is much appreciated.  Thanks!

```
$ lspci
Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
```

Come on, surely someone else has the same wireless adapter and is having the same issues.  No solution out there?  Maybe someone has posted the solution and I just have not found it on the forums yet.  Thanks!

---

### Post by hilltop_yodeler on 2009-11-06
Ok, it appears as though there is a solution.  Thanks to drpjkurian for coming up with this.  I am able to now connect to wireless networks via command line.  Neither wicd or network-manager will recognize my AR5212 Atheros wireless card, but using the command line, I can specify the following (as root):

```
## scan for wireless networks
$ iwlist ath0 scanning
$ iwconfig ath0 essid routerName key yourWepKey
## if you can't connect to your router, try obtaining an IP via dhcp:
$ dhclient aht0
```

Here is drpjkurian's solution:
[http://ubuntuforums.org/showthread.php?t=1309072]("http://ubuntuforums.org/showthread.php?t=1309072")

---

