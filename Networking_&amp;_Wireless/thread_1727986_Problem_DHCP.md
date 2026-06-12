---
title: "Problem DHCP"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by deus16 on 2011-04-13
THis is dhcpd.conf
#
# DHCP Server Configuration file.
# see /usr/share/doc/dhcp*/dhcpd.conf.sample
# see 'man 5 dhcpd.conf'
#

allow bootp;
ddns-update-style ad-hoc;

option browser-portal-page code 224 = string;
option browser-portal-page "cms_fe";
option provisioning code 225 =string ;
option provisioning "192.168.100.20";
#option browser-portal-page "http://192.168.100.17";

#option browser-portal-page "http://192.168.100.17/video.html";
#option browser-portal-page "http://192.168.100.214/test.html";
##### Class "Xavi"
class "Xavi"
{
match if (substring(hardware,1,3) = 00:01:38) or
(substring(hardware,1,3) = E0:91:53);
}
##### Class "jao"
class "jao"
{
match if (substring(hardware,1,3) = 00:04:5F);
}

subnet 192.168.100.0 netmask 255.255.255.0 {
option routers 192.168.100.254; # passerelle par défaut
option subnet-mask 255.255.255.0; # masque de sous-réseau
option domain-name "setupbox.lan"; # nom de domaine
option domain-name-servers 192.168.100.201;# serveurs DNS


# Pool Xavi
pool
{
allow members of "Xavi";
range 192.168.100.233 192.168.100.233;
default-lease-time 10;
}

# Pool jao
pool
{
allow members of "jao";
range 192.168.100.234 192.168.100.234;
default-lease-time 10;
on commit {
set provisioning = provisioning;
execute("/tmp/dhcpcommit.sh", "commit", provisioning);
}
}


}
Could someone help me to write this script dhcpcommit.sh permetrra to write the information provisioning (option creates) a text file. Thank you

---

