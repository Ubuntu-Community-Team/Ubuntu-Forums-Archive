---
title: "Jaunty, iwl3945, compat-wirless make issues, rfkill?"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by golfcaddy on 2009-06-10
Hi all,

Im on a fresh Jaunty install and im trying to update my wireless drivers so i can use the aircrack suite. Im not too well versed outside of a windows environment so bear with me! 

Card is

```
jammin@Mars:~$ sudo lspci | grep 3945ABG
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

Looking [here]("http://www.spinics.net/lists/linux-wireless/msg34288.html") and [here]("http://www.spinics.net/lists/linux-wireless/msg33938.html") im guessing i need to

> I just git-format-patch'ed the rfkill
commit from wireless-testing and reverted it in compat-wireless.  Then
compat-wireless built and worked ok.


However i dont have the slightest idea what git-format or rfkill are and what patch to use!

Here is my iwconfig

```

wlan0     IEEE 802.11abg  ESSID:"APazAoaBC"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:4D:FD:80:96   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=94/100  Signal level:-35 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


What ive done so far, grabbed the pre-reqs

```

sudo apt-get install build-essential
sudo apt-get install libssl-dev

```

Grabbed the latest tar from [here]("http://linuxwireless.org/download/compat-wireless-2.6/"), untarred, go into the dir then:

```

sudo make && make install && make load

```

which fails here:

```

  CC [M]  /home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath5k/attach.o
  CC [M]  /home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath5k/base.o
  CC [M]  /home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath5k/led.o
  LD [M]  /home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath5k/ath5k.o
  LD      /home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath9k/built-in.o
  CC [M]  /home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath9k/hw.o
In file included from /home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath9k/hw.c:20:
/home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath9k/ath9k.h:469: error: field ‘ops’ has incomplete type
make[5]: *** [/home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath9k/hw.o] Error 1
make[4]: *** [/home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath/ath9k] Error 2
make[3]: *** [/home/jammin/compat-wireless-2009-06-05/drivers/net/wireless/ath] Error 2
make[2]: *** [/home/jammin/compat-wireless-2009-06-05/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/jammin/compat-wireless-2009-06-05] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2

```

Any help with this would be much appreciated.

---

### Post by superprash2003 on 2009-06-11
post output of
1)ifconfig
2)sudo iwlist scan

---

### Post by MaindotC on 2009-06-11
Um...I installed 8.04 on my Thinkpad T60 which has an Intel card and the iwl3495 driver came with the install - I didn't have to download anything to get the wireless working.  Are you sure this is necessary?

---

### Post by golfcaddy on 2009-06-11
Thanks for the reply guys, just to confirm, i can connect to wifi just fine, and I can also get the card into monitor mode using iw and airmon-ng, the problem is getting the driver to inject packets. Looking [here:]("http://www.ubuntugeek.com/how-to-enable-packet-injection-on-a-intel-prowireless-3945abg-wireless-card.html")

> 
The ipwraw driver is not necessary since Hardy. Since kernel verion 2.6.27 iwl3945 already supports injection, and with kernel version 2.6.28 iwl4965 and iwl5XXX support injection.


Injection shouldnt be an issue, which is why i was trying to follow the aircrack wiki I linked to in my original post for iwl3945. 

As said above the only fixes to my make issue I can find mention rfkill and a patch of which im clueless! It doesnt seem to be a massively prevalent issue as there arent a lot of people asking about it, and also BackTrack 4 beta supports injection on my card straight out of the box so it must be possible; it would just be nice to get injection working on my Ubuntu install.

> **superprash2003 said:**
> post output of
1)ifconfig
2)sudo iwlist scan

```

jammin@Mars:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:44:ae:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:2c:94:39  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe2c:9439/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81110194 (81.1 MB)  TX bytes:2731299 (2.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-2C-94-39-34-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

And with mon0 in monitoring mode using airmon:

```

jammin@Mars:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:44:ae:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

mon0      Link encap:UNSPEC  HWaddr 00-1F-3C-2C-94-39-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4000 (4.0 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:2c:94:39  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe2c:9439/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81110368 (81.1 MB)  TX bytes:2731533 (2.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-2C-94-39-34-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Output of sudo iwlist scan

```

jammin@Mars:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:FD:80:96
                    ESSID:"NotMyAPName"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=83/100  Signal level:-51 dBm  Noise level=-88 dBm
                    Encryption key:on
                    IE: Unknown: 00094E6F49567348657265
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010024FF7F
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000098fc67981
                    Extra: Last beacon: 64ms ago

pan0      Interface doesn't support scanning.

mon0      Interface doesn't support scanning : Operation not supported

```

Thanks

---

### Post by MaindotC on 2009-06-11
Oh I didn't know you were cr4ck!ng.  I tried the same thing because the gas station where I work only has a protected network and there are usually no clients using it.  I tried the tutorial about "how to crack wep when there are no clients using it" and I never got mine to work.  Just wanted to let you know in case you want to try an atheros device or something a little more supported because the Intel didn't work for me.

---

### Post by golfcaddy on 2009-06-11
Thanks strAlan; yeah ive asked around on the aircrack forums to be told its a known issue and should be fixed in compat-wireless 2.7, see [here.]("http://forum.aircrack-ng.org/index.php?topic=5525.0")

And if you still intrested strAlan, i can confirm injection works straight out of the box on this card using BackTrack4 beta live DVD.

---

### Post by NoOne121 on 2009-06-11
intel iwl3945 works very well for aircrack-ng on jaunty.

i also have exactly the same issues as original poster when trying to install compat-wireless.

however there is one easy way to get aircrack-ng working on jaunty and that is to use the original driver that ships with jaunty and to forget compat-wireless untill someone comes up with the correct install method.

can you post output of 
modinfo iwl3945

because there is a big issue certain drivers and im baffled with every one EXCEPT the stock jaunty driver. i basically had to reinstall jaunty to get injection working properly after messing for days trying to get the 'perfect' drivers installed.

---

### Post by NoOne121 on 2009-06-11
just to add for injection disable networking by right clicking on network icon at the top of screen and click 'enable networking' to disable it.

then in terminal
sudo airmon-ng start wlan0
sudo aireplay-ng -9 mon0

---

### Post by golfcaddy on 2009-06-11
> **NoOne121 said:**
> just to add for injection disable networking by right clicking on network icon at the top of screen and click 'enable networking' to disable it.

then in terminal
sudo airmon-ng start wlan0
sudo aireplay-ng -9 mon0

Ahh, you absoloute legend :D Cant believe thats all it was!

I also have been doing the same, trying to get the "perfect" drivers running, never crossed my mind to disable networking.

```

jammin@Mars:~$ sudo aireplay-ng -9 mon0
17:53:30  Trying broadcast probe requests...
**17:53:30  Injection is working!**
17:53:32  Found 1 AP 

```

Excellent, thanks again NoOne123 ;)

---

### Post by NoOne121 on 2009-06-12
trust me when i say dont mess with compat-wireless, dont touch ipwraw either(although it does inject ok but no net access). with compat-wireless i can test inject ok but i cannot harvest iv's ? and i have read every piece of advice out there to figure out the problem including...

[http://aircrack-ng.org/doku.php?id=i_am_injecting_but_the_ivs_don_t_increase](http://aircrack-ng.org/doku.php?id=i_am_injecting_but_the_ivs_don_t_increase)

there is something to do though if you are still on a quest for the perfect setup for iwl3945 and that is to patch the mac80211 stack. theres a great guide on another foum to do this but im not sure its ok to link to other forums here.

hey i got a great script, from aircrack-ng forum, for you to make it easier to crack your wep router. just use

sudo ./ws2.tcl RouterName mon0 channel

ahh must install tcl to use script

sudo apt-get install tcl

enjoy

---

### Post by MaindotC on 2009-06-13
Can you get this to work when there are no clients using the AP?

---

### Post by NoOne121 on 2009-06-20
yes....no problem although it can take longer. it just helps to have data being generated by the router but its not necessary to have clients on the AP.

---

### Post by MaindotC on 2009-06-20
I don't think the AP i'm testing is generating any data :(

---

### Post by NoOne121 on 2009-06-20
yes ive had that too....but ive still managed to get aircrack-ng to crack the wep key.
have you tried the script i posted?

do you authenticate with the AP ok? they might hace mac filtering enabled but thats not a problem if you have a client mac to spoof.

---

### Post by MaindotC on 2009-06-22
I'll load it onto my T61 and try again.  I should have a result for you tomorrow night.  As for authentication - I dunno if they have MAC filtering and I'm not really sure what MAC's are used at this location.  I'm kind of on the outside and I have to audit it :(  Well I'll give it a try and have a result for you later.  Thanks and I didn't look at the script but I'll check it.

---

### Post by Tox|k on 2009-10-25
I've been trying to get injection working with my intel3945 and just can't seem to get it to go. It only ever seems to inject once and then does not until I restart the module/device. From what I can tell, it's not that it injects only one packet, but that injection only works once and only after the module has been freshly started. It's as though after something is done using injection, it isn't released/reset/whatever properly for future use.

I've tried with compat-wireless and ipwraw and neither seemed to make an improvement. I have since completely reinstalled ubuntu, not because anything was destroyed, but because I figured it may be a good idea after messing with so many different drivers.

I've tried everything recommended in this thread, but, again, it didn't make any improvement.

I was wondering if anyone else had come up against this issue and could provide some help, or at least somewhere else I could look for help.

FYI, I'd mostly been using *aireplay-ng --test wlan0* to test injection, but also tried *aireplay-ng --arpreplay* as well.

---

