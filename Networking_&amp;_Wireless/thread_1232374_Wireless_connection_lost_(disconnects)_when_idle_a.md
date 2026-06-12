---
title: "Wireless connection lost (disconnects) when idle after locking screen"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by pveurshout on 2009-08-05
A little over a week ago I installed Jaunty on my new laptop, but every now and then my wireless network disconnects (and doesn't auto-reconnect) some time (45-60 mins) after I **lock the screen** (or automatically locks when the screensaver kicks in after 10 mins of idle time) and walk away from my computer. It doesn't happen all the time (seems to be totally random whenever it happens..I can't think of anything 'special' I might be doing at such a time) and I have _never experienced anything like this when I was actively using the computer_. I'd like to add that every time it did happen there was network activity although I was away (torrenting using Vuze and IM with KMess - I received messages between the moments I locked the screen and the network connection shut down) and I'm using power management to turn off the screen after 20 minutes (I tried to reproduce the problem a couple times with various screensaver-/idle-/powermanagement-settings, but "unfortunately" it all still worked fine after > 70 minutes of idle time at that time). The wireless card is an Intel WiFi Link 5300 and according to iwconfig power management is turned off.

I've spent quite some time searching the forums and googling and although I stumbled upon many problems, bugs and solutions regarding wireless networking in Ubuntu, everything I found is missing one or more essential characteristics of my problem (no problems when not idle, problems not related with screensaver/lock screen, etc.).

Does anyone know what might cause this (seemingly) random behavior of wireless disconnecting? Or does anyone know of a way to find out? Does Ubuntu log anything regarding the wireless card activity? Any help, comments, similar problems, known bugs, or just random information regarding wireless networks & Ubuntu, anything that might help, is very much appreciated! :)

---

### Post by pveurshout on 2009-08-06
The problem just reappeared again, this time within 10 minutes after locking the session. It worked fine the whole afternoon (6 hours straight) including several occasions of locked sessions (both manual and automatic), but now it just stopped. I had to disable networking (right-click on the network manager icon in the task bar) and enable it again, so no restart or something required to make it work again.

Could someone who understands anything of dmesg output please take a look at the code below? Although it's quite a lot of text, most of the lines say exactly the same.

```
[22876.398924] iwlagn: Read index for DMA queue txq_id (2) index 141 is out of range [0-256] 172 159
[22876.398935] iwlagn: Read index for DMA queue txq_id (2) index 140 is out of range [0-256] 172 159
[22876.398942] iwlagn: Read index for DMA queue txq_id (2) index 139 is out of range [0-256] 172 159
[22881.076276] wlan0: No ProbeResp from current AP 00:0c:f6:1e:16:5e - assume out of range
[22881.676281] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22882.176282] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22882.176292] iwlagn: Error setting new RXON (-110)
[22882.176306] wlan0: direct probe to AP 00:0c:f6:1e:16:5e try 1
[22882.376041] wlan0: direct probe to AP 00:0c:f6:1e:16:5e try 2
[22882.576292] wlan0: direct probe to AP 00:0c:f6:1e:16:5e try 3
[22882.776276] wlan0: direct probe to AP 00:0c:f6:1e:16:5e timed out
[22889.492274] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22889.992126] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22889.992135] iwlagn: Error setting new RXON (-110)
[22894.993807] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22895.492281] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22895.492290] iwlagn: Error setting new RXON (-110)
[22896.492278] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22896.492288] iwlagn: Error setting new RXON (-110)
[22896.992296] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22897.492273] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22897.492282] iwlagn: Error setting new RXON (-110)
[22897.992319] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22898.492276] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22898.492286] iwlagn: Error setting new RXON (-110)
[22900.492279] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22900.996280] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22900.996289] iwlagn: Error setting new RXON (-110)
[22905.992276] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22906.492074] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22906.492083] iwlagn: Error setting new RXON (-110)
[22911.492284] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22911.492323] iwlagn: No space for Tx
[22911.492328] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22911.492333] iwlagn: Error setting new RXON (-28)
[22911.492342] iwlagn: No space for Tx
[22911.492346] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[22916.493493] iwlagn: No space for Tx
[22916.493505] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[22916.493528] iwlagn: No space for Tx
[22916.493532] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22916.493536] iwlagn: Error setting new RXON (-28)
[22916.493543] iwlagn: No space for Tx
[22916.493547] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[22921.494270] iwlagn: No space for Tx
[22921.494283] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[22921.494307] iwlagn: No space for Tx
[22921.494312] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22921.494316] iwlagn: Error setting new RXON (-28)
[22921.494323] iwlagn: No space for Tx
[22921.494327] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[22926.495533] iwlagn: No space for Tx
[22926.495546] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[22926.495569] iwlagn: No space for Tx
[22926.495573] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22926.495578] iwlagn: Error setting new RXON (-28)
[22926.495584] iwlagn: No space for Tx
[22926.495588] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[22931.496787] iwlagn: No space for Tx
[22931.496799] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[22931.496822] iwlagn: No space for Tx
[22931.496827] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22931.496831] iwlagn: Error setting new RXON (-28)
[22931.496838] iwlagn: No space for Tx
[22931.496842] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[22936.396020] iwlagn: No space for Tx
[22936.396032] iwlagn: Error sending REPLY_STATISTICS_CMD: enqueue_hcmd failed: -28
[22936.498043] iwlagn: No space for Tx
[22936.498055] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[22936.498079] iwlagn: No space for Tx
[22936.498083] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22936.498087] iwlagn: Error setting new RXON (-28)
[22936.498094] iwlagn: No space for Tx
[22936.498098] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[22941.499284] iwlagn: No space for Tx
[22941.499296] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[22941.499319] iwlagn: No space for Tx
[22941.499323] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22941.499327] iwlagn: Error setting new RXON (-28)
[22941.499334] iwlagn: No space for Tx
[22941.499338] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[22946.500520] iwlagn: No space for Tx
[22946.500532] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[22946.500554] iwlagn: No space for Tx
[22946.500558] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22946.500562] iwlagn: Error setting new RXON (-28)
[22946.500569] iwlagn: No space for Tx
[22946.500573] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[22951.501763] iwlagn: No space for Tx
[22951.501775] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[22951.501798] iwlagn: No space for Tx
[22951.501802] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22951.501806] iwlagn: Error setting new RXON (-28)
[22951.501813] iwlagn: No space for Tx
[22951.501817] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[22956.503170] iwlagn: No space for Tx
[22956.503181] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[22956.503202] iwlagn: No space for Tx
[22956.503206] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[22956.503211] iwlagn: Error setting new RXON (-28)
[22956.503218] iwlagn: No space for Tx
[22956.503222] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[23008.996573] iwlagn: No space for Tx
[23008.996583] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[23008.996603] iwlagn: No space for Tx
[23008.996607] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[23008.996612] iwlagn: Error setting new RXON (-28)
[23008.996619] iwlagn: No space for Tx
[23008.996623] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
```

---

### Post by pveurshout on 2009-08-08
Is there anyone who could help me interpret the dmesg output I get when the error occurs?

It just happened again. However, the network manager said it was still connected with the wireless network (92% signal strength) but I could not browse, IM, etc. This time dmesg gave a somewhat different output than the last time:

(the lines starting from timestamp 8366 are after I reconnected)

```

[ 7624.807190] iwlagn: Read index for DMA queue txq_id (2) index 63 is out of range [0-256] 75 72
[ 7624.807204] iwlagn: Read index for DMA queue txq_id (2) index 61 is out of range [0-256] 75 72
[ 7625.574262] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[ 7625.591816] iwlagn: Can't stop Rx DMA.
[ 7625.632327] Registered led device: iwl-phy0:radio
[ 7625.632365] Registered led device: iwl-phy0:assoc
[ 7625.632400] Registered led device: iwl-phy0:RX
[ 7625.632433] Registered led device: iwl-phy0:TX
[ 8366.100042] mac80211-phy0: failed to remove key (0, 00:0c:f6:1e:16:5e) from hardware (-22)
[ 8366.101180] wlan0: direct probe to AP 00:0c:f6:1e:16:5e try 1
[ 8366.101373] wlan0: disassociating by local choice (reason=3)
[ 8366.103613] wlan0 direct probe responded
[ 8366.103620] wlan0: authenticate with AP 00:0c:f6:1e:16:5e
[ 8366.105493] wlan0: authenticated
[ 8366.105500] wlan0: associate with AP 00:0c:f6:1e:16:5e
[ 8366.109118] wlan0: RX AssocResp from 00:0c:f6:1e:16:5e (capab=0x411 status=0 aid=6)
[ 8366.109124] wlan0: associated
[ 8366.211237] phy0: failed to restore operational channel after scan
[ 8366.224542] wlan0: authenticate with AP 00:0c:f6:1e:16:5e
[ 8366.424330] wlan0: authenticate with AP 00:0c:f6:1e:16:5e
[ 8366.528803] wlan0: authenticated
[ 8366.528814] wlan0: associate with AP 00:0c:f6:1e:16:5e
[ 8366.533005] wlan0: RX ReassocResp from 00:0c:f6:1e:16:5e (capab=0x411 status=0 aid=6)
[ 8366.533013] wlan0: associated


```

---

### Post by Sevmpe on 2009-08-10
Your problem looks similar to this thread: [http://ubuntuforums.org/showthread.php?t=1138177](http://ubuntuforums.org/showthread.php?t=1138177)

Have a look. There might be a hint there that could help you.

---

### Post by pveurshout on 2009-08-10
> **Sevmpe said:**
> Your problem looks similar to this thread: [http://ubuntuforums.org/showthread.php?t=1138177](http://ubuntuforums.org/showthread.php?t=1138177)

Have a look. There might be a hint there that could help you.

Thanks for the suggestion. Someone mentioned there might be a problem with Jaunty and WPA secured connections, which could cause my problem: when I logged back into my (running) session about an hour ago, my connection was once again lost and I noticed there was a network manager box which asked me to type my WPA key (it was pre-typed, by the way, so it hadn't lost it or something) and hit Connect (which didn't work by the way; I had to manually uncheck&check 'Enable Wireless' and 'Enable Networking' by right-clicking the NM tray icon.) The dmesg output was the same was last time (see my post above). Next time it happens I'll try to ping the router and see what happens. Nevertheless, I'm still wondering why this **only** occurs when I lock the session and leave the computer idle for a while (although there is constant network activity) whereas I have no problems at all while I keep using it or leave it idling without locking the session.

By the way, I still don't understand what dmesg is actually telling me..could someone interpret the dmesg error messages for me, or at least give an idea what it's about, because I have absolutely no clue as to what information I *should* be getting out of this.. Thanks so much!

```

[22876.398942] iwlagn: Read index for DMA queue txq_id (2) index 139 is out of range [0-256] 172 159
[22881.076276] wlan0: No ProbeResp from current AP 00:0c:f6:1e:16:5e - assume out of range
[22881.676281] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22882.176282] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22882.176292] iwlagn: Error setting new RXON (-110)
[22882.176306] wlan0: direct probe to AP 00:0c:f6:1e:16:5e try 1
(...)
[22882.776276] wlan0: direct probe to AP 00:0c:f6:1e:16:5e timed out
[22889.492274] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[22889.992126] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[22889.992135] iwlagn: Error setting new RXON (-110)

```

---

### Post by pveurshout on 2009-08-24
Although it unfortunately seems like no one has encountered this problem before, I just thought I'd let you guys know something I suspected but didn't know for sure.

The wireless connection seems to drop only when I'm actually using it. If I just let my IM clients sit online I can stay away for hours at a time without ever losing the connection, but if I'm downloading/uploading stuff (both to the internet and to other computers on my home network) it just dies after a while when I lock the session. Below is the (only!) dmesg line I got after I just got disconnected again, while sending a 4,4 GB file to another computer in my home network. I don't know whether it's just a coincidence, but (as can be seen in previous posts in this thread) I always got a hell of a lot more lines when I got disconnected while downloading/uploading to the internet..

```
[ 6932.158879] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
```

---

### Post by Randomperson_1000 on 2009-08-26
Sorry for the delay

i had a similar problem my connection would drop only when i wasnt hitting high upload/download speeds.

I cant rememebr what i exactly did but u might want to google how to turn power saving of in ubuntu. Second try setting up a a static address. This normally stops all the weird wi-fi disconnects. Demsg comes out with dissacoiated local choice reason=3 i use to have this alot and i beleive its related to interference. run "iwlist [interface] scan" (when disconnected from wi-fi too see what channels other routers in teh area are using they normally use 6 or 11 try switching channels my disconnect problems decreased around 80% after switching channels.  

Can you post ur output of ifconfig? im curious but what is your wireless card wlan0 or iwlagn? also can u give more detailed info on what card u are using and perhaps a link

edit: [https://bugs.launchpad.net/ubuntu/+bug/411869](https://bugs.launchpad.net/ubuntu/+bug/411869) seems som1 has a similar problem

---

### Post by pveurshout on 2009-08-28
Hey, don't worry about the delay, I really appreciate your time to get back to me :)

I'm using a static IP-address at the moment (actually never used dynamic with this machine yet). According to iwconfig, power management is turned off:
```

wlan0     IEEE 802.11abgn  ESSID:"Sitecom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:F6:1E:16:5E   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-52 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

There are usually about 3 other wireless networks in the area. How can I see what channel they're using? I'll then try doing this as well when the problem occurs again (I've deliberately been shutting down Vuze over the past few weeks when I left my computer, to make sure it works fine when there's no network activity (or hardly any; I always left two IM clients on), and everything did work perfectly) (except for the time I sent a movie over the home network and the connection, not surprisingly, died). I'm on channel 11, according to 'iwlist wlan0 scan':

```

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:F6:1E:16:5E
                    ESSID:"Sitecom"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level:-40 dBm  Noise level=-93 dBm
                    Encryption key:on
                    IE: Unknown: 000753697465636F6D
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD07000C4301000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000273408dca5d
                    Extra: Last beacon: 32ms ago


```

This is the ifconfig output:
```

eth0      Link encap:Ethernet  HWaddr 00:25:b3:bf:98:75  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:db300000-db320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5686 (5.6 KB)  TX bytes:5686 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:5b:c7:12  
          inet addr:192.168.0.98  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe5b:c712/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:209048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23490999 (23.4 MB)  TX bytes:356154060 (356.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-6A-5B-C7-12-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I'm using an Intel WiFi Link 5300 card (manufacturer's info [here]("http://www.intel.com/network/connectivity/products/wireless/adapters/5000/") and [here (pdf)]("http://download.intel.com/network/connectivity/products/wireless/319982.pdf")) on an HP 8530w laptop. (I was the one who reported the bug you mentioned, by the way)

edit: Should the iwlist wlan0 scan command have listed *all* networks in range, instead of just the one I'm connected to? The Gnome network manager sees 3 (including my own) (it actually lists 4, but 2 of them have the same name although a slightly different connection strength)

---

### Post by Randomperson_1000 on 2009-08-29
i seriously cant remember what i did to alleviate myslef from this problem so bare with me while i try to remember teh chain of thoughts that went through my head. When you run "iwlist scan" make sure u are disconnected to get info from all channels otherwise if u are connected to a network the card locks onto that channel. I currently am using channel 7 no one else uses it and i hardly get disconnected.

Okay i have noticed that ur noise level=-92 and signal level = -52 i think this may be the problem. From some googling the negative number show that theres interference. Try changing channels 6 and 11 are most commonly used so try something different. 

Perhaps it is a router setting? try turning on fragmentation threshold if ur router supports this feature. Soem more info on this [http://forums.techguy.org/networking/694582-solved-mtu-vs-fragmentation-threshold.html](http://forums.techguy.org/networking/694582-solved-mtu-vs-fragmentation-threshold.html) 

Im pretty sure ur issue will be solved after reducing interference i think this was how i solved the problem. If this doesn't help do u have any othe computers on ur wlan and do they too experience disconnects/lock-ups? I will hook up my other card when i have time to test if the cards may be the problem.

---

### Post by pveurshout on 2009-08-30
From iwlist wlan0 scan it seems that all the other wireless networks in the area are on a different channel. Can interference still be caused by them while they're using a different channel?

I used my previous laptop (Hardy) for over a year without any problems, so I doubt there's anything wrong with the router or its settings. The strangest thing still is, though, that I have used this machine for over a month now and I never experienced any wireless problems while I was using it. Only when I lock the session the connection seems to drop after a while - sometimes after 10 minutes, sometimes after an hour, sometimes not at all :-?

Actually, I just remembered I decided to install Jaunty on my old laptop as well, after I moved all my the data. I'll play around with it and see if I can reproduce the problem there, which would indicate a problem with Jaunty (or the network - but as it worked fine under Hardy, I doubt that).

---

### Post by Randomperson_1000 on 2009-09-06
phones can also cause interference(never found a phone that does though) and other radio devices. Try switching channels it could be the solution.

Its sort of ironic that as i help you with ur wireless my own has been playing up with different symptoms now. Try: 

sudo apt-get install linux-backports-modules-jaunty

that should install some updated drivers and hopefully it will work.

ive got a theory on idea if it will work. Ur wireless doesn't drop with windows does it? it only drops when ubuntu makes alot of connections, window has a limit. I think you might want to limit the number of half open tcp connections in your bt client.it could be your router just cant handle it (mines cant).

---

### Post by pveurshout on 2009-09-16
Hey, sorry for my delayed reply. Thanks for getting back to me. Actually I just lost my connection again, this time without locking my session (dmesg below, though I don't think there's anything new in it). Good to know it's unrelated, I guess. I was downloading a 4 GB file with Firefox, but had a bittorrent client running (not sure if it was doing anything). I decreased the maximum number of connections from 200 to 100 and the half-open connections from 50 to 20 (or should these be even lower to make any difference?) and will first wait and see if it improves. If not, I'll try the backports (not that I don't want to use that right away, by the way, but I'd like to know what causes the problem instead of applying two solutions and not knowing which one fixed it :)).

UPDATE: interestingly enough, when I restarted my Firefox download, I lost my connection again within just a couple of minutes. Exact same problem as always. I'm currently downloading it for the third time, this time without my bittorrent client running in the background. Does Firefox make more than 1 connection, like a bittorrent client, when using it to download a file? If not, it should work this way. If it doesn't, I'll install the backports modules and see if the problem persists.

```

[ 4585.064184] iwlagn: Read index for DMA queue txq_id (2) index 97 is out of range [0-256] 110 103
[ 4585.064194] iwlagn: Read index for DMA queue txq_id (2) index 98 is out of range [0-256] 110 103
[ 4589.736573] wlan0: No ProbeResp from current AP 00:0c:f6:1e:16:5e - assume out of range
[ 4590.336567] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 4590.837402] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 4590.837412] iwlagn: Error setting new RXON (-110)
[ 4590.837425] wlan0: direct probe to AP 00:0c:f6:1e:16:5e try 1
[ 4591.037063] wlan0: direct probe to AP 00:0c:f6:1e:16:5e try 2
[ 4591.236571] wlan0: direct probe to AP 00:0c:f6:1e:16:5e try 3
[ 4591.438959] wlan0: direct probe to AP 00:0c:f6:1e:16:5e timed out
[ 4600.844781] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 4601.344085] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 4601.344094] iwlagn: Error setting new RXON (-110)
[ 4605.164282] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 4605.164291] iwlagn: Error setting new RXON (-110)
[ 4605.667152] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 4606.165082] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 4606.165086] iwlagn: Error setting new RXON (-110)
[ 4606.664271] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 4607.164279] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 4607.164288] iwlagn: Error setting new RXON (-110)
[ 4612.164079] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 4612.664308] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 4612.664317] iwlagn: Error setting new RXON (-110)
[ 4617.664280] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 4618.164270] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 4618.164279] iwlagn: Error setting new RXON (-110)
[ 4623.164269] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 4623.664073] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 4623.664082] iwlagn: Error setting new RXON (-110)
[ 4628.664277] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 4629.164276] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 4629.164285] iwlagn: Error setting new RXON (-110)
[ 4629.164302] iwlagn: No space for Tx
[ 4629.164306] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4633.665802] iwlagn: No space for Tx
[ 4633.665814] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4633.665836] iwlagn: No space for Tx
[ 4633.665840] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4633.665844] iwlagn: Error setting new RXON (-28)
[ 4633.665851] iwlagn: No space for Tx
[ 4633.665855] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4638.667435] iwlagn: No space for Tx
[ 4638.667447] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4638.667470] iwlagn: No space for Tx
[ 4638.667474] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4638.667478] iwlagn: Error setting new RXON (-28)
[ 4638.667485] iwlagn: No space for Tx
[ 4638.667489] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4643.669436] iwlagn: No space for Tx
[ 4643.669448] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4643.669472] iwlagn: No space for Tx
[ 4643.669477] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4643.669481] iwlagn: Error setting new RXON (-28)
[ 4643.669488] iwlagn: No space for Tx
[ 4643.669491] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4645.036548] iwlagn: No space for Tx
[ 4645.036560] iwlagn: Error sending REPLY_STATISTICS_CMD: enqueue_hcmd failed: -28
[ 4648.671486] iwlagn: No space for Tx
[ 4648.671498] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4648.671519] iwlagn: No space for Tx
[ 4648.671523] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4648.671527] iwlagn: Error setting new RXON (-28)
[ 4648.671534] iwlagn: No space for Tx
[ 4648.671537] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4653.672198] iwlagn: No space for Tx
[ 4653.672209] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4653.672230] iwlagn: No space for Tx
[ 4653.672234] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4653.672238] iwlagn: Error setting new RXON (-28)
[ 4653.672245] iwlagn: No space for Tx
[ 4653.672249] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4658.674066] iwlagn: No space for Tx
[ 4658.674078] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4658.674101] iwlagn: No space for Tx
[ 4658.674106] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4658.674110] iwlagn: Error setting new RXON (-28)
[ 4658.674117] iwlagn: No space for Tx
[ 4658.674121] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4663.676136] iwlagn: No space for Tx
[ 4663.676146] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4663.676167] iwlagn: No space for Tx
[ 4663.676171] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4663.676175] iwlagn: Error setting new RXON (-28)
[ 4663.676182] iwlagn: No space for Tx
[ 4663.676186] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4675.655306] iwlagn: No space for Tx
[ 4675.655317] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4675.655339] iwlagn: No space for Tx
[ 4675.655343] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4675.655347] iwlagn: Error setting new RXON (-28)
[ 4675.655354] iwlagn: No space for Tx
[ 4675.655358] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4795.656160] iwlagn: No space for Tx
[ 4795.656172] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4795.656195] iwlagn: No space for Tx
[ 4795.656199] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4795.656203] iwlagn: Error setting new RXON (-28)
[ 4795.656210] iwlagn: No space for Tx
[ 4795.656214] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 4915.655755] iwlagn: No space for Tx
[ 4915.655767] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 4915.655789] iwlagn: No space for Tx
[ 4915.655794] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 4915.655798] iwlagn: Error setting new RXON (-28)
[ 4915.655805] iwlagn: No space for Tx
[ 4915.655809] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 5035.655125] iwlagn: No space for Tx
[ 5035.655138] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5035.655160] iwlagn: No space for Tx
[ 5035.655165] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5035.655169] iwlagn: Error setting new RXON (-28)
[ 5035.655176] iwlagn: No space for Tx
[ 5035.655180] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 5155.655431] iwlagn: No space for Tx
[ 5155.655443] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5155.655464] iwlagn: No space for Tx
[ 5155.655468] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5155.655473] iwlagn: Error setting new RXON (-28)
[ 5155.655480] iwlagn: No space for Tx
[ 5155.655483] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 5275.655602] iwlagn: No space for Tx
[ 5275.655615] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5275.655639] iwlagn: No space for Tx
[ 5275.655643] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5275.655647] iwlagn: Error setting new RXON (-28)
[ 5275.655654] iwlagn: No space for Tx
[ 5275.655658] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 5339.421919] iwlagn: No space for Tx
[ 5339.421930] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5339.421949] iwlagn: No space for Tx
[ 5339.421954] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5339.421958] iwlagn: Error setting new RXON (-28)
[ 5339.421965] iwlagn: No space for Tx
[ 5339.421969] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 5344.423411] iwlagn: No space for Tx
[ 5344.423423] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5344.423446] iwlagn: No space for Tx
[ 5344.423450] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5344.423454] iwlagn: Error setting new RXON (-28)
[ 5344.423461] iwlagn: No space for Tx
[ 5344.423465] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 5349.424931] iwlagn: No space for Tx
[ 5349.424943] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5349.424967] iwlagn: No space for Tx
[ 5349.424971] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5349.424976] iwlagn: Error setting new RXON (-28)
[ 5349.424983] iwlagn: No space for Tx
[ 5349.424987] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 5354.426436] iwlagn: No space for Tx
[ 5354.426448] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5354.426471] iwlagn: No space for Tx
[ 5354.426475] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5354.426479] iwlagn: Error setting new RXON (-28)
[ 5354.426486] iwlagn: No space for Tx
[ 5354.426490] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 5359.427934] iwlagn: No space for Tx
[ 5359.427945] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[ 5359.427969] iwlagn: No space for Tx
[ 5359.427973] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 5359.427977] iwlagn: Error setting new RXON (-28)
[ 5359.427983] iwlagn: No space for Tx
[ 5359.427987] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28

```

---

### Post by pveurshout on 2009-09-27
> **Randomperson_1000 said:**
> ive got a theory on idea if it will work. Ur wireless doesn't drop with windows does it? it only drops when ubuntu makes alot of connections, window has a limit. I think you might want to limit the number of half open tcp connections in your bt client.it could be your router just cant handle it (mines cant).

Unfortunately this wasn't the problem. The connection just dropped again although I significantly decreased the number of connections (also, my previous laptop using Hardy never had any problems with the network even though I used it intensively for bittorrenting as well).

I installed the linux-backports-modules-jaunty as you suggested and will report back either when it works for a couple of days (while intensively using the connection) or as soon as it breaks (hopefully not).

---

### Post by pveurshout on 2009-09-28
Hey, after installing the backports modules my dmesg keeps flooding with these messages:
```
[   75.919076] wlan0: beacon loss from AP ffff88013fd70ac0 - sending probe request
[  115.877120] wlan0: beacon loss from AP ffff88013fd70ac0 - sending probe request
```

It works fine (though it's too early to say whether the original problem has been solved by this) but I can only assume something else is wrong now. Any idea why these messages keep popping up?

---

### Post by pveurshout on 2009-10-01
Unfortunately, I just lost my connection again.. installing linux-backports-modules-jaunty didn't help either :(

```
[ 5880.996571] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
<repeated many times>
```

EDIT: found [this]("https://bugzilla.redhat.com/show_bug.cgi?id=493018"), which says it's fixed in kernel 2.6.30.5. Anyone got any idea when this kernel version will become available for Ubuntu??

---

### Post by kngunn on 2009-10-02
I'm seeing a similar problem on my Lenovo ThinkPad T500.  At home it drops connections every half hour or so.  At work I cannot reproduce the problem.

At home I'm using WPA, at work it's WEP.  I believe that's the problem but have no solution.

---

### Post by pveurshout on 2009-10-03
> **kngunn said:**
> I'm seeing a similar problem on my Lenovo ThinkPad T500.  At home it drops connections every half hour or so.  At work I cannot reproduce the problem.

At home I'm using WPA, at work it's WEP.  I believe that's the problem but have no solution.

That's too bad :( do you have any idea whether this will remain a problem in Karmic?

---

### Post by kngunn on 2009-10-05
Yes.  It's a problem in Karmic as well.

---

### Post by VidJa on 2009-10-12
Hi all, same problem here. I'm running an up to date fresh install of 9.04 on a Dell 630c.. I'm sitting about 5 meters away from my access point and use WPA2.

The strange thing is that it connects upon boot, fails after 5 minutes or so randomly and then never reconnects. 

When I play with the settings, remove the auto configuration it 'might' reconnect, but often not. If it does, the connection is more or less stable for a longer period. When I connect a cable, the wireless suddenly remembers it should connect and at that time I have two IP addresses, one for wireless and one for the wired connection.
 
This is driving me crazy since I don't have problems on two different macs, a windows machine and a pda connecting without problems.

this dmesg log repeats itself about 50 times:
363.618859] wlan0: associated
[  373.641137] wlan0: disassociating by local choice (reason=3)
[  375.477449] wlan0: authenticate with AP 00:18:39:a1:28:a0
[  375.490172] wlan0: authenticate with AP 00:18:39:a1:28:a0
[  375.490193] wlan0: authenticated
[  375.490199] wlan0: associate with AP 00:18:39:a1:28:a0
[  375.495522] wlan0: RX ReassocResp from 00:18:39:a1:28:a0 (capab=0x411 status=0 aid=3)
[  375.495527] wlan0: associated

I hope someone finds a solution for this

---

### Post by arlwsbuntu on 2009-10-22
It does not really help to fix the problem, but:

**iwlagn** is extremely **poor quality driver** in Linux.

Have used hours and hours by fixing the problems. It is killing 64-bit systems. The driver somehow blocks the system - sometimes for tens of seconds. I _have_ been writing device drivers, so I _do_ know that there's something seriously wrong.

With HP EliteBook laptops it helps to disable 11n using module parameters - which you'll find conveniently using strings to module binary. The problem exist in all Elitebooks (we have 3 of those).

Currently sitting between shoes at my corridor using Ethernet cable because iwlagn gave totally out an system propably needs rebooting. I'm seriously considering to buy some other adapter.

Also whenever you need to change your wifi channel to say 9 - iwlagn does not work .. it just loops and loops and loops .. and the rest of your system is totally locked. And you see messages like:

Oct 22 20:33:06 hoopotin kernel: [253394.883189] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 3 bytes away.

This is due the handy logic of locking all interrupts within the driver? Is there really another driver or code accessing the same registers as iwlagn driver does? do you really need to lock **everything**?
I could use stronger words also.

This is just an open cry for better coding.

(I seriously think government should **pay** pension for coders - which produce bad code - not to code at all)

//arl

---

### Post by pveurshout on 2009-10-22
> **arlwsbuntu said:**
> (I seriously think government should **pay** pension for coders - which produce bad code - not to code at all)

Yeah, or just send them to a country where they deal with these things 'appropriately' :twisted: (nah, just kidding)

Anyway, thanks for your reply, Arl, your post clarifies a lot for me. Actually, I'm currently using an HP EliteBook, but I've never heard about this thing called '11n' you mentioned. Do you know how I can disable it and what the consequences of doing that are (apart from hopefully not getting disconnected anymore)?

---

### Post by arlwsbuntu on 2009-10-24
> **pveurshout said:**
> Do you know how I can disable it and what the consequences of doing that are (apart from hopefully not getting disconnected anymore)?

Not checked iwlagn source code (just strings), currently have in /etc/modprobe.d/options line::

options iwlagn amsdu_size_8K=1 11n_disable=1 debug=1 11n_disable50=1 amsdu_size_8K50=1 debug50=1

Maybe just 11n_disable=1 and 11n_disable50=1  might do the trick.

But without these options iwlagn cannot connect to my access point.

Anyway my 11n Linksys access point started to die, but it also has buggy code (ns proxy has/had poor locking for ns entries, and parallel ns queries caused corrupted entries, which caused wrong addresses for hosts) so cannot say if iwlagn options cause it or not.

//arl

---

### Post by pveurshout on 2009-10-26
Thanks!


By the way, this..
> **pveurshout said:**
> Hey, after installing the backports modules my dmesg keeps flooding with these messages:
```
[   75.919076] wlan0: beacon loss from AP ffff88013fd70ac0 - sending probe request
[  115.877120] wlan0: beacon loss from AP ffff88013fd70ac0 - sending probe request
```

(...)
..was gone after updating the kernel from 2.6.28-15 to 2.6.28-16. However, that also caused my system to start freezing randomly (although I suspect it may have something to do with handling larger files..not sure though) so I decided not to use it after all lol

---

### Post by pveurshout on 2010-03-19
Marked as solved. This is not an issue anymore in Karmic.

---

### Post by salemjones69 on 2012-05-24
I´ve had the same problem with it. I cant even go online thru my android, go thru my contacts or even touch my pho, for that matter, without losing connection on my desktop. On my ph (under wireless & connections), it´l first say ¨obtaining IP address  from 2wire142 (gateway 2wire from AT&T), then it´l say it&#347; scanning and then disconnected. I just updated up to 12.04 and thats when it happened, so I unstalled the 12.04 by reinstalled the 11.10 disk and im havin the same probs...](*,)

I dont have windows anymore, just ubuntu 11.10

I can check the internet & contacts/etc, whenever im away from home, but I can no longer go thru it at home..:(

I also thought that it may have somethin to do with ¨Magic Jack¨, but it´s not that either...:(

Can you please help me ?

I also have no idea where these codes go. Im new at linux and I see these codes to install/download or whatever for certain things on linux, and I have no idea where they go. I know how to copy/paste, just clueless on where to paste them...:confused:

I hope all this makes sense and nothin seriously bad...:confused:

Thanx

---

