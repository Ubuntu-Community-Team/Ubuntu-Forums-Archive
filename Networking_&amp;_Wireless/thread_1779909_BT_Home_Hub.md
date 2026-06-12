---
title: "BT Home Hub"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by Don Vosper on 2011-06-11
Hi
Just installed 11.04 on separate hard drive.
All ok apart from wireless connection to BT Home Hub.
It can identify the local wireless networks and can see my own Hub but will nort connect to it.
It will,however, connect to a nearby BT Openzone hub but all I can get on that is the BT website, obviously hoping fopr me to subscribe!.
I'm guessing that the problem is due to the way Ubuntu 11.04 is failing to accept the WPA key code for the Hub.
The same computer and hardware works fine on XP with the wireles connection via the BT Home Hub.
I did have Version 10.1 working on this computer on the internet as well but since then I have changed over to BT.
I see a few others have had problem with the BT Hub.
I wonder if anyone can shed any light on this?
Cheers
Don,
Bristol UK

---

### Post by TooFarNorth on 2011-06-11
I am having very similar problems, i was trying to get wireless on an acer aspire one D255E, and have been trying to reinstal drivers to see if that would fix the problem. The router i have is a BT Home Hub 2.0 and neither the wireless or wired networks seem to work. I have yet to try with a different router.

Is the problem a home hub thing or my drivers? 

Thanks

---

### Post by Don Vosper on 2011-06-11
I have had a look on a BT Forum.
Others are having problems with BT HomeHub2 and Ubuntu.
Seems to coincide with a firmware upgrade as far as I can gather.
Nothing seems to have been done about it so far.
I get the impression from what I read that BT are not interested unless its windows.
I wonder if anyone here is using a BT HomeHub2 that actually works with the wireless connection?
Don

---

### Post by Don Vosper on 2011-06-11
Just spent 20 minutes on the phone to BT tech support.
Most of which was on hold.
Tested line and said that the line was ok but they can't help with Linux as they are not trained.
The operator was kind enough to give me a telephone number of a tech support company who would investigate the problem and charge me for their time though.
What service!
Cheers
Don

---

### Post by Don Vosper on 2011-06-12
OK try this:
Right click on Network manager.

Click on Wired or Wireless tab as appropriate.

Click on the connection you want.

then click on ADD.

Under IPv4  settings enter the following info:-

IP Address-   192.168.1.xx (Last two digits any available  address on your network) I haven't a clue so I just typed 13, worked for me!

Subnet mask- 255.255.255.0

Gateway-       192.168.1.254

DNS server- 192.168.1.254

When I clicked on "save" it connected automatically.

I'm using it now.
When I get on my wired pc I'll sent a link to the BT forum from where I got it in case I've miss-typed anything.

Don

---

### Post by Don Vosper on 2011-06-12
[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9)

here is the link.
The first bit didn't work for me but the second part was fine.
Don

---

### Post by makavell1 on 2012-01-04
Hi, New to the forum and Ubunto.

I have a Homehub 3 and was having problems connecting. 

I had given up on connecting to the home hub until I bought a wireless printer to use with idevices that didn't work either.

I have changed the hub security settings to WPA only and taken off the smart channel selection (selected channel 6) and everything seems to be working fine, not only with the printing from idevices but also with my connection to the internet.

Could anyone advise me on whether I have compromised the security of my network by changing the security settings or if this is a valid work around?

Thanks in advance.

---

