---
title: "Problems with DSL Router, DHCP, IPv6 &amp; Ubuntu Hoary"
date: 2005-01-10
forum: Networking &amp; Wireless
---

### Post by rob martin on 2005-01-10
I've been lurking here since yesterday pm in the hope that someone would post a solution to my problems, alas, no one has.  There does seem to be a rash of similar problems around the theme of "NIC or eth0 can't connect".  So here is my  tuppence.

I'm running a Hoary laptop (IBM R31 - yes I know about the ACPI problems, have every confidence that Paul Sladen will get it working ;)  after updating the slew of packages yesterday, my laptop refused to assign itself an IP address from my DLink router.  Yes I know it has a problem with DNS, which I have fixed and up until yesterday it was not a problem so I can rule that one out.

I can 
sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0 broadcast 192.168.1.255
 ifconfig eth0 up
route add default gw 192.168.1.1

to get back on the network (hence this posting) but I'm keen to find out why this "feature" has only recently occurred.  

The e100 is recognised at boot the module is there in the lsmod output, lspci lists it too.

lspci : 
0000:01:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
lsmod :
e100                   33920  0
mii                     4896  1 e100

less /var/log/messages gives the following
Jan 10 20:38:43 localhost kernel: e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex ..... (stuff you don't need)....
Jan 10 20:39:18 localhost kernel: Disabled Privacy Extensions on device c030fb40(lo)
Jan 10 20:39:18 localhost kernel: IPv6 over IPv4 tunneling driver

less /var/log/syslog gives lots of these 
Jan 10 21:07:29 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan 10 21:07:34 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan 10 21:07:40 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan 10 21:07:50 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan 10 21:08:00 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Jan 10 21:08:21 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jan 10 21:08:30 localhost dhclient: No DHCPOFFERS received.
Jan 10 21:08:30 localhost dhclient: No working leases in persistent database - sleeping.

(come back to this in a minute)

when I check ifconfig on reboot I only have an IPv6 address no IPv4 eg 192.168.1.*
 
So I tried to stop the loading of the IPv6 module by editing /etc/modutils/aliases and uncommenting the IPv6 line - didn't work, am I missing a step here?

then I re-read man dhclient, the port for DHCP requests is 68 why is my Ubuntu box trying to find a DHCP server on port 67?

So there you are, a nice puzzle on a Monday night, any help would be gratefully received.

rob

---

### Post by rob martin on 2005-01-11
**GROVEL:**
 To creep on the earth, or with the face to the ground; to lie prone, or move uneasily with the body prostrate on the earth; to lie fiat on one's belly, *expressive of abjectness*; to crawl. 

Resolved the problem.... sometimes restarting appliances works. 

I turned the adsl modem off, waited a minute, turned it back on, rebooted computer and it worked.  

Off to hide my head in shame and disgrace  :oops:

Thanks to everyone  who took the time to read the posting, when next I encounter a problem I will re-read this and try the off button.


rob

---

### Post by hardcandy on 2005-01-11
That's OK, I rebuilt several kernels, reinstalled Slackware several times and waited for an answer from different forums for a couple of days because my sound was not working. I was going to install a   new sound card and discovered the speaker cable was unplugged. :oops:

---

