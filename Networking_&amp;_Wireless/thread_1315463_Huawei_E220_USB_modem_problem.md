---
title: "Huawei E220 USB modem problem"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by petermoffat on 2009-11-05
I've read a bunch of things about this, but nothing seems to match my problem exactly..

The modem sort of works, it connects and then disconnects and 'disappears' then connects again (if I have it on auto connect).

Has anyone found a fix for this yet?

**EDIT**

SOLVED

I found a fix!

Download the firmware updater at [http://www.maxis.com.my/maxisbb/download/E220SoftwareUpgrade.zip](http://www.maxis.com.my/maxisbb/download/E220SoftwareUpgrade.zip) and run it under XP.

---

### Post by meeya on 2009-11-05
I'm using the same modem on ubuntu 9.10 64 bit version, mine gets connected but the applications does not get connected to the INTERNET until you disconnect and connect several times. This did not happen in 9.04 32 bit version.
One bro has the same problem and he is using another type of HSPDA but still on 9.10 which he didn't have in 9.04.

---

### Post by CbrPad on 2009-11-05
I can eventually get mine going by this...

sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x1003
sudo pppd ttyUSB0

However, it can take ages plugging and out and doing the rmmod before it finally works - it's sometimes taken me over half an hour, and then my network drops the connection and the only way to get it back is to do it all again, but your mileage may vary !  

IMO it isn't worth the hassle and you're probably better off with 9.04 or something else.

---

### Post by petermoffat on 2009-11-05
OK, I think if Karmic consitantly sees your USB dongle, you are fine.

Disconnect connection

System, preferences, network proxy

Click Direct connection and apply system wide

In firefox, go to edit, preferences, advanced, network, settings

select use system proxy

ok

Now connect and it should work

Just sorted this with a mates E220, but for some reason mine doesn't work.. His works fine on mine, and both work fine on his 9.04.. Bugger.

---

### Post by bco on 2009-11-06
Hi  , I have been having problems connecting to Vodafone Mobile on Karmic and tried most of the suggestions on this forum but got nowhere. I then discovered that netmanager defaults to a wired connection when this is available. Disconnected same - internet works perfectly  - reconnected ethernet - internet gone again. Hope this helps

Ubuntu Karmic on PC, Apple Imac

---

### Post by Spin Doctor on 2009-11-07
Check [out  this]("http://ubuntuforums.org/showthread.php?p=8263639#post8263639") post for another possible solution.

---

### Post by John Read on 2009-11-16
Assuming you have installed your Vodaphone (Australia) wireless broadband modem via the Network Manager and are able to get it to "connect" but are still unable to actually connect to any Web sites, etc. then chances are you still have one small step to go. Right-click the Network Manager icon, choose Edit Connections, click the Mobile Broadband tab, click your Vodaphone service (e.g. Vodafone Postpaid), click the Edit button on the right, leave Number set to *99#, set the Username to vodafone, set the password to vodafone, leave APN set to vfinternet, and click the Apply button. You will be asked if it's OK to store some keys on a keyring, choose "At any time" (or somesuch), then you're set.

I find the connection speed I can achieve in Ubuntu 9.10 is several times faster than I could achieve in Ubuntu 9.04 which is just great.

The only hassle I have is that Ubuntu boots so fast that the modem does not have time to find the Vodafone connection and then it won't appear in the Network Manager list. You then have to cold boot again and hope for better luck next time.

Hope this helps.

Regards,

John

---

### Post by petermoffat on 2009-11-17
Loud noises

---

### Post by petermoffat on 2009-11-17
Loud noises

---

### Post by petermoffat on 2009-11-17
Any chance this could be stickied for a while or until the kernel works with the old firmware? I found it very frustrating digging through threads trying to find a solution.

Can anyone else try and confirm if this works?

---

### Post by bbrain on 2009-11-17
I applied this firmware version and although the modem worked it only connected at 56kb/sec Green light.  I tested it on Ubuntu 9.04 as well.  I have two identical devices so switching between them was simple and showed that the new firmware was affecting the connectivity

I put the firmware version back to the original one and it connected at 3G speed again Blue Light.

Anyone any ideas?

---

### Post by alexfish on 2009-11-17
> **petermoffat said:**
> Any chance this could be stickied for a while or until the kernel works with the old firmware? I found it very frustrating digging through threads trying to find a solution.

Can anyone else try and confirm if this works?

can't figure it out  usb-modeswitch installed  does work to a point connects ok
but browser does not connect / I am twitching on this side cos the device manager shows the  a modem but also an ignored device . is the network manager switching between the two devices randomley ???  just don't know

I vote still Sticky

---

### Post by StRobo on 2009-11-18
I have the same problem and it looks like the /etc/resolv.conf link points correctly but does not contain the correct DNS updates.

So something with the network-manager seems to have regressed...

I will continue to look into this but not sure if I will find a solution.

---

### Post by StRobo on 2009-11-18
The easiest solution for the moment seems to simply to
1) Connect the modem (that works for me without problems for some reason)
2) do a sudo dhclient3 in your shell to get the dns name server stuff working.

Surf the web!

---

### Post by petermoffat on 2009-11-18
I've had two completely different issues with two different E220 modems. Mine had the issue described in this post, and would connect and disconnect a few times after I plugged it in, and then disappear from my system, usually switching the modem off (no lights flashing). The firmware update solved this problem, and I'm using it right now.

The other issue I had was using a friends E220, which is much newer than mine. His worked and connected and stayed connected, however, Firefox would not connect to anything. The solution for that was to apply a system wide 'direct connection' in network managers proxy settings, and tell FF to use the system proxy settings.

---

### Post by alexfish on 2009-11-18
> **petermoffat said:**
> I've had two completely different issues with two different E220 modems. Mine had the issue described in this post, and would connect and disconnect a few times after I plugged it in, and then disappear from my system, usually switching the modem off (no lights flashing). The firmware update solved this problem, and I'm using it right now.

The other issue I had was using a friends E220, which is much newer than mine. His worked and connected and stayed connected, however, Firefox would not connect to anything. The solution for that was to apply a system wide 'direct connection' in network managers proxy settings, and tell FF to use the system proxy settings.

thanks i will try this

here is a link to usefull site relating to the usb modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by alexfish on 2009-11-25
try adding ppa   re:   ppa:network-manager link here

[http://ubuntuforums.org/showthread.php?t=1336197](http://ubuntuforums.org/showthread.php?t=1336197)

---

### Post by Ususbuntung on 2009-12-11
Thanks it works for my E220.

---

