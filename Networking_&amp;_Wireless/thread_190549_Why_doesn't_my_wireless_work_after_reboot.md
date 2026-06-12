---
title: "Why doesn't my wireless work after reboot?"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by johnkennethhughes on 2006-06-06
I have just set up Ubuntu Dapper on a laptop with a Broadcom wireless card. I installed bcm43xx-fwcutter and used it to install the firmware from a bcmwl5.sys file. Everything worked fine. However, every time I reboot, I have to go into System->Administration->Networking, deactivate and re-activate the card in order to get connected. This is no use as I am not the only person who uses this computer - I need the connection to work automatically when the computer boots. Please help!

---

### Post by slakkie on 2006-06-06
Hi, you might want to check out this page: [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

But what is /var/log/messages telling you, and how is your /etc/network/interfaces configured?

---

### Post by johnkennethhughes on 2006-06-06
I used that link to set the connection up in the first place. I didn't install Network Manager because I only really need to connect to the one network. I'm not quite sure what you want me to do with /var/log/messages, but my /etc/network/interfaces file looks like this:

> auto lo
iface lo inet loopback

iface eth0 inet dhcp
wireless-essid MYESSID
wireless-key MYWEPKEY

auto eth0

---

### Post by johnkennethhughes on 2006-06-07
I checked out this Wiki page:

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

And added the following to my /etc/network/interfaces file immediately after "iface eth0 inet dhcp":

> pre-up ifconfig eth0 up
post-up iwlist eth0 scan

I'm not sure which one of those commands is responsible, but now it seems to work perfectly!

---

