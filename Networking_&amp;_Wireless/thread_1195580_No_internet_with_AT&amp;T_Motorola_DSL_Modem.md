---
title: "No internet with AT&amp;T Motorola DSL Modem"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by amder on 2009-06-24
I finally convinced my cousin to convert to Ubuntu but things have not been going smoothly and I need your help.  Specs:

Her ISP and networking setup: AT&T, Motorola 2210 DSL modem
My ISP and networking setup: AT&T, 2wire DSL modem, 5 port Netgear switch
System: Fry's Electronics limited edition custom PC, OS: Ubuntu 8.10 desktop version

We were unable to connect to the internet at her home.  *ifconfig* shows lo, eth0, and eth1 (inet addr 62.xx.xx.xx).  eth0 is the busted onboard NIC.  eth1 is the new NIC which is connected directly to the Motorola modem.  Running *dhclient eth1* did not help either.  The cat5 cable and modem works fine because a Vista laptop was connected and it can go online.  When the computer boots up, it will notify "Connection established.  You are now connected to the wired network."  /etc/network/interfaces:
auto lo
iface lo inet loopback

The strange thing is that when I tested the system at my house, it works fine and I can go online.  It also worked when I tried bypassing the Netgear switch and plugging directly to the 2wire modem.

Googling provided this helpful link but I don't think this is related because the modem is already set up:
[http://ubuntuforums.org/showthread.php?t=896181]("http://ubuntuforums.org/showthread.php?t=896181")

Any help or advices would be greatly appreciated.  I have a hunch it has to do with compatibility issues with the Motorola modem but don't know what to do.

---

### Post by aago1254 on 2009-06-27
try using a live cd and see if it is doing it on a live cd to see if its a setting with in ubuntu.

---

### Post by tgalati4 on 2009-06-27
ATT modems have authentication which requires logging into them and typing in the serial number of the modem and the password of the owner of the account.  

Try logging into the modem at [http://192.168.0.1](http://192.168.0.1) and look at the status.

What do the status lights on the front indicate?

---

### Post by aago1254 on 2009-06-29
i thought the ip to the modem was 192.168.1.254.  the lights should be green on the modem im talking about the dsl light and all. if you are static id make sure your not static and doing dhcp. and by the ip you gave me sounds like your connected to a router of some kind.

---

### Post by amder on 2009-07-01
Thank you aago1254 and tgalati4 for your replies.  Unfortunately, we were fed up with the back and forth and back and forth with ATT tech support and my cousin reinstalled Win XP.  It turns out that that specific model will not work with Ubuntu.  I was going to try Slax or another live CD but oh well.  

We didn't test for internet connectivity with the Ubuntu live CD.  Yeah, that's what made me scratch my head too.  The ip from ipconfig was a weird ip.  If I remember right, there are three green lights that were lit.  The fourth one, internet, never lit up.  The fifith one, status/activity, which usually blinks is never lit.  I think the ip is not static, DHCP from ATT.  We couldn't log in to the modem to authenticate because we forgot the username and password.  We had to go through a tedious process to get those info again and that was why my cousin went back to Windows.

Thanks for your help.

---

