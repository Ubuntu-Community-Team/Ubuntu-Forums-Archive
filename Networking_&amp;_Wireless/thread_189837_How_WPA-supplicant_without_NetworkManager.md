---
title: "How WPA-supplicant without NetworkManager?"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by supermihi on 2006-06-05
Hey, I reinstalled kubuntu on my laptop to get a "clean" install. Now I have issues with my wireless connection:
I remember, before the reinstallation, I had a /etc/network/interfaces with some wpa-specific lines, like "wpa-essid XYZ" or something like that. Unfortunately I didn't save this config file, and I can't find _anything_ about that in the docs. NetworkManager isn't an option for me since it doesn't work with my chip, and furthermore I want my connection to be established before I login to kdm.
So, I'd like to have a nice wpa_supplicant.conf for roaming and just tell the /etc/network/interfaces to use that and dhcp as soon as it's connected to an AP.
There are some solutions in this forum but they all do something like "killall wpasupplicant", which doesn't seem very sophisticated, and I remember having a better solution.
Of course I could just write something to in a local initscript, but since there is a way to do this clean with ifupdown, I'd like to use that.

---

### Post by elamericano on 2006-06-05
Why would you have to kill wpa_supplicant if you never started it?

The used to be a wpa_supplicant service in /etc/default, but I think that's gone with Dapper. I'd just start it manually and use a wpa_cli action script to kick-off DHCP. That is documented in the wpa_supplicant README.

---

### Post by elamericano on 2006-06-05
> NetworkManager isn't an option for me since it doesn't work with my chip
NetworkManager uses wpa_supplicant for WPA, so why wouldn't it be compatible with your chip?

---

### Post by lexxonnet on 2006-06-05
Just out of curiosity, which chip are you using?

---

### Post by supermihi on 2006-06-06
I am using an atheros chip, but it's a very new one on a mini-express card and only supported by newer svn versions of madwifi-ng. Already posted that here:
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15-23-386/+bug/48507]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15-23-386/+bug/48507")

The problem is that first I needed to also recompile wpa_supplicant because the headers for the new ng code weren't compiled in. Now, newer versions of madwifi-ng svn are supported by wpa_supplicants wext driver. Maybe this is why the networkmanager doesn't work, because i tries to use madwifi driver instead of wext.

---

### Post by elamericano on 2006-06-06
I've been meaning to recompile my atheros driver and wpa_supplicant anyway. I'll do that now, and see how it goes. I'm already using network-manager-pptp_0.6.2-0ubuntu0linux2go1_i386.deb, which is also an upgrade, so I'll have a completely new wireless codebase. If network manager still works I'll post my results here.

---

### Post by elamericano on 2006-06-06
madwifi-ng-r1627-20060605 and wpa_supplicant-0.5.3 up and running! I was a little superstitious and didn't take the build from 6/6/6. I wouldn't want my computer to become possessed :twisted: 

as I said before, this works with network-manager_0.6.2-0ubuntu7linux2go2_i386. Whether or not this works for you depends on if you chipset is supported by the latest madwifi-ng drivers. If it is, then compatibility the rest of the way shouldn't be a problem.

---

### Post by supermihi on 2006-06-08
Where do I get this version of network-manager you mentioned? In APT I only have 0.6.2-0ubuntu7

---

### Post by marcantonio on 2006-06-10
Check out /usr/share/doc/wpasupplicant/.  It's got a lot of info on the new wpa_supplicant setup in Dapper.

---

### Post by supermihi on 2006-06-11
Yeah thanks, I now found the according section.

I just wrote my own wpa_supplicant.conf and put the line:
```
wpa-conf /etc/wpa_supplicant.conf

```
into the section of the wireless interface. This works since all my networks use DHCP. If I find the time I'll try something more sophisticated like guessnet or whereami.
The NetworkManager still doesn't work. But this solution now is even better, since it starts connecting before I login to KDE.

---

