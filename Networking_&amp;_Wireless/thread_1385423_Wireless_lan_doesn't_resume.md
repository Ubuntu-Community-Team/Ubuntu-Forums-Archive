---
title: "Wireless lan doesn't resume"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by Iskendar on 2010-01-19
Hi all,

 I'm setting up an HTPC (Zotac IONITX-F in a Silverstone ML02-MXR case with remote) running XBMC on top of a minimal karmic install. So far I've managed to get everything running including the tricky stuff: wireless, lcdpro and lirc. I did have the same samba/dhcp conflict described in [this thread]("http://ubuntuforums.org/showthread.php?t=1140094"), so I opted for a static IP solution instead of the usual dhcp connection with the router (D-link DIR-615) reserving an IP for the MAC-address. This is my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# Wireless
auto wlan0
#iface wlan0 inet dhcp
iface wlan0 inet static
	address 192.168.0.111
	netmask 255.255.255.0
	gateway 192.168.0.1
pre-up /sbin/wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

 So far I can get the pc to suspend and wake up using the remote, but when I do so, the wireless connection dies. Pinging it from my desktop leads to "Destination Host Unreachable" errors. Running ifconfig on the htpc shows that wlan0 doesn't have an IP address anymore. 

 To make things stranger: restarting /etc/init.d/networking gives wlan0 an IP address again, but still results in "Destination Host Unreachable" errors on both sides! Rebooting OTOH solves the problem. Any ideas what might be causing this?

I looked into some logs in /var/log, for instance the pm-suspend.log:
```
Tue Jan 19 20:09:23 CET 2010: performing suspend
Tue Jan 19 20:10:08 CET 2010: Awake.
Tue Jan 19 20:10:08 CET 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55wicd resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Tue Jan 19 20:10:11 CET 2010: Finished.

```

It seems to imply that the wicd resume script succeeded even though /var/log/wicd/wicd.log states:
```
2010/01/19 20:14:01 :: No wired connection present, attempting to autoconnect to wireless network
2010/01/19 20:14:01 :: Unable to autoconnect, you'll have to manually connect
```

---

### Post by Iskendar on 2010-01-21
Bump.

Anyone?

Should I put this in server instead?

---

### Post by Iskendar on 2010-01-22
Ok, threw out samba for the time being, and set interfaces to dhcp. No more IP reservation on the router side. Problem still persists. Restarting the network gives the error:

```
No DHCPOFFERS received
No working leases in persistent database - sleeping
```

Running "iwlist scanning" returns:

```
wlan0   Interface doesn't support scanning: Device or resource busy
```

Ideas?

---

### Post by Iskendar on 2010-01-24
Ok, this is starting to look more like a blog than a forum, but whatever...

Been digging into the pm-utils docs a bit, and I've tried running the scripts in /usr/lib/pm-utils/sleep.d (55wicd and 55NetworkManager more specifically) and /etc/pm/sleep.d/wpa_action separately, and strangely enough, running them with the suspend option does NOT shut down the network. Nor do the resume options affect the network in any way, it happily keeps pinging my router without any change. So I suspect when the system suspends, the network goes down the hard way.

I don't really know whether I use wicd or NetworkManager at all, this is a gui-less install from the minimal 9.10 iso, I basically installed my network
by configuring /etc/network/interfaces and /etc/wpa_supplicant.conf and that's about it. Any hints on how to write a decent suspend/resume script for this sort of setup?

---

### Post by Iskendar on 2010-01-24
Another thing I tried: I stopped the network (/etc/init.d/networking stop), suspended the system, resumed, then started the network (/etc/init.d/networking start) again, with the same results.

---

### Post by Iskendar on 2010-01-24
Ok, did it the hard way: unloaded the ath9k driver for the wireless card before suspend, reloaded it after resume, and restarted the network. It works! Yay me...

And since all this digging gave me a rudimentary understanding of how all this pm-utils stuff works, I wrote a script for it :-) Behold /usr/lib/pm-utils/55wireless:

```
#!/bin/bash
case $1 in
    hibernate)
        /etc/init.d/networking stop
        rmmod ath9k
        ;;
    suspend)
        /etc/init.d/networking stop
        rmmod ath9k
        ;;
    thaw)
        modprobe ath9k
        /etc/init.d/networking start
        ;;
    resume)
        modprobe ath9k
        /etc/init.d/networking start
        ;;
    *)  echo "Not an option for 55wireless"
        ;;
esac
```

I'm not labeling this as resolved yet, because it's a bit of an ugly hack and I don't know what's causing this yet. So I'd appreciate some input on what may cause this, and how to solve it properly (isn't there a modules config file for pm-utils or something?)

---

