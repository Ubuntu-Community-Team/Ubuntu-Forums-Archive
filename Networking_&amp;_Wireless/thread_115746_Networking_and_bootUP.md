---
title: "Networking and bootUP"
date: 2006-01-11
forum: Networking &amp; Wireless
---

### Post by dezral on 2006-01-11
In the next release, i would like to see DHCP broadcasting to bee (backgrounding), right now i use 5.10 on my laptop(acer) and i have to hit CTRL+C , to brake the " network service" from DHCP at THAT moment(need to chose the right wireless network first).

I use my laptop at work and home, different key's and networks...:KS 

i have try''d
wifiradar
networkmanager(current)
Gnome network thing/ubuntu default (why are we using this??)
2 - 3 others...:???: 

one thing more, why does the default ubuntu network manager, try to find a DHCP server, when the network fail???:confused:  not connectet even..(no link).

Dezral
Member Of Takhis Network.

---

### Post by s_p_a_r_k_y on 2006-01-11
find this line in 
/etc/init.d/networking
 ifup -a  >/dev/null 2>&1
and change it to
 ifup -a  & >/dev/null 2>&1

This will force it to go into the background on startup, not slowing you down while waiting for dhcp

---

### Post by Mr_Grieves on 2006-01-11
I think 'screen' would be abit better for you.

Check this out:
[http://nerdierthanthou.nfshost.com/2004/12/screen-howto.html](http://nerdierthanthou.nfshost.com/2004/12/screen-howto.html)

---

### Post by dezral on 2006-01-12
Thanks, i try that...

Dezral

[QUOTE=s_p_a_r_k_y]find this line in 
/etc/init.d/networking
 ifup -a  >/dev/null 2>&1
and change it to
 ifup -a  & >/dev/null 2>&1

This will force it to go into the background on startup, not slowing you down while waiting for dhcp[/QUOTE]

---

### Post by dezral on 2006-01-12
screen is not used on bootup(init), i use screen  for lets say 
btdownloadcurses.bittornado... and so on...

Dezral
[QUOTE=Mr_Grieves]I think 'screen' would be abit better for you.

Check this out:
[http://nerdierthanthou.nfshost.com/2004/12/screen-howto.html](http://nerdierthanthou.nfshost.com/2004/12/screen-howto.html)[/QUOTE]

---

### Post by dezral on 2006-02-15
found a new way.....

i use Network Manager for gnome...it's not perfect YET.. but close...

i remove the /etc/init.d/networking and from rc0.d,rc6.d,rcS.d(Network manager takes care of detection anyway(DHCP).)

maybe remove ntpupdate to(timesyc to ntp.ubuntulinux.org).

nice no errors and waiting to find networks/DHCP servers....

ps. use can still use /etc/network/interface, and ifconfig eth0 add and so on... i just hate the network tool for ubuntu thats all ;-)-...

>>and you can apt-get remove "netapplet" to... no need for it.

dezral

---

