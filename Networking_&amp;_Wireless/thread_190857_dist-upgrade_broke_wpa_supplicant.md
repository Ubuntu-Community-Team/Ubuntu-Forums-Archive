---
title: "dist-upgrade broke wpa_supplicant?"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by Kensey on 2006-06-06
Friday night I took the big step of dist-upgrading to Dapper (well, I let the wizard do it, but it was still a dist-upgrade under all the dress-up, right?)  I was impressed with how smoothly it went, *except* that after I rebooted, wpa_supplicant no longer ran as a daemon.  The init.d script had been renamed out of the way, as had the config files; I renamed them back but they still did not work ('# /etc/init.d/wpasupplicant start' just gave me back a root prompt, and '# ps aux | grep wpa' showed no processes running).

After leeching my neighbor's unsecured wireless network, I managed to find a few posts about how great gnome-network-manager is, and after installing it and getting back on my secure network, I agree... but it's not as stable as wpa_supplicant was.  Once the desktop became unresponsive when I think it was trying to prompt for the keyring password; I've seen other complaints here related to NM tickling an IRQ issue or some such thing.  Anyway, all that is neither here nor there; what I really want to know is, how do I make wpa_supplicant run as a daemon on boot again?

---

### Post by entangled on 2006-06-07
I put the following command at end of /etc/init.d/bootmisc.sh :
```
sudo wpa_supplicant -Bw -Dwext -iath0 -c/etc/wpa_supplicant.conf
```
The daemon flag is -Bw. Substitute your own interface name if ath0 isn't right for you.
You probably know how to generate a passkey to use in the wpa_supplicant.conf file. I didn't know until recently, then it solved my wpa connection problems.

---

