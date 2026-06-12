---
title: "Wpa-psk issues ubuntu 9.10"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by supaman306 on 2009-11-02
Hi All,
 
I am a newbie to ubuntu! I first thought it was GREAT until I found that I couldnt configure the internet on it after 3days!! (I dont  give up easy). So right now I am not happy with UBUNTU.
 
 
I have followed loads of posts this one was helpful but never worked:
 
_[COLOR=#800080][http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)[/COLOR]_
 
My config looks like this:
 
[B]auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp[/B] 
 
I have installed the ndiswrapper and ndisgtk packages and used network manager however never been able to get it working, works without a password on the router but not with the WPA-PSK TKIP password I have set. (also tried Wcid without luck)
 
The wireless network is found but no internet connection.
 
I have nearly given up...Any ideas? :(
 
Thanks
AJ

---

### Post by supaman306 on 2009-11-04
So is the fact no one knows the answer or ???
 
I really wanna get this working please help meeeeeee ??!!

---

### Post by glen_4455 on 2009-11-04
I also faced same problem. My Kubuntu 9.10 karmic couldn't connect to my AP with WPA2-PSK. However, a friend of mine who use Fedora 11 can connect to my AP with no problem. Anyone have idea how to fix it?? Please help:(

---

### Post by crgwil on 2009-11-04
If your SSID is hidden, then you may be hitting the following bug:

[https://bugs.launchpad.net/ubuntu/+bug/468741](https://bugs.launchpad.net/ubuntu/+bug/468741)

If I change the access point settings to enable the SSID broadcast, I'm able to connect. Less than ideal work-around, but it's all I've got for now on 9.10. No such problem for me with 9.04.

---

### Post by supaman306 on 2009-11-04
Mine was not hidden :(

---

### Post by supaman306 on 2009-11-04
Left wireless card in the machine and reinstalled ubuntu, all worked fine thereafter

---

### Post by wieman01 on 2009-11-07
Wireless should not be much of an issue any longer, so I am glad it turned out to work OK for you.

---

### Post by tdwright on 2009-11-08
I'm having similar troubles with my upgraded (from intrepid) set up.

Under intrepid I could connect to my non-hidden, wpa-psk access point. After upgrading, I'm unable to connect at all; even after changing my AP to use WEP (64 and 128 bit).

Any ideas?

---

### Post by fubofo on 2010-01-20
I'm also having issues. Fresh install, Kubuntu 9.10, wireless card in machine during install. Wireless worked perfectly without any encryption - I had an issue with my network so had to turn on WPA-PSK (TKIP). Now I simply cannot connect.

This seems to be a recurring issue with A LOT of people on 9.10 and nobody seems to know the issue or be bothered to look into it. Yet another reason I'm keeping Win7 as my main machine and Linux for 'playing around with'

---

### Post by mixalis1987 on 2010-02-11
After upgrading today to 9.10 from 9.4 my wireless broadcom stoped connecting to wpa2 TKIP, the fix for me was to change my routers settings to wpa2 AES after doing that and perhaps a sudo apt-get update it seems to be working ok now.

---

### Post by outside context problem on 2010-02-15
yeah, feeling the pain here too. it just stalls as it attempts to connect. Under "hardware drivers" there's a Broadcom STA wireless driver, but when I try to activate it there's an issue with installation. It says "Please have a look at the log file for details: /var/log/jockey.log" - but that log doesn't mean much to me.

---

### Post by zaphod777 on 2010-02-16
Have you guys taken the time to file bug reports? 

her is the link for network manager in launchpad.
[https://launchpad.net/ubuntu/+source/network-manager](https://launchpad.net/ubuntu/+source/network-manager)

posting bug reports on there is the only way we can get patches released.

---

### Post by ialazzo on 2010-04-11
The following has worked for me. After using network manager (adding the network connection, choosing WPA/WPA2 Personal security, and entering the WPA PSK in the password field) 

You need to manually connect. 
$ sudo wpa_passphrase <ESSID> <your WPA password> > /etc/wpa_supplicant.conf
$ sudo wpa_supplicant -B -c /etc/wpa_supplicant.conf -i wlan0
$ sudo dhclient wlan0
Restart the computer and connect using network manager. It works fine!

---

### Post by yrhen on 2010-04-11
when I try this it refuses the first line: won't admit me to the file (which doesn't seem to exist either)?

---

### Post by outside context problem on 2010-04-15
ditto

---

### Post by dissembly on 2010-08-02
Did either of you ever find a fix for this?

I entered > $ sudo wpa_passphrase <ESSID> <your WPA password> > /etc/wpa_supplicant.confas ialazzo says, and got:> bash: /etc/wpa_supplicant.conf: Permission denied

---

### Post by gimmickless on 2010-08-04
Also tried sudo wpa_passphrase.  Also getting "permission denied".

---

### Post by Starks on 2010-08-05
Put sudo in front of /etc/wpa_supplicant.conf

---

### Post by sinner99 on 2011-05-04
> **ialazzo said:**
> The following has worked for me. After using network manager (adding the network connection, choosing WPA/WPA2 Personal security, and entering the WPA PSK in the password field) 

You need to manually connect. 
$ sudo wpa_passphrase <ESSID> <your WPA password> > /etc/wpa_supplicant.conf
$ sudo wpa_supplicant -B -c /etc/wpa_supplicant.conf -i wlan0
$ sudo dhclient wlan0
Restart the computer and connect using network manager. It works fine!


THANK YOU!! googling all over the place and nothing, nowhere does anyone mention this..to the ubuntu devs or any nix devs for that matter, do you guys ever try installing distros with only wireless? im far from a complete noob. but man. what a headache. the default options even in natty 11.04 only accept wep as far as i could tell.

---

