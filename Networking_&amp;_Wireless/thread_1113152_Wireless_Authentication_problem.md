---
title: "Wireless Authentication problem"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by phree on 2009-04-01
Hi, I'm new to Ubuntu but not to linux. I have just installed Ubuntu on an old Toshiba which has a built in Inprocom IPN 2220 card. After the usual messing with Ndiswrapper it is now recognised bt the O/S. 

My problem is this, I tried connecting to my wireless netgear router which has  WPA-PSK [TKIP] + WPA2-PSK [AES] enabled. I get the 2 little green blobs near the clock and the spinning thing to show its trying, but it fails saying it need the pass key. 

After enterning the key several times, I decided to diable  WPA-PSK [TKIP] + WPA2-PSK [AES] authentication, and viola, the thing connected up and was operating fine.

I reenabled authentication and rebooted everything, but it failed to connect having authentication problems again. 

When I type the passphrase in, it is in clear text and is correct. When it fails and the dialogue box comes up, I click on show passphrase and it comes back a a string of numbers; this could be just how linux handles the passphrase but am not sure.

Has anyone else had this problem and if so what have they done to get around it?

rgds Phree

---

### Post by sgosnell on 2009-04-01
What version of Ubuntu?  There is a bug in 9.04 beta that causes this.  On 8.10 it's caused by some wireless adapters, and there are workarounds for it.

---

### Post by phree on 2009-04-01
Hi, its 8:10. I have an inprocomm IPN 2220 internal Wireless lan adapter sat in a toshiba L10. 

Any help would be appreciated. 

cheers Phree

---

### Post by sgosnell on 2009-04-02
Try [this troubleshooting guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  It may help.

---

### Post by kilgore9 on 2009-04-02
Hi I've been having a similar problem, only with my WEP key.  (I'm sure you've seen my thread floating up there..)
How did you turn off the WPA security?  Is it something you have to do in the router or is it somewhere in Ubuntu?

---

### Post by phree on 2009-04-02
Kilgore9, yes, you go into your routers configuration and disable it. I would'nt recommend doing it other than for testing purposes, re-enable once the test has been proven.

Sgosnell, I'll give the workaround a go thanks.

rgds Phree

---

### Post by phree on 2009-04-03
Sgosnel I tried everything in the guide, had a few problems which i think I resolved but I still cannot connect when WPA is enabled. 

I think I am a little further in that message i now get from the network manager start with 'Attempting to join wireless network 'xxxx'' an then change to getting address from the router, however at this point it fails.

Anyone got any further suggestions for this?

rgds Phree

---

### Post by phree on 2009-04-03
A bit more info.

If i just log in normaly and then try to connect, I dont get anywher. If I log in and then run wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf at a terminal, I get a connection but it times out when trying to obtain the IP address from the router.

If i run dhcpcd wlan0, an ip is allocated but it isnt from my pool, i'm not sure where it is being allocated to but its not in my network and so i still cannot conect to my router.

rgds Phree

Oh, and if i run iwconfig wlan0 it tells me that the access point is not associated

---

### Post by kilgore9 on 2009-04-04
Hey Phree....
Thanks for  the tip on configuring the router.  I did this.  Then on a whim I tried installing wicd to replace network manager.  With wicd I was connecting using my key within seconds.... weeks of frustration solved with one simple thing!
so download wicd in the synaptic, maybe it will work for you too!

---

### Post by phree on 2009-04-04
Hi Kilgore9, I downloaded wicd and installed it. My problem has moved on from wpa authentication to IP assignement and wicd experiences the same problem and nm did.

Symptoms are,

I click connect in wicd (or nm) and I get validating authentication message, this then quickly becomes an obtaining IP address message. I am assuming from this that my WPA authentication is now working and that my problem now lies with IP address allocation (DHCP) but I am struggling to find out what the problem actualy is.

Incidently, I think the wpa issue is to do with the passphrase. I used wpa_supplicant passphrase to generate a hex string of my ascii key. I then put this in the password box and it seemed to work.

Any DHCP specialists out there ???? help !""

---

### Post by elhunko on 2009-10-23
phree, did you ever figure out what was going on?  I pretty much experienced all the same things you did and am still stuck.

---

