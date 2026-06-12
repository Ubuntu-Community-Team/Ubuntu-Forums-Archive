---
title: "madwifi (breezy badger) seems flaky on my thinkpad"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by byron on 2006-01-16
the default install pickedup my atheros wireless card and applied the madwifi drivers... i set up a temporary non WEP/WPA network to browse HOW TOs and such on setting up wpasupplicant for my card.  i had no problem getting it to connect to the open network... but it disconnects every couple minutes, then reconnects 60sec or so later.  

i followed the WPA How To:  [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

but i still get nothing... im running wpa_cli in a diff terminal and when i do a "status" it says it is authenticated.. so i know the wpa_supplicant.conf file is set up properly and such... it just isn't issuing a DHCP address.  

is there a problem with the madwifi drivers included with breezy badger?  if so... how might i go about upgrading to a newer version?

don't assume anything please... i'm coming from RedHat/Fedora... so some of the deb/ubuntu stuff is a bit foreign to me.

thanks.

---

### Post by Lambert on 2006-01-16
Madwifi is still a beta driver but it's pretty stable in ubuntu from my experience.

After it disconnects run dmesg or look in /var/log/syslog to see what it says.

Does your router have a log you can also check?

Sounds like you've used this card in another distro so this may be nothing but have you tried using a different channel to see if it's any different? Possible signal interferance.

---

### Post by byron on 2006-01-16
ya.. i'm coming from FC4.  i couldn't get any stability on my thinkpad in FC4.  it would just randomly lock up the entire machine and required a hard reboot.  it did it about once per day.

are there any nice step by steps for updating the drivers in ubuntu from the old madwifi drivers to the new madwifi-ng drivers?

---

### Post by Lambert on 2006-01-17
[http://ubuntuforums.org/showthread.php?t=105437](http://ubuntuforums.org/showthread.php?t=105437)

---

### Post by byron on 2006-01-17
thanks... 

ok.. i've got the latest -ng drivers working.. but now it can't get the interface to load at boot.

the section of my /etc/network/interfaces file looks like:

```

iface ath0 inet dhcp
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
pre-up ifconfig ath0 up
pre-up ifconfig mode "Managed"
pre-up /usr/sbin/wpa_supplicant -Bw -iath0 -Dmadwifi -c/etc/wpa_supplicant.conf
pre-up sleep 5
post-down killall -p wpa_supplicant

```

i downloaded the latest wpa_supplicant and compiled it myself rather than using the .deb versions... so i want to just launch wpa_supplicant after the interface is created... is it not possible to do this from the interfaces file?

if i copy the above into a file and chmod 777 on it and launch it via *sudo ./startwifiwpa* the interface comes right up and wpa_supplicant launches and works.  the only exception being that wpa_cli doesn't want to see the wpa_supplicant process.... any ideas?

any suggestions on tweaking this section?  again, sorry if any of this is way off base... im slowly learning the deb way of doing things.

---

### Post by Lambert on 2006-01-17
I'm not that knowledgeable when it comes to wpa as I don't use it and haven't needed to yet.

But here is what I can offer.

1. the pre-up ifconfig ath0 up...remove this line
2. add *auto ath0* so it looks like this

auto ath0
iface ath0 inet dhcp
xxx
xxx
xxx
xx

---

