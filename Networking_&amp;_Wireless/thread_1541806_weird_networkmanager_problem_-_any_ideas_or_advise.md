---
title: "weird networkmanager problem - any ideas or advise?"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by marc.verwerft on 2010-07-29
Hello,

I have a strange problem with Networkmanager and don't  know how to further debug it. Any advise is welcome. I use Ubuntu 10.04 on a thinkpad T400, iwlagn driver with 'Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection'.

Problem description:
-  in the list of networks that drops down from the NMapplet (after a left  mouse click) I see often that the system found networks with gibberish  names (see attached appetizer and full screenshots). These names look  like taken from uninitialized memory.
- this only happens at this particular client where I work (monday to thursday). Anywhere else I don't have problems with my wifi.
- when these names appear I can't connect to any wireless network (looks like the networkmanager is 'confused')
- I can fix this issue by either doing:
[INDENT]   - a cold start. Sometimes the issue is fixed sometimes I have the same problem.
[/INDENT][INDENT]   - disabling wireless and enabling it again. This also only works sometimes but typically with more luck then the reboot.
[/INDENT]-  I've also noticed that when the icon of the network manager changes to a  circle (to indicate that it is connecting) it is usually showing two  half circles turning around (see screenshot 4-5). Don't know if this  related to my problem ...

This looks to me as an initialization  issue but I don't know what the trigger is. Maybe the wireless radio  signals 'found a network' when it's not really the case? Possibly the  problem lies deeper in the wireless driver because once I'm connected,  those names don't show up anymore. Race condition   somewhere?

In attachment there are some screenschots and the  output of syslog and daemon.log from the time the system booted till I  got a working connection (approx 10 mins worth of logging). The  screenshots show the dropdown list of network names and on the left top  side the output in a terminal of syslog, at the bottom the output of  daemon.log. At Jul 29 09:00:01 I clicked on the 'Enable wireless'  checkbox to disable and approx 30 secs later i did the same to enable  it. I could then connect to the correct network with Networkmanager.

Log  files attached are syslog, daemon.log, uname, lspci and 6 screenshots.  I've also included an appetizer that only shows the drop down list with  gibberish names.

Hope somebody will guide in what to do next ...

Regards,

Marc Verwert

---

### Post by mprokolo on 2010-07-29
just a thought: right click Network Manager select edit connections go into wireless tab see if there is any gibberish in there and remove it

From your logs i see that 

Jul 29 08:52:25 marc-laptop wpa_supplicant[994]: Association request to the driver failed

Jul 29 08:57:01 marc-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed


and after that every time you associate you get kicked 

Jul 29 08:57:01 marc-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 29 08:57:06 marc-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Jul 29 08:57:06 marc-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected

Also these bugs look very similar

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/543816](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/543816)

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/568244](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/568244)

Looks like the network you are trying to connect to uses wpa and there is a problem with wpa_supplicant in your computer 
probably is a good idea to give some info about the router also and if you can connect successfully to other routers with wpa security

---

### Post by marc.verwerft on 2010-07-30
> just a thought: right click Network Manager select edit connections go  into wireless tab see if there is any gibberish in there and remove it


No gibberish in there.

> Looks like the network you are trying to connect to uses wpa and there is a problem with wpa_supplicant in your computer 
probably is a good idea to give some info about the router also and if  you can connect successfully to other routers with wpa security 	

Indeed, I use WPA for this sometimes failing connection. Other networks with WPA are OK.

Next monday, I'll try to post another logfile (this time with wpa_supplicant traced in detail with -dddt) and more details about the router.

Regards,

Marc

---

### Post by mprokolo on 2010-07-30
hmm i saw that your card model doesn't play nice when trying to connect to N routers ([https://bugs.launchpad.net/ubuntu/+bug/575492](https://bugs.launchpad.net/ubuntu/+bug/575492))

I'm thinking that if it had problem with wpa then you wouldn't connect to any wpa network. If it works ok everywhere else you should probably try to find whats the difference in this setup because the logs can be missleading

other thoughts is that the router uses wpa2-enterprise or something else than the wpa-personal that is "normally" used

if you have a spare router at home try to replicate the problem by changing the security settings of the router

---

### Post by marc.verwerft on 2010-08-02
This morning - to my surprise - I found no gibberish names in NM.
 
 I had changed 2 things since last thursday:
 - the 'connect automatically' checkbox on the connection properties was unmarked (where it was previously marked)
 - I uninstalled WICD (that I previously installed to figure out whether  the problem was only happening in NM - the gibberish was also shown in  WICD)
 
 I'll retry later on with the checkbox marked again.
 
The router is a linksys G-router: [http://www.linksysbycisco.com/UK/en/support/WRT54G3GV2-VF](http://www.linksysbycisco.com/UK/en/support/WRT54G3GV2-VF)
 We can thus exclude the problem with N-routers.

Regards,
 
 Marc

---

### Post by mprokolo on 2010-08-04
Seems like a driver issue but it is strange that it works everywhere else.
next time could you post a "iwlist scan" and a "iwconfig" maybe there something in there.

PS. If it now works don't fix it!

---

### Post by marc.verwerft on 2010-08-05
Thanks for the advice.

I've been using that network connection for a couple of days now with automatic logon switched off. And I don't see these weird names anymore. I don't think it's a coincidence.

I had already seen strange ESSID's in the output of iwlist but didn't really know what to think of it.
A quick glance on iwlist:
$ sudo iwlist wlan0 scan | grep -i ssid
                    ESSID:"ValueManagementB"
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
I've attached full logs for iwlist and iwconfig.

Regards,

Marc

---

### Post by mprokolo on 2010-08-06
At first i thought that the 
ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00" 
was probably a hidden network which your card did not recognize well and failed when tried to connect to. 
but one of the \x00 essid's comes from your own network (if you see the mac Address: 00:23:69:57:33:20)

it seems that you received 2 beacons 
your normal one "Extra: Last beacon: 48ms ago"
but from the same router you received a \x00 one also "Extra: Last beacon: 148ms ago"

so, with auto connect your card tries to connect to the first network it finds but it finds two with the same mac and that probably causes some problems

if you want to inspect the problem more get another linux laptop and see if it gets 2 beacons from your router but it works now so there is no need for a fix

---

### Post by marc.verwerft on 2010-08-10
Hello - sorry it took so long to come back. I first want to thank you for the hints and the analysis. From your message I can derive that you know a lot more about wifi then I do ;-)

However: are you sure that iwlist shows the MAC address of my card?
As far as I can tell, it displays the MAC address of the router I'm connected to and ifconfig shows the MAC address of the card.

The output of both commands:
```
marc@marc-laptop:~/wifi-prob$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"swisscom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:A0:F8:A8:A9:35   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

marc@marc-laptop:~/wifi-prob$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:21:6b:3b:e5:70  
          inet addr:192.168.49.214  Bcast:192.168.51.255  Mask:255.255.252.0
          inet6 addr: fe80::221:6bff:fe3b:e570/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34077743 (34.0 MB)  TX bytes:6233460 (6.2 MB)

```

In that case we're back where we started. If I use auto connect, things go wrong. If I'm on manual it works as expected. Should I take this to the NM forum?

Regards,

Marc

---

### Post by mprokolo on 2010-08-11
No i meant the mac address of the router not the card
iwlist scan shows the wifi's in range 
from your iwlist logs (I cut some parts to be more readable):
```

          Cell 01 - Address: 00:23:69:57:33:20
                    ESSID:"ValueManagementB"
                    Extra: Last beacon: 48ms ago
          Cell 02 - Address: 00:23:69:57:33:20
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Extra: Last beacon: 148ms ago

```

As you can see from the same router you receive 2 different (only on Essid) beacons

I hope its more clear now what i tried to tell you.

Also you said that wicd too had the same problem so I doubt it if it is a "pure" NM problem but you can always try there maybe there someone who knows better

Finally if you have a second laptop use a livecd and do another iwlist scan to see if it gets the same results (2 beacons from the same router) in that case it is the router that confuses your card and probably will confuse the 2nd laptops card as well

---

