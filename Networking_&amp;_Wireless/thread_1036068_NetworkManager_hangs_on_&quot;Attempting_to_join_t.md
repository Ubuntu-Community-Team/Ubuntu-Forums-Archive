---
title: "NetworkManager hangs on &quot;Attempting to join the wireless nework&quot;"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by gimlan824 on 2009-01-10
I'm using Ubuntu 8.10 on a Toshiba Satellite a215-s4807 with an Atheros wireless card. I'm picking up all the wireless connections around me, however when I actually attempt to connect to one, NetworkManager will hang on "Attempting to join the wireless network" for a while, then a window will pop-up asking for the the Security Key (the network uses WEP encryption), I enter in the key and hit OK. Then it hangs on "Attempting" again and will ask for the Key again. This cycle will continue until it eventually just fails.

I originally had an earlier version of Ubuntu installed on my computer (7.10) and I had a similar problem but changing the Security Type to a different WEP solved the problem, but here that isn't working. I've found several others with this issue online but haven't seen anyone get it fixed. Any help would be much appreciated.

---

### Post by daal21 on 2009-08-25
I have a similar problem. *My wireless card is a D-link dwl-122 
usb stick. *My router is using a 128 bit password (13 letters/numbers).* Ubuntu requests a 40/128 bit HEX password or a 128 bit passphrase. *I assume the passphrase is what I should check. *But no luck. *As with the OP it attempts and fails. *I am new to Linux and have been struggling with this for several weeks. *I'd appreciate any input...

Thanks,

---

### Post by caz162 on 2009-10-30
Has anyone found a solution to this problem. Im trying to connect to my wireless network. It asks me for the WEP key and i enter it correctly then a few minutes later it asks me again and again then fails.

---

### Post by gumshore on 2009-10-30
I have had this problem since 9.04. I am using a Gateway MT6458 with a Marvell Topdog using the Netgear WN311T drivers. Here is [a link the thread I started]("http://ubuntuforums.org/showthread.php?t=1303957")

---

### Post by gumshore on 2009-10-30
> **gimlan824 said:**
> I'm using Ubuntu 8.10 This actually the last version for me that DOES NOT have this problem, so I have been forced to use It even though It is a bit old.

---

### Post by lunanueva on 2009-10-30
That is the same problem i am having after upgrading from 8.10 to 9.04...i was hoping that problem would have been fixed by now, but apparently it still happens to some of us.  i need a solution, i do not want to go back to 8.10  ...

---

### Post by gumshore on 2009-10-30
I have been looking into this with my limited knowledge of Linux networking and have tried to use the 8.10 versions of network manager on 9.10, and that does not work. I also tried to remove network manager and replace it with Wicd, but Wicd would not even detect networks present with ndiswrapper. I have yet to try it with my external wireless device, but I can't lug my laptop around with that plugged in constantly, and I am in no position to spend money to replace the internal wireless card. I really need this fixed ASAP!

---

### Post by brandon88tube on 2009-10-30
Same issue, but I believed it worked out of the box in 9.04

If anyone is interested my card is a d-link dwa-140 usb adapter(Ralink 802.11n)

---

### Post by lunanueva on 2009-10-30
I know what you mean gumshore.  I want this fixed too, but my knowledge is very limited so i'm depending pretty heavily on the ubuntu community right now.  :confused:

---

### Post by a.malcolm.stanley@gmail on 2009-10-30
I have the same problem.
Here is a log of what is going on:
```

Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) starting connection 'Auto 7LQ21'
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto 7LQ21' has security, but secrets are required.
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
ct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) starting connection 'Auto 7LQ21'
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...

Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto 7LQ21' has security, and secrets exist.  No new secrets needed.
Oct 30 23:20:42 marquesas NetworkManager: <info>  Config: added 'ssid' value '7LQ21'
Oct 30 23:20:42 marquesas NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 30 23:20:42 marquesas NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Oct 30 23:20:42 marquesas NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Oct 30 23:20:42 marquesas NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Oct 30 23:20:42 marquesas NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Oct 30 23:20:42 marquesas NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 30 23:20:42 marquesas NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 30 23:20:42 marquesas NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 30 23:20:42 marquesas wpa_supplicant[1030]: CTRL-EVENT-SCAN-RESULTS
Oct 30 23:20:42 marquesas wpa_supplicant[1030]: Trying to associate with 00:1f:5b:88:2e:8d (SSID='7LQ21' freq=2437 MHz)
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct 30 23:20:42 marquesas wpa_supplicant[1030]: Association request to the driver failed
Oct 30 23:20:42 marquesas wpa_supplicant[1030]: Associated with 00:1f:5b:88:2e:8d
Oct 30 23:20:42 marquesas wpa_supplicant[1030]: CTRL-EVENT-CONNECTED - Connection to 00:1f:5b:88:2e:8d completed (reauth) [id=0 id_str=]
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '7LQ21'.
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct 30 23:20:42 marquesas NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Oct 30 23:20:42 marquesas dhclient: Internet Systems Consortium DHCP Client V3.1.2
Oct 30 23:20:42 marquesas dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct 30 23:20:42 marquesas dhclient: All rights reserved.
Oct 30 23:20:42 marquesas dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct 30 23:20:42 marquesas NetworkManager: <info>  dhclient started with pid 2188
Oct 30 23:20:42 marquesas dhclient:
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Oct 30 23:20:42 marquesas NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 30 23:20:42 marquesas dhclient: Listening on LPF/eth1/00:12:f0:00:b6:ae
Oct 30 23:20:42 marquesas dhclient: Sending on   LPF/eth1/00:12:f0:00:b6:ae
Oct 30 23:20:42 marquesas dhclient: Sending on   Socket/fallback
Oct 30 23:20:42 marquesas NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
Oct 30 23:20:44 marquesas dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Oct 30 23:20:50 marquesas dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Oct 30 23:20:55 marquesas wpa_supplicant[1030]: CTRL-EVENT-SCAN-RESULTS
Oct 30 23:20:58 marquesas dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Oct 30 23:20:59 marquesas wpa_supplicant[1030]: CTRL-EVENT-SCAN-RESULTS
Oct 30 23:21:11 marquesas dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Oct 30 23:21:28 marquesas NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.
Oct 30 23:21:28 marquesas NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 2188
Oct 30 23:21:28 marquesas NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Oct 30 23:21:28 marquesas NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
Oct 30 23:21:28 marquesas NetworkManager: <info>  Activation (eth1/wireless): could not get IP configuration for connection 'Auto 7LQ21'.
Oct 30 23:21:28 marquesas NetworkManager: <info>  (eth1): device state change: 7 -> 6 (reason 0)
Oct 30 23:21:28 marquesas NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets
Oct 30 23:21:28 marquesas NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Oct 30 23:21:36 marquesas NetworkManager: <info>  (eth1): device state change: 6 -> 9 (reason 7)
Oct 30 23:21:36 marquesas NetworkManager: <info>  Activation (eth1) failed for access point (7LQ21)
Oct 30 23:21:36 marquesas NetworkManager: <info>  Marking connection 'Auto 7LQ21' invalid.
Oct 30 23:21:36 marquesas NetworkManager: <info>  Activation (eth1) failed.
Oct 30 23:21:36 marquesas NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Oct 30 23:21:36 marquesas NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Oct 30 23:21:36 marquesas wpa_supplicant[1030]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```Basically, it is associating fine with the access point, but for some reason DHCP is timing out and when that fails you go into the loop. 
So it looks like to me (or at least, for me) the problem is NOT with wireless, it is with DHCP.

Anybody have a clue about how to fix this?

---

### Post by Cypher1101 on 2009-10-31
I'm also having the same issue with a broadcom wifi card on a fresh karmic. It says its connecting to my WAP, but keeps asking me to input my pass without getting any further.
Since I never had jaunty on this old laptop i just started playing around with, I think I'll reformat and throw 9.04 on it to see if I can make it work. I've tried both ndiswrapper and fwcutter and neither seem to work.

Also, does anyone else have a list of ASCII garbage text showing up in their available wireless network list?

---

### Post by lunanueva on 2009-10-31
[/QUOTE]Basically, it is associating fine with the access point, but for some reason DHCP is timing out and when that fails you go into the loop. 
So it looks like to me (or at least, for me) the problem is NOT with wireless, it is with DHCP.

Anybody have a clue about how to fix this?[/QUOTE]


ya, i agree that it is not a wireless problem, but a communication problem.  either way, i am still lost.

---

### Post by gumshore on 2009-10-31
so does anybody think that we should file a bug report on this in Launchpad?

---

### Post by brandon88tube on 2009-10-31
I would say if you feel like it make a bug report, but give details otherwise it won't get fixed.

---

### Post by gumshore on 2009-10-31
> **brandon88tube said:**
> I would say if you feel like it make a bug report, but give details otherwise it won't get fixed.
If I was to report this as a bug, what details should I give? what package does this concern, and what Ubuntu versions should I mark. I only ask because I have not actually filed a bug before, and I dont want to screw it up. I would actually be more comfortable if someone else filed the bug.

---

### Post by brandon88tube on 2009-10-31
I'm not really sure myself what you would list it under etc. I would however say exactly what is happening such as "When trying to connect wirelessly, I constantly get asked to provide my wireless key, but it ends up failing and asking me over and over again as it gets stuck in an endless loop. This has been happening to quite a few people. I am using Ubuntu 9.10 and here are is a copy of my log file. If you need any more information just ask and I will try to provide you with it in hopes of getting this fixed <signed you>." < You can reword it if you want and provide a copy of your log file as I've stated.

---

### Post by gumshore on 2009-10-31
thanks a lot, brandon88tube!

---

### Post by gumshore on 2009-10-31
I have filed a bug report in launchpad

[https://bugs.launchpad.net/ubuntu/+bug/467638](https://bugs.launchpad.net/ubuntu/+bug/467638)

---

### Post by brandon88tube on 2009-10-31
I would suggest 2 things, provide the syslog.log file and change nework to network, lol.

---

### Post by gumshore on 2009-10-31
> **brandon88tube said:**
> I would suggest 2 things, provide the syslog.log file and change nework to network, lol.
thanks. I fixed the name and uploaded syslog

---

### Post by lunanueva on 2009-11-04
awesome job posting the bug.  hopefully we'll get some help soon.

---

### Post by joewein on 2009-11-05
I was having the same problem with the Marvel Topdog wireless adapter once I upgraded from 9.04 to 9.10 on my Gateway M-6750. I couldn't even browse the web on my wired connection afterwards (looks like DNS lookups got broken, but DHCP worked for the IP). 

It kept requesting the password, even though both the DD-WRT router and Ubuntu were configured for WPA2 Personal and the same key. Sometimes it would say it connected, only to report a disconnect soon after.

For lack of alternatives I ended up wiping the Linux partition and reinstalling from scratch. That got me back my wired connection, but not the WLAN access.

I then retraced [my steps](http://www.joewein.net/blog/2008/03/10/first-impressions-of-vista-and-ubuntu/) with which I originally got the XP driver for this device working via ndiswrapper, but no luck under 9.10 so far...

---

### Post by lunanueva on 2009-11-10
i ran the 9.10 live disk to see if it would grant me net access, but no luck.  i was hoping to upgrade and see if this problem would resolve itself.  still seeking the fix.

---

### Post by gumshore on 2009-11-14
OK, THE NEWS (THAT SOME OF) YOU HAVE BEEN WAITING FOR!

I got it working!

If you can, change your wireless network security from WEP to WPA. That is what fixed it for me!

---

### Post by xtbt on 2009-11-16
> **gumshore said:**
> OK, THE NEWS (THAT SOME OF) YOU HAVE BEEN WAITING FOR!

I got it working!

If you can, change your wireless network security from WEP to WPA. That is what fixed it for me!

OK, so you're pretty sure that changing from WEP to WPA is gonna fix this issue ? how many days have you been working with ubuntu without any connection problem ?

I really want to know because my situation is a little different. Let me explain it to you guys and see if any of you have had the same problem.

When I log in, my wireless connection is automatically configured and everything is fine for like 1 hour and then, suddenly, I get disconnected and ubuntu tries to connect again and ask me the WEP key, I write it and click connect, and keeps trying, and trying, and again asks for the WEP key forever and ever. I can't connect to any of my 2 wireless networks anymore. I even tried restarting the network (sudo /etc/init.d/networking restart) with no luck. Only 'temporally' solution is restarting computer (Logging off and on doesn't help).

Thanks in advance,
X-TBT a.k.a. The Mentor.

---

### Post by judytownshend on 2009-11-16
I'm having a similar problem, I connected to wireless with no problem and this was fine for about three days, then suddenly it kept asking me for "WPA & WPA2 Personal" key, which I entered, it carried on trying to connect and then kept asking for the key again and again. When I upgraded to 9.10 I thought this would fix it but no luck. I don't understand why it worked for a few days and then just stopped! I have tried to connect to two different wireless networks and the same thing has happened each time.

---

### Post by aquavitae on 2009-11-16
> **judytownshend said:**
> I'm having a similar problem, I connected to wireless with no problem and this was fine for about three days, then suddenly it kept asking me for "WPA & WPA2 Personal" key, which I entered, it carried on trying to connect and then kept asking for the key again and again. When I upgraded to 9.10 I thought this would fix it but no luck. I don't understand why it worked for a few days and then just stopped! I have tried to connect to two different wireless networks and the same thing has happened each time.

What make & model is the wireless router you're trying to connect to?  Can you access its web interface (usually [http://192.168.1.1)?](http://192.168.1.1)?)

---

### Post by judytownshend on 2009-11-16
The wireless router is a BT Voyager 2100 (Wireless ADSL). I have access to its web interface.

---

### Post by xtbt on 2009-11-16
Ok now the network manager is a little creepy. All the wireless networks I detect in the area seems to be less strong in Ubuntu and stronger in Windows 7 (I'm not making any comparison, I'm just making it clear).

I'm really, sincerely thinking in moving completely to Ubuntu and say goodbye to Windows (For personal use), but these things keep happening.

Another thing is that when I'm connected, the signal suddenly goes to 100%, and then suddenly goes to 5%, and then 30% with all networks (Right now as I type, I'm experiencing that behaviour). I know it's not the wifi adapter because it doesn't happen on Windows 7 (Once again, I'm not comparing in any way, I prefer Ubuntu). When I've been connected like for 1 hour in Ubuntu, it suddenly disconnects and then it won't connect anymore, asking and asking for the WEP key.

My laptop is a ACER ASPIRE 5536 with a AR5B91 integrated module. The loaded wifi modules in Ubuntu are cfg80211->ath->ath9k->mac80211.

Well, I hope someone has some tips to fix this up, maybe I just have to change some modules or something.

Thanks in advance,
X-TBT a.k.a. The Mentor.

EDIT: WOW, just after I posted this message I got disconnected and then it reconnected successfully. It's the first time it happens. Anyway, the signal bars are crazy, 100% then 10% then 5%, etc, etc.

---

### Post by lunanueva on 2009-11-16
> **gumshore said:**
> OK, THE NEWS (THAT SOME OF) YOU HAVE BEEN WAITING FOR!

I got it working!

If you can, change your wireless network security from WEP to WPA. That is what fixed it for me!

is it still working well for you gumshore??

---

### Post by xtbt on 2009-11-17
Well, I followed gumshore's suggestion. I changed one of my AP to WPA and the other one to WPA2. The signal is still week, I haven't got disconnected yet, but I have to use it for a while to tell you if it's finally fixed.

The signal bars are still crazy, 5% then 100%, then 50%, etc,etc. I changed the channel on both AP's as well. No luck.

I hope it stays connected at least. I'll post my results tomorrow.

Well, C-ya later guys. If someone knows the solution to this kind of freaky issue with wireless networking please help us. In my case, fixing this wireless issue will be the final consideration to leave windows forever.

Thanks in advance,
X-TBT a.k.a. The Mentor.

---

### Post by xtbt on 2009-11-17
> **xtbt said:**
> Well, I followed gumshore's suggestion. I changed one of my AP to WPA and the other one to WPA2. The signal is still week, I haven't got disconnected yet, but I have to use it for a while to tell you if it's finally fixed.

The signal bars are still crazy, 5% then 100%, then 50%, etc,etc. I changed the channel on both AP's as well. No luck.

I hope it stays connected at least. I'll post my results tomorrow.

Well, C-ya later guys. If someone knows the solution to this kind of freaky issue with wireless networking please help us. In my case, fixing this wireless issue will be the final consideration to leave windows forever.

Thanks in advance,
X-TBT a.k.a. The Mentor.

Well, I have some results.

**Results for signal going crazy:** When I'm very near of any of the AP's (no more than 5 mts) the signal is stable (75%-85%) but when I move away more than 10 mts the signal starts to go crazy. Take in mind that both AP's are like 30-40mts away from each other. I think the problem is that I have a lot of interference in my house (Paranormal interference maybe ???? :P). It doesn't matter if I have WEP or WPA.

**Results for suddenly disconnection, and refuse of reconnecting:** I changed one of my AP's to WPA and the other one to WPA2. I tested last night the WPA one like 5mts away from the AP. 75%-85% like I mentioned before and everything was ok. Good speed, no lost packets, not any problem, I felt sleep. When I woke up in the morning I checked the signal and it was stable like at night and I was still connected with no problem at all.

I need to check the WPA2 AP today and see if it's ok too.

**Conclusion:**
1.- Wireless connections work better if they use WPA instead of WEP (Which is the default), at least one of mine does (It's a 2Wire), no matter if it's Linux or Windows.

2.- Signal is more stable on Windows than in Linux (at least for both of my AP's) and that's a fact, not a comparison. What do you mean with that? I mean that if I'm using Windows 7 i.e., I can stay connected even if I'm far away the AP. In linux if I get 20 or 25 mts away from the AP the signal starts to go crazy and then suddenly disconnects. The real problem with Ubuntu comes when the Network Manager tries to reconnect, it just keeps asking for the Key again and again. I can't even connect to another AP anymore, only solution is restarting Ubuntu (I tried restarting Network, no luck).

3.- My opinion is that the modules Ubuntu uses for my Wifi adapter are not the appropiates, or maybe they are so generic, and that's why it's not functioning like it has to. Just my thought, I could be wrong.

Well, a lot of write, this is just my situation that maybe would be helpful for some other people out there.

C-ya later,
X-TBT a.k.a. The Mentor.

---

### Post by gumshore on 2009-11-17
> **lunanueva said:**
> is it still working well for you gumshore??
 
The WAP solution has worked well for me. I have been using it with Karmic since the time I made the post with no problems. The network does occasionally disconnect, but I think that is a separate issue not related to this. Wicd might fix this problem, but I have yet to try that. The network only gives me repetitive disconnection like every 1 or 2 days, and a simple reboot is not all that troublesome for me. If I am doing something like compiling source code, I usually right-click on the applet, and disable networking, wait like 5 seconds, and then re-enable it. It's a quick fix, but usefull during the rare occastion that you cannot restart your computer.

---

### Post by judytownshend on 2009-11-19
I've fixed it!!!!!!

Documentation tells me this wireless does not work on Channel 12.
I change it to 11
YEEEEEAAAAAAHHHHHHH !!!!!!!!!

Hopefully this is a fix everyone can use.

---

### Post by pooja on 2009-11-19
How did you solve it? Please post all the steps like it was a "Network management for DUMMIES in Ubuntu9.10"

---

### Post by xtbt on 2009-11-19
> **judytownshend said:**
> I've fixed it!!!!!!

Documentation tells me this wireless does not work on Channel 12.
I change it to 11
YEEEEEAAAAAAHHHHHHH !!!!!!!!!

Hopefully this is a fix everyone can use.

Good for you my friend. Maybe you didn't have any problem related to Linux or your adapter, instead you had a problem related with interference.

Anyway, it's very helpful from your part posting your solution because problems are not always the same even if they have similar symptoms.

I've already changed the channel a lot of times and the result is the same.

The 2wire AP I have is now working 'acceptable' now, I can stay connected if I'm not too far. I have to check the Netgear AP, I just changed it to WAP today (was WPA2 with same problems) to test it all night and post the results in here.

If anyone has any useful information regarding this issue, please share it with us, that's why the forum is here.

Thanks in advance,
X-TBT a.k.a. The Mentor.

---

### Post by gumshore on 2009-11-20
> **xtbt said:**
> Good for you my friend. Maybe you didn't have any problem related to Linux or your adapter, instead you had a problem related with interference.

Anyway, it's very helpful from your part posting your solution because problems are not always the same even if they have similar symptoms.

I've already changed the channel a lot of times and the result is the same.

The 2wire AP I have is now working 'acceptable' now, I can stay connected if I'm not too far. I have to check the Netgear AP, I just changed it to WAP today (was WPA2 with same problems) to test it all night and post the results in here.

If anyone has any useful information regarding this issue, please share it with us, that's why the forum is here.

Thanks in advance,
X-TBT a.k.a. The Mentor.
yes, please post your methods. sharing is what makes the open-source community shine.

---

### Post by xtbt on 2009-11-20
[IMPORTANT UPDATE]
Well people, I'm very exited because I think I finally [SOLVE] my wireless problem under Ubuntu.

After doing several things, from changing the encryption scheme of both of my AP's, to blacklisting the ath*k drivers originally installed and installing Madwifi, I lead to a thread that gave me the solution.

I'm going to divide the post in four parts, my equipment, the initial problem, everything I did to try to fix it, and the final solution.

[B]<EQUIPMENT>
[/B]   Laptop: ACER ASPIRE 5536
   Wireless Adapter: Atheros AR928X
   Wireless AP 1: 2Wire HT-2701 (DSL Wireless Router)
   Wireless AP 2: Netgear CG814GCMR (Cable Wireless Router)
[B]
<INITIAL PROBLEM>[/B]
   Everything started since I fresh-installed Ubuntu 9.10 x64 in my laptop (After fresh-installing Win7).
*NOTE1: Both of my AP's had WEP (I was too lazy to change the default).
*NOTE2: No problems at all with Win7 when I was configuring it/installing the software, updating it, downloading things, watching youtube, etc, etc.
   Since the first boot into Ubuntu, I started to notice some strange behaviour with my wireless connections, the signal went crazy sometimes going down from 85% to 10% with no reason, and then going back to 80%, and after an hour or so it suddenly disconnected ... no matter how far I was from the AP. Sometimes I couldn't even reconnect, like if I just turned off the adapter, giving me the only option of restarting the system. Sometimes, network manager kept asking me for the WEP key.

**<EVERY TEST I TRIED>**
   After following the suggestions of some users of this glorious forum, I did the following:

1) Change auth/enc from WEP to WPA:
   I did it on both of my AP's (from now on AP1 and AP2, look under <EQUIPMENT>). I set AP1 to WPA and AP2 to WPA2. I notice a difference in AP1, as I could stay connected a whole night without a single problem, but, I had to stay no more than 20 meters away. The speed was even better using WAP on AP1, even in Win7. I didn't see any difference in AP2, things were just the same like when it was WEP (good in Win7, bad in Ubuntu). So, since the results where unacceptable I changed AP2 to WAP too and see if I could stay connected several hours like with AP1, but no success.

*NOTE: I have to mention that I notice a gain of speed on both wireless when I changed them from WEP to WPA. You should give it a try if you still have WEP. Also take in mind that WEP is less secure.

2) Replace Network-Manager with Wicd:
   I didn't see any difference by doing this, but I have to say that Wicd has better interface and also, has better network management. It's even more organized so I really recommend it. As I say, it didn't solve anything for my wireless problem but at least I found a better choice.

* EDIT: Before leading to the final solution described at the end, I was trying to connect to my wired network using Network-Manager (I had to switch back from Wicd to Network-Manager to make some tests) and I had some troubles to make it recognize my network. I connected the cable and nothing happened, like if my Ethernet was turned off, very odd. So I really recommend that you give Wicd a try.

3) Replace the ath9k drivers with the Madwifi-ng drivers:
   No luck at all, the wireless adapter was not even detected. I tried to read the Madwifi documentation to see the compatibility list but they were having some server problems (a lot of 404 errors). I check and recheck my installation, the modules were loaded like they had to, so my bet is that my adapter is not yet supported by Madwifi, period. I even went back to Network-Manager (just to see if miracles exist :P) but no luck at all. I had to revert changes and reload ath9k drivers.

4) Again, replace Network-Manager because of some problems with my wired network, like I wrote in the edit before.

**<FINAL SOLUTION>**
   Reading some other threads I had two more things to do. Try the compat-wireless drivers or go back to Intrepid. But suddenly I saw a post where someone said to just install **linux-backports-modules-karmic** and that would fix the problem. So, I gave it a try, anyway, I had nothing to loose.

   I went to Synaptics and installed linux-backports-modules-karmic, restarted the system and ... let me see where's the difference ... same modules, Wicd is acting normal, no error messages, no difference at all so I connected to my AP2 (The more problematic one) and started to watch some videos on Youtube. The signal seems a little more weak than before but surprisingly it is stable as hell (30 mts away and 41%-48%, it's pretty good considering the signal has to travel through some doors, some walls, go outside, get up some stairs, another door and then my lap). I decided to make a final test, leave it connected while I sleep.

   Well, I left it at 10pm of yesterday. I woke up now, at 5am to go to the bathroom, raise the lid and WHALA!!! it's still connected. You can't imagine how good I feel. Now I'm going to have sweet dreams.

   Sorry if it was so long but I did it so I can help someone else with the same problem. I hope this post helps some souls out there and please, always post your result no matter the problem, no matter the method, so we can all help each other.

Sorry for the long post but I had to,
Sincerely,
X-TBT a.k.a. The Mentor.

---

### Post by a.malcolm.stanley@gmail on 2009-11-21
Installing the backports packages did not work for me. 
Wireless still fails while attempting to negotiate DHCP.

---

### Post by xtbt on 2009-11-21
> **a.malcolm.stanley@gmail said:**
> Installing the backports packages did not work for me. 
Wireless still fails while attempting to negotiate DHCP.

It would be great if you can post the 'lsmod' output, as well as the 'lspci' output to see your modules & devices.

Also, do a 'ifconfig -a' to see if your device is being loaded by the kernel.

*NOTE: 'lsmod', 'lspci' & 'ifconfig -a' are commands that you have to throw into the terminal. Just in case you didn't know.

Good luck,
X-TBT a.k.a. The Mentor.

---

### Post by a.malcolm.stanley@gmail on 2009-11-21
Post 10 of this thread has a syslog fragment showing my wireless connection failing in dhcp address acquisition. But since you ask:

> **xtbt said:**
> It would be great if you can post the 'lsmod' output

Module                  Size  Used by
aes_i586                8124  0 
aes_generic            27484  1 aes_i586
lib80211_crypt_ccmp     5340  0 
arc4                    1660  0 
ecb                     2524  0 
lib80211_crypt_wep      3708  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipw2200               139400  0 
sdhci_pci               7100  0 
iptable_filter          3100  0 
dell_wmi                2564  0 
snd_timer              22276  2 snd_pcm,snd_seq
libipw                 42720  1 ipw2200
sdhci                  17472  1 sdhci_pci
joydev                 10272  0 
ip_tables              11692  1 iptable_filter
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop             8128  0 
cfg80211              130440  2 ipw2200,libipw
yenta_socket           24200  1 
x_tables               16544  1 ip_tables
dcdbas                  7292  1 dell_laptop
lib80211                6528  4 lib80211_crypt_ccmp,lib80211_crypt_wep,ipw2200,libipw
led_class               4096  1 sdhci
rsrc_nonstatic         11644  1 yenta_socket
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
soundcore               7264  1 snd
serio_raw               5280  0 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
b44                    28620  0 
ssb                    44868  1 b44
pcmcia                 36808  1 ssb
pcmcia_core            35792  4 yenta_socket,rsrc_nonstatic,ssb,pcmcia
mii                     5212  1 b44
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


> **xtbt said:**
> , as well as the 'lspci' output to see your modules & devices.

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


> **xtbt said:**
> Also, do a 'ifconfig -a' to see if your device is being loaded by the kernel.

eth0      Link encap:Ethernet  HWaddr 00:11:43:72:f8:18  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1100448 (1.1 MB)  TX bytes:169965 (169.9 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:00:b6:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:12 dropped:12 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5015 (5.0 KB)  TX bytes:3396 (3.3 KB)
          Interrupt:17 Base address:0xe000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


> **xtbt said:**
> *NOTE: 'lsmod', 'lspci' & 'ifconfig -a' are commands that you have to throw into the terminal. Just in case you didn't know..

uh, yeah, I kinda did know that...

cheers...

---

### Post by xtbt on 2009-11-22
a.malcolm.stanley@gmail:

   Ok, as I can see, your wireless adapter is being detected successfully by the kernel but there's something that bothers me. By default, a wireless adapter is activated by the name of WLAN0 or something that has to be with WLAN ... maybe WIFI0 or something similar.

   The thing my friend, is that your wireless adapter is being configured like if it was an ethernet adapter. I don't really know why, maybe it's being specified by some config file like '/etc/network/interfaces'.

   Also, do you already have your network-manager configured to know which your wifi adapter is ?

   I've never seen a wireless connection named eth1, that's what I don't understand in your configuration. Maybe it has nothing to do with your problem, but you better check that.

Good luck,
X-TBT a.k.a. The Mentor.

---

### Post by a.malcolm.stanley@gmail on 2009-11-22
> **xtbt said:**
> a.malcolm.stanley@gmail:

   The thing my friend, is that your wireless adapter is being configured like if it was an ethernet adapter. I don't really know why, maybe it's being specified by some config file like '/etc/network/interfaces'.

   Also, do you already have your network-manager configured to know which your wifi adapter is ?

   I've never seen a wireless connection named eth1, that's what I don't understand in your configuration. Maybe it has nothing to do with your problem, but you better check that.


useful.

here is the output for the interface when I run iwconfig:

```
eth1      IEEE 802.11bg  Mode:Managed  Frequency:2.437 GHz  
          Access Point: Not-Associated   Bit Rate:0 kb/s   Tx-Power=20 dBm   
          Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```looks right to me, but what do I know?

Interestingly, in /etc/network/interfaces only loopback is specified.
so that looks wrong, and doesn't really indicate where the  w/l interface is being set up. I've put a rudimentary setup in place, we'll see if it makes a difference.

Thanks, that was helpful.

**UPDATE:**

So a couple of things

a) adding eth1 to the /etc/network/interfaces disabled wireless: network manager said it was now unmanaged. deleting the lines re-enabled it.
b) I found this quote: 
>  If after rebooting the wireless adapter stops working, then restarting the wireless interface may fix it. Do ifconfig to check the interface name (likely either eth1 or eth2 - the laptop's wired Ethernet socket is likely to be eth0) at [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200) which sort of indicates to me that eth1 as a wireless network interface identifier is ok. 

so now I'm not sure I really need to look into that further, and think there needs to be a renewed focus on the dhcp failure.
Which I will look into again tomorrow, after I sleep on it some more.

---

### Post by xtbt on 2009-11-22
That's a new thing to me. From my experience, 'eth' stands for 'ethernet' but well, we learn new things everyday.
 
Also, which Manager do you use ? I don't know about 'Network-Manager' (the default on Ubuntu), but in Wicd you can manually specify the wireless adapter identifier (which by default is wlan0). Maybe that's the problem, you network manager thinks that your wireless adapter is wlan0 but it fails to assign an IP address because it doesn't find any 'wlan0' adapter.
 
Well, just my thought.
X-TBT a.k.a. The Mentor.

---

