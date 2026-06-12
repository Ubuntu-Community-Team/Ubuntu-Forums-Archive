---
title: "Linksys WPC54G ver 1.1 issues"
date: 2006-05-23
forum: Networking &amp; Wireless
---

### Post by lorenzo111 on 2006-05-23
Ok ran into a problem had a pcmcia linksys wpc 11 ver 3 working great but its 802.11b so wanted to upgrade to G so I got a linksys WPC 54G ver 1.1 after reading ppl had success with them.

status report where I'm at now

installed ndiswrapper-source, ndiswrapper gtk, ndiswrapper-tools via synaptic everything went fine

installed the lsbcmnds.inf file into ndiswrapper used the version 1.3 from ndis wrapper website which everyone got to work but me go figure everything went fine

when I do ndiswrapper -l
I get lsbcmnds driver present hardware present a good sign

after that i edited /etc/network/interfaces like the guide i read said to do

this is where im stuck at cant connect to internet just stuck in the water at this point

really would like to get this G working any help would be much appreciated


P.S. I running a freshly upgraded Brezzy

---

### Post by Titus A Duxass on 2006-05-24
Disable any other cards i.e. eth0 then do a cold start.

---

### Post by jml on 2006-05-24
I would also suggest that you try to set up an unencrypted wireless connection first.  Then add WEP encryption if you want it.  By the way, WPA encryption is not supported by Ubuntu 5.10 out of the box.  If you want/need it, you will have to download, install and configure an application called wpa_supplicant.

Joe

---

### Post by lorenzo111 on 2006-05-24
deactivated everything except the G card seeing it as wlan0 and did a cold start it shows up in my network window but after I configure it it just hangs on activation screen and does nothing.

tried configuring from CLI but it still doesnt take

---

### Post by lorenzo111 on 2006-05-31
anyone out there have any suggestions?

havent been able to lick this problem yet

---

