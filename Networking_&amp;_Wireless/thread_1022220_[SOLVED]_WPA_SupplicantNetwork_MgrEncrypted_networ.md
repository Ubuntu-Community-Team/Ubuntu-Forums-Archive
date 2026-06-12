---
title: "[SOLVED] WPA Supplicant/Network Mgr/Encrypted network"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by KC1117 on 2008-12-26
Beginner needing guidance:
In my attempt to convert to Linux from Windows, I recently set up wireless on my Toshiba laptop using a madwifi driver by following several posts and getting some help from the forum.   At that point I was able to see all available networks on the Network Manager but was only able to connect to the unencrypted network of a neighbor (NETGEAR) and could not connect to my WEP encrypted network (2WIRE390).  

I then followed some directions to try and fix this using WPA-supplicant and change from the WEP to WPA-2. I don't know if I should have even gone that route for that particular problem, but now although I am connected to the NETGEAR, I cannot see in the Network Manager menu as before any of the other networks to attempt changing to them.  I can only see the available networks on 

I have several questions before I change anything else:
1)  I planned to change from WEP to WPA-2.  I read that was the best security-any advice just on that?
2)  Should I have changed something first at the router before doing anything on my laptop.  (My router is connected to my desktop pc) 
3)  I also read WPA supplicant and Network Manager don't work together/go together or something to that effect which made me wonder what the heck I was doing to begin with.  Is WPA supplicant another type of "network manager" or something entirely different?  
4)  So then where should I start to fix this so I have good security and on my own network?

Here are the results of some commands I see asked for on these type of posts.  If you need something else please let me know.  Thank you for helping us beginners who aren't afraid to roll up their sleeves a little in this conversion process.




kelly@kelly-laptop:~$ lsmod | grep ath

ath_rate_sample        16128  1 

ath_pci               249016  0 

wlan                  236400  4 wlan_scan_sta,ath_rate_sample,ath_pci

ath_hal               305376  3 ath_rate_sample,ath_pci


kelly@kelly-laptop:~$ iwconfig | grep ath

lo        no wireless extensions.



eth0      no wireless extensions.



wifi0     no wireless extensions.



ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""


kelly@kelly-laptop:~$ ifconfig | grep ath

ath0      Link encap:Ethernet  HWaddr 00:1b:9e:ad:15:5f  

kelly@kelly-laptop:~$ 




kelly@kelly-laptop:~$ iwlist scan


lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wifi0     Interface doesn't support scanning.



ath0      Scan completed :

          Cell 01 - Address: 00:1E:C7:1C:41:61

                    ESSID:"2WIRE390"

                    Mode:Master

                    Frequency:2.412 GHz (Channel 1)

                    Quality=33/70  Signal level=-62 dBm  Noise level=-95 dBm

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

          Cell 02 - Address: 00:0C:41:F3:E0:59

                    ESSID:"fatdaddycool"

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

                    Extra:bcn_int=100

          Cell 03 - Address: 00:09:5B:AB:78:EC

                    ESSID:"NETGEAR"

                    Mode:Master

                    Frequency:2.462 GHz (Channel 11)

                    Quality=19/70  Signal level=-76 dBm  Noise level=-95 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

                    Extra:bcn_int=100

---

### Post by kevdog on 2008-12-26
wpa_supplicant is actually the program that does the background wpa authentication.  Network Manager runs a wpa_supplicant library that was compiled into the sources.  It usually works well, however there are some hiccups some of the times.

If converting to WPA at the router level, I would first choose and setup and run WPA (1) then once things are up and running go to WPA(2).  There are definitely potential pitfalls with WPA2 although it is inherently better than WPA2.  

If changing your router, I would use either one computer that can possibly be connected via an ethernet cross-over cable and has wireless, or use two computers.  You will need a wired connection initially in case something is messed up during the change over.  The direct connection will allow to continue to access the router if the wireless is temporarily broken.

If having problems using network manager along with wpa_supplicant, that is where the headache starts.  The options at this point are to debug the problem either manually starting wpa_supplicant via the command line or using an alternative network manager something like wicd.

Manual command line debugging is not really that hard if you need to do it so don't be scared.  Proceed with courage since its not that hard.  Do not be afraid is the best advice I can give you -- and a helping hand if you have problems.

---

### Post by KC1117 on 2008-12-27
What should I do first?   I set up the drivers via command line so I'm not afraid to proceed if I have some clear instructions to follow.
Here is my equipment:
I have a desktop that is connected to the router and ethernet and is WindowsXP.
I have the laptop that is secured wireless on Windows Vista and can be connected via ethernet on either Windows Vista or Ubuntu.

Interestingly enough I had already bookmarked your thread to follow if I did not get a reply to this question.  It looks pretty straight forward.  Should I start there?

---

### Post by kevdog on 2008-12-27
Yes follow that thread, and if you have questions, post in that thread.  I reply to that thread if there are any unanswered questions.

---

### Post by KC1117 on 2008-12-28
Secured wireless internet up and running using the commands in Kevdog's tutorial in his signature line.  Thanks!!

---

