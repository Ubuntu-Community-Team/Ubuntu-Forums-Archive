---
title: "Can't Ping Ubuntu PCs by Hostname"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by Sasayaki on 2009-11-09
Hey guys,

Have a perplexing one for you all. My home network has six Ubuntu PCs and about seven Windows PCs (plus a couple of iPhones, MythTV frontend/backend etc... it's a large household) and up until now we've been using a 2Wire 2701HGV-W ([http://www.2wire.com/index.php?p=106](http://www.2wire.com/index.php?p=106), came free with our old Bigpond service) to run our Internet. This device also did our DHCP, a job it did quite well.

However, we're all heavy Internet users and as such we've retired that modem and bought something more beefy- a Netcomm NB6Plus4W ([http://www.netcomm.com.au/products/adsl_broadband/nb6plus4w](http://www.netcomm.com.au/products/adsl_broadband/nb6plus4w)). This does our Internet MUCH better, but has one minor issue with the DHCP... and the weird thing is it's with Ubuntu only. The various Windows machines don't seem to have any issues.

The problem is that the Ubuntu machines can't ping other Ubuntu machines by host name. The Windows machines can ping the Windows machines just fine, and with one exception (I think that one's dodgy... so just ignore it) the Ubuntu machines can ping the Windows ones.

However- before people start saying that it's the new Netcomm modem's fault... we also tried a Buffalo WZR-HP-G300NH ([http://www.buffalotech.com/products/wireless/nfiniti-wireless-n/nfiniti-wireless-n-high-power-router-access-point-wzr-hp-g300nh/](http://www.buffalotech.com/products/wireless/nfiniti-wireless-n/nfiniti-wireless-n-high-power-router-access-point-wzr-hp-g300nh/)), a D-Link DSL-504T ([http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=1&Sub2=2&PID=49](http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=1&Sub2=2&PID=49)) both with original firmware AND flashed with the RouterTech firmware... all of these devices ran DHCP and all of these devices had the same issue. DHCP only worked properly with the 2wire device.

Just to make things stranger- sometimes after a reboot it works between one host or two, but then it stops working (usually after another restart). :/ I dunno what's going on. 

Things I've done to try and make it work:

- Swapping various modems, all set to DHCP. Nothing worked.

- A lot of kerfutzing around with various files, trying to make it work (based on suggestions found elsewhere on the 'net). Most notably /etc/nsswitch.conf and /etc/dhcp3/dhclient.conf; but all Ubuntu machines are now running identical copies of these files and I'll provide them below for analysis.

- Set each machine's dhclient.conf to send their own host name (eg 'tymanther') rather than <hostname>. This had no effect.

Any idea what could be wrong?

[quote="/etc/nsswitch.conf"]
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files wins dns
networks:       files wins dns

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
[/quote]

[quote="/etc/dhcp3/dhclient.conf"]
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "tymanther";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu,
	rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
[/quote]

---

### Post by Sasayaki on 2009-11-09
What. -_-;

Well, I spent all weekend trying to narrow it down, track down various modems etc... then gathering all the above information and making this post... turns out about 5 minutes after I made it I figured it out. The issue lay with Samba; making sure that the lines "dns proxy = no", "wins support = no" and "wins server = w.x.y.z" were commented out seems to have fixed the problem completely.

Heh... oh well. At least I learned a fair bit about Ubuntu's networking! (and how it can be messed up...)

Hope it helps others further down the track.

---

### Post by Iowan on 2009-11-09
So this one is [SOLVED]?
(Thread Tools)

---

