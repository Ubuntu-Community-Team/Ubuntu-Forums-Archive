---
title: "Network manager driving my router wild."
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by EMulligan on 2010-10-27
I recently installed Edubuntu 10.10 (unpartitioned) on a HP Compaq nc2400 ([spec]("http://h18000.www1.hp.com/products/quickspecs/12439_na/12439_na.HTML")). The wired interface is the Broadcom and the wireless is Intel PRO.  The communications worked "out of the box" almost.  It recognised both interfaces and I was quickly able to connect to my router and my adsl modems admin pages.  However going beyond that was painfully slow. With the help of this and other forums, I was able to diagnose this as related to the auto generation of resolv.conf by network manager.  by changing the settings for the connections in network manager (dhcp addresses only), I was able to get it to generate a resolv.conf with my ISP's DNS server addresses.  This sorted that problem.

The next problem that arose was that after an hour or two on-line the network manager would drop the wireless connection and keep asking me for the WEP key (128 bit).  When it would not reconnect, I tried the wired connection.  This also failed to connect.  In addition, any other (windows based) PCs on the network were getting no response from the router.  I had to restart the router to restore the connections.  It would usually fail again in a shorter timeframe after that.  I have not been able to recreate the problem using the edubuntu machine with the wired connection.  The problem has never occurred when the edubuntu machine is not connected.  it would appear that the edbuntu machine, when wirelessly connected, is doing something which sends my router into a tizzy.  Shutting down the linux machine does not sort the problem but restarting the router does.  The time lapse suggests a hardware problem which appears when components heat up.  If that were the case, shutting down the linux machine should fix it if the problem were there.  If the problem were with the router then I would expect it to happen even when the linux machine is not connected and to relate to the amount of time the router was running.

I have not tried managing the connection from the command line.  I'm not really a command line kinda guy (I've never used linux before, It's over 20 years since I used unix and probably 15 since I used dos last).  My objective is to get an "it just works" version of linux (So far edubuntu seems to be living up to this). so I'd like to sort this in a way which allows me to continue to use the GUI tools to manage the system.

Has anyone come across this problem before?  Any suggestions on how to sort it? My router is quite old (Netgear Mr814 802.11b) as is my adsl modem (a 6 to 7 year old netopia).

Éamon

---

### Post by EMulligan on 2010-11-09
I am a bit disappointed that no one has been able to help me on this.  Since posting, I have ahd the opportunity to use the edubuntu laptop in another location.  in the other location was a netopia router modem using WPA and 802.11g.  Could the problem be related to the netgear, 802.11b or WEP?

---

### Post by grahammechanical on 2010-11-09
I haven't a clue! I, too like to use GUI tools. Network manager is not dropping the connection. The modem is. This is why network manager asks for authentication (WEP key). It is trying to re-establish the connection to the modem. You say:

> In addition, any other (windows based) PCs on the network were getting no response from the router

People who post questions on this forum usually say that the connection works fine in Windows or that others who use Windows can connect to the Internet with no problems. It is just 10.4 or 10.10 that has the problem.

My guess is that the modem is failing. Do the indicator lights on the thing give you any indication that the modem is not working as it should? Or perhaps you should monitor what the router is doing.

Regards.

---

### Post by toekneewood on 2010-11-09
The problem you mention with having to keep putting your WEP key in and loosing connection rings a bell with me.  In the past I had this problem if my SSID was hidden.  If it is hidden then allow it to broadcast.

---

### Post by EMulligan on 2010-11-09
It appears to be a problem in the interaction between the router and the ubuntu.  The problem never arises when only windows machines are connected. It never arises when the ubuntu is connected by wire.  At the other location, I had no problem with the netopia router modem.  When the problem does arise with the netgear router, it shuts out all connections, wired, wireless, ubuntu and windows.  So the problem appears in the router but Ubuntu appears to be part of the cause.

---

### Post by EMulligan on 2010-11-09
SSID is broadcast.  At work was able to connect to a wep key hidden SSID.  I haven't really been able to test it out because I cannot get the DNS to work.

---

### Post by toekneewood on 2010-11-09
check that the router MTU size it at 1500 and I found this link that might have some tips
[http://www.questionhub.com/?keyword=netgear-mr814]("http://www.questionhub.com/?keyword=netgear-mr814")

---

### Post by iponeverything on 2010-11-09
See if there is firmware upgrade for the router -- and if you have the option -- don't use wep. (wep is just hair better than no encryption)

I would wager that if you turned off wep the router would stop crashing with the linux client. Issues like this are not uncommon - i.e. a buggy implementation in router firmware that conflicts with certain clients.

---

### Post by EMulligan on 2010-11-09
The consensus appears to be that the problem lies with the router.  I sorted the DNS problem with the router at work and have been using that for over two hours now with no problem.  It also uses 128 key WEP (albeit 802 11g - 54mbps) so that does not appear to be the problem.  That appears to narrow it down to the Netgear router (or perhaps 802.11b - 11mbps).  I don't think it has had any firmware upgrade since it was bought - don't fix what isn't broken - so I might take the suggestion to look for a firmware upgrade.

Thanks everyone for your input.

---

### Post by EMulligan on 2010-11-09
The latest version of the firmware is [5.3_05]("http://kbserver.netgear.com/release_notes/D102358.htm") dating from June 2004.  This is already installed.

---

### Post by EMulligan on 2010-11-12
Switched the WEP mode from automatic to open system on the Netgear (this is the default when setting up on both windows and ubuntu).  Then switched wep off altogether. Neither worked.  Looks like it's an incompatibility problem between Netgear MR814v2 with 802.11b and Ubuntu.

---

### Post by EMulligan on 2010-11-14
Tried setting MTU to 1500.  It was working for most of the morning (2-3hours) without incident.  However it eventually failed.  Again no other connection could be made until the router was switched off and on again.  Best performance so far, though.  Thanks for the suggestion Tony.

---

### Post by EMulligan on 2010-11-19
Booted another laptop with Edubuntu using the live cd.  A HP Pavilion dv1355.  It worked perfectly and gave no problems.  I used it for a total of 6 hours browsing the Internet.  The longest session was 3 hours.  I also has an Intel PRO/wireless but it's a 2200BG (rev 05).  The driver used by ubuntu is IPW2200.  The machine causing the trouble has an Intel PRO wireless 3945ABG (Rev 02).  The driver used by ubuntu is iwl3945.

It appears that the problem is specific to the iwl3945 driver and the netgear MR814v2 router.

---

