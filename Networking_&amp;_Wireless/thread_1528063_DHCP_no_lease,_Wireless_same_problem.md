---
title: "DHCP no lease, Wireless same problem"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by blastinc on 2010-07-10
Hi guys,

i am familiar with Linux used in the past OpenSUSE and BackTrack. A friend of mine told me that Ubuntu should be also a great distribution and gave me the 10.04 Desktop Alternate on a CD.

Yesterday evening decided to install it. Got 40 Gigs free for in so ran the installation, everything went smooth until the point with the Network adapters came.

I have a Gigabit onboard Realtek and Linksys wireless with Atheros chipset which i use for WEP cracking.

Ubuntu was able to determine exactly the types of the adapters and of course i told it to try to get a DHCP lease from my router which is ASUS RT-N16 with DD-WRT flashed on it. Just to tell that the router works perfectly and when i am under WinXP i get my addresses immediately.

Then back to Ubuntu. No success getting IP for the wired connection tried then the WLAN one, the same result ok then i decided to continue the installation without configuring them and to make the configuration through a terminal later.

Everything installed perfectly logged in tried the graphical tool with no success, tried the DHCP tool over terminal again no success after 5 or 6 intervals is going to sleep.

Then i made a static IP configuration i get connection to the Router, can lod to it throug ssh and WEB but no Internet connection again.

And to be honest i am buffed. I do not understand why the DHCP tool is telling me that there is no DCHP offering when every other station in my network is getting this offers and the same machine as well but under WinXP even my PSP which is again some kind of BSD based and my iPod are getting DHCP leases from my Router.

Anybody any clue !?

when i input : sudo dhclient eth0

i get this response:

Listening on LPF/eth0/00:23:54:.......
Sending on LPF/eth0/00:23:54:.......
Sending on Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

