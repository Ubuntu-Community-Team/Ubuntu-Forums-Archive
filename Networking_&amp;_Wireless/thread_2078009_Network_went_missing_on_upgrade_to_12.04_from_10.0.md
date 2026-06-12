---
title: "Network went missing on upgrade to 12.04 from 10.04"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2012-10-29
I'm in the process of cleaning up a laptop to be given to a son's family. Since I had xubuntu 8.04 installed on it, via wubi, I decided to do some experimenting before wiping the wubi install completely off the disk, so I did a version upgrade to 10.04. My main purpose in this is simply to gain experience in an area I had not previously touched; my other version upgrades were all clean installs, and this is the only machine of mine that's used wubi.

That upgrade went fairly well, but since the wireless chip in the laptop is a Broadcomm I had a bit of trouble getting the box back on line before discovering that 10.04 included the necessary drivers under "Hardware Drivers." By that time I had rigged a patch cord from my LAN switch to the laptop and for a while had both eth0 and wlan0 working at the same time.

Emboldened by that, I then did another version upgrade, to 12.04. It completed, but on the reboot at the end of the upgrade, /dev/sdb1 (my /host partition) failed to mount because it was already mounted for exclusive access. I hit S to skip it for the time being, and the system then began waiting for network configuration. It never finished. Eventually it continued without full network capability.

Once I was logged in, I checked "ifconfig" and both interfaces reported they were up and running. I can ping another box on my LAN, presumably via eth0, but only by its IP address. Apparently no DNS server is working on this installation. I've seen posts about dnsmasq but have not yet found how to deal with it, if that's the problem.

At this point my question for this forum is simply "How can I get networking going again?" It may be relevant that there's no Network Manager icon in the notification area of my top panel, and that the Network Connections setting dialog has everything grayed out. All was working properly on 10.04, and it still works when booted into WinXP.

What diagnostic data is needed to troubleshoot this? Let me know and I'll provide it (if the not-fully-capable system will give it to me)...

---

### Post by JKyleOKC on 2012-10-30
Latest update: running boot-repair apparently changed a few things. On the first reboot, the system complained about errors on /boot but eventually did make it all the way through. On the next reboot I hit "F" to fix the problems, and subsequent reboots have been error-free -- but the "Waiting for network configuration..." message, followed a minute later by "Waiting for up to 60 seconds more" and after that "Continuing without network" is still there, and in boot-repair the option to replace legacy grub with grub2 is grayed out.

Despite the network error messages during boot, once it gets to the desktop the network is fully operational (at least through eth0; wlan0 still seems dead). I added dns-nameservers lines to both the eth0 and wlan0 stanzas of /etc/network/interfaces and this apparently was the cure for eth0. Also commented out the "dns=dnsmasq" line in the resolver config file...

The continuing error messages during boot may be due to absence of the b43 firmware; I've still not attempted to download the fix for that. Currently the main problem is how to get grub2 into place, but that's off-topic for this forum...

I know that wiping out this twice-updated installation and replacing it with a clean 12.04 would solve most if not all of the problems, but that wouldn't teach me how to advise folk with similar troubles -- which was the whole point of attempting to upgrade in the first place!

---

### Post by JKyleOKC on 2012-10-31
Finally solved, and as always, once the light dawned the fix was simple.

If an interface is defined in /etc/network/interfaces, then Network Manager will **not** deal with it. Since I had defined all my interfaces in that file, Network Manager loaded but then went dormant with nothing to do.

This would have been fine, except that my definition of wlan0 included the key hash necessary to make connection to my access point, and for some reason that saved hash was no longer correct. Thus wlan0 could never get an IP address, and this caused the failure errors during boot-up.

Once I commented out every line in the interfaces file that dealt with wlan0 and rebooted, everything works as expected. Initially the wireless didn't connect, but Network Manager was able to locate my access point, ask me for the key, and make the connection exactly as expected.

Now if I can determine how to make the connection automatic at boot time, things will be as expected and I can try another on-line upgrade to 12.10 and go through all the troubleshooting again...

EDIT: I installed the b43 firmware installer and this allowed the system to communicate with the router; "dmesg" then showed me that it was being rejected because of the key. Thus this may have been a combination of two problems, not just one...

---

