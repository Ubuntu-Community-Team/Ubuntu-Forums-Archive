---
title: "Problem on connecting by essid, not MAC address on wicd"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by sayyeah on 2009-05-27
Hi there, I'm in the university with 100+ AP's around the campus. Since they all have identical ESSID and the same WEP password, I wanted to connect to them based on ESSID, not per AP's MAC address whenever I change to a different location.
(Otherwise it's a nightmare...)

After searching, I followed the next article but found something unexpected.
[https://bugs.launchpad.net/wicd/+bug/270291](https://bugs.launchpad.net/wicd/+bug/270291)

1. On the advanced settings of the selected network, I checked "Use this settings for all networks sharing this essid". However, on the wicd's network list, I still see several networks with the same ESSID. I think they should be grouped with a single ESSID, like the network manager or windows does. So when I try to connect to another AP with the same ESSID, wicd asks me to enter the WEP key again. I think it should automatically put the key that I entered on the last network since they have the same ESSID.

2. More fundamentally, I do not understand why this setting should be included in the advanced setting of each network. This setting is in the level of "global" scope, not "per-network". Intuitively, it should be in the "Preferences" menu, which belongs to the global scope.

I'm using wicd 1.5.9-2 on Jaunty 9.04.

I really don't want to use the network manager again.. :(
Any hint or help is greatly appreciated!

---

### Post by imdano on 2009-05-27
Checking that box doesn't cause all the AP's to consolidate into one, but it should make them all share the same settings.  The option isn't in the preferences window because you may want all networks named "Wifi" to share settings, but want all networks with the name "linksys" to have their own individual settings.

What version of wicd are you using?  What does /etc/wicd/wireless-settings.conf look like?  I haven't heard of anyone running into issues with the "Use these settings for all networks sharing this ESSID" option in 1.5.9.

---

### Post by sayyeah on 2009-05-27
Thanks imdano for the explanation. Interestingly, after I rebooted ubuntu, I found that it now works !

I also verified that /etc/wicd/wireless-settings.conf contains [essid:GTwireless] part, where GTwireless is the ESSID.

Wicd rocks..Hope it is the standard of the next ubuntu version.

---

### Post by kerry_s on 2009-05-27
wicd is nice for auto setup.
there is also a manual option called "network-config" it's in the repos.
in network-config you just store the settings you want in a profile you create, after that you just select it and apply. there's no running daemons like other network managers, so it's as light as you can get.

i put some screenshots here: [http://ubuntuforums.org/showthread.php?p=7353834#post7353834](http://ubuntuforums.org/showthread.php?p=7353834#post7353834)
and
here: [http://ubuntuforums.org/showthread.php?p=7354992#post7354992](http://ubuntuforums.org/showthread.php?p=7354992#post7354992)

---

### Post by sayyeah on 2009-05-27
It looks very nice. I'll give it a try.
The fact that it doesn't require a daemon is pretty intriguing.
Thanks for the info.

---

### Post by kerry_s on 2009-05-27
> **sayyeah said:**
> It looks very nice. I'll give it a try.
The fact that it doesn't require a daemon is pretty intriguing.
Thanks for the info.

since the ap's use the same name & password you should be able to create 1 profile that works for all of them.
you know how to create a launcher right? i use "gksudo network-config" for my launcher command. it can run with just "network-config", but i found its faster to just start it as root. you can also use the "NOPASSWD" option in sudoers so you don't have to type the password every time you use it.

---

