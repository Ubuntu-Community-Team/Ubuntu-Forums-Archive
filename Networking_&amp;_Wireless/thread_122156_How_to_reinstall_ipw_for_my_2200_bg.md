---
title: "How to reinstall ipw for my 2200 bg"
date: 2006-01-26
forum: Networking &amp; Wireless
---

### Post by StormWatcher on 2006-01-26
Let me start by saying I have no idea what I am doing in Ubuntu or anything linux.

I just installed Ubuntu to my Dell 700m laptop.  I ran XP on it for a several years and all I have used is WIndows for the last 10 years.  I thought I would switch and so I formatted the drive and started at it.

I have pretty much figured out how to get everything running except for my wireless card.  I tried downloading the source from Source Forge and installing the latest version so I could have WPA support.

I ran the make and had error about not being able to find certain directories.  I am guessing Ubuntu puts it in a different place.  OK so I tried to follow the manual instruction and managed to COMPLETELY screw everything up.

Being that I don't understand much about linux I am finding it frustrating to get wireless working.  Can anyone point me towards a place that has well documented the process of setting up the IPW drivers in Ubuntu.  Something that shows me the exact commands to run.

I have the eth1 wired connection working fine.  However for my home and school I would like to have wireless running.  This is the last thing I have to figure out.

Thanks for your help.

---

### Post by Lambert on 2006-01-26
See if these links can help you.

[http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200)

[http://doc.gwos.org/index.php/Ipw2200_wpa](http://doc.gwos.org/index.php/Ipw2200_wpa)

read through both of these before starting anything.

---

### Post by StormWatcher on 2006-01-26
Thanks for your quick response!

I am almost there.

I am confused on how to check the status of my wireless connection.  My AP says I am connected, but it did not give me an IP through DHCP.

When I run:

dmesg | grep ipw

It returns:

[4294698.619000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.10[4294698.619000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4294698.623000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

So I guess I am connected.  But if I run ifconfig it does not show my eth0 as active or anything.  What do I use to configure my wireless.  I have info in wpa_supplicant.conf and that seems to be working.  That file has:

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="my_sid"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="my_key"
}

and I would assume by what dmesg | grep ipw returns that all is ok.

I read the command dmesg | grep ipw off of the second tutorial.  I understant grep to be a search tool adn I assume dmesg is a log file, but I am not sure.  

If I unplug eth1 and reboot I don't connect to anything.  Any ideas?

Thanks.

---

### Post by StormWatcher on 2006-02-02
I am so close I can taste it.  \\:D/ 

Everything seems to come up except I have to manually run dhclient eth0 and then it gets an IP and everything works.

When I first boot it takes forever to get past the bringing up network interfaces.

eth0 shows up under network interfaces, but without an IP.  I disabled my wired card eth1 in hopes of speeding up the boot.

I don't mind running dhclient manually, but I know there is a way to automate all of it.  Thanks for your time.

StormWatcher

---

