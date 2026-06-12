---
title: "Connect to wireless without GUI"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by lunix- on 2010-02-10
Hi ubuntu community!
For a long time I been struggeling with how to connect to my home wireless network from console.

The wireless connecter on gnome does the job perfectly though.
There I just type in the key when prompted and it works great! (thanks ubuntu!)

But I'm planning to set up a headless linux installation without any GUI and I need to find out how to connect from console.

To connect on other networks I do this and it usually works: 
#ifconfig wlan0 up
#iwconfig essid "network" key 10DIGITHEX
#dhclient

But on my home network, this doesnt work at all. I get no dhcp offers.. 

Is it possible to see what the nm-applet does to connect and make a nogui script from that? :)

Here is the output from 'iwlist scan' command:

          Cell 01 - Address: MA:CA:DD:RE:SS:00
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key: on
                    ESSID:"my network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000020sc7f40244
                    Extra: Last beacon: 89940ms ago
                    IE: Unknown: 0008417269665474
                    IE: Unknown: 0104848B9
                    IE: Unknown: 03010
                    IE: Unknown: 2A010
                    IE: Unknown: 32080C121830406C


Here is a working iwconfig output (connected using Gnome) :
wlan0     IEEE 802.11bg  ESSID:"my network"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:20:B2:E0:33:82  
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

Any help would be greatly appriciated!     

(my first post on ubuntu's forums!  YAAY :D    Hope Ill be able to conrtibute soon)

---

### Post by bkratz on 2010-02-10
Sorry, afraid I would be of little help except there is a very long tutorial thread on manually connecting.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by lunix- on 2010-02-10
Thanks for a lightning fast reply and for a nice link! :)
I have been reading and testing for a while now and I got a little further. But I'm still not able to do what I need to:

When i disconnect with the gnome-connection-manager and then try to reconnect with my script, then nothing works.

but: When I _don't_ disconnect from internet with the connection manager, and just run my script, then I'm able to reconnect using my script.  I guess that means that my script is functional, but just need some more vital data to be able to connect from scratch?
Here is my connection script so far:  
```

#!/bin/bash
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up

iwconfig wlan0 essid "my network"
iwconfig wlan0 key 10DIGITHEX              # s:ASCII_KEY

iwconfig wlan0 key open
#iwconfig wlan0 key restricted     ( I try switching between those two   without much luck..) 

iwconfig wlan0 ap MA:CA:DD:RE:SS:00

iwconfig wlan0 channel 5
iwconfig wlan0 mode Managed
dhclient wlan0
```

Here is my dmesg | tail:
```
[26901.357108] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[26901.396447] wlan0: direct probe to AP MA:CA:DD:RE:SS:00 try 1
[26901.404445] wlan0: direct probe to AP MA:CA:DD:RE:SS:00 try 1
[26901.404476] wlan0 direct probe responded
[26901.404479] wlan0: authenticate with AP MA:CA:DD:RE:SS:00
[26901.407824] wlan0: authenticated
[26901.407827] wlan0: associate with AP MA:CA:DD:RE:SS:00
[26901.409822] wlan0: RX AssocResp from MA:CA:DD:RE:SS:00 (capab=0x431 status=0 aid=7)
[26901.409825] wlan0: associated
[26901.419820] wlan0: disassociating by local choice (reason=3)

```

Seems that the 'disassociating' from the dmesg is because of timeout, after waiting a long time for dhcp offers.


The output from running script:
```
root@syntaxerror:/home/a# sh scriptname
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/MA:CA:DD:RE:SS:00
Sending on   LPF/wlan0/MA:CA:DD:RE:SS:00
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 10.0.0.138 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/MA:CA:DD:RE:SS:00
Sending on   LPF/wlan0/MA:CA:DD:RE:SS:00
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

It would be really nice to understand what fails here.

---

### Post by lunix- on 2010-02-11
bump. anyone?

:)

---

### Post by chili555 on 2010-02-11
Is Network Manager still running on the computer? If so, it is doubtful you will *ever* connect manually. NM just wants one set of hands on the steering wheel; not yours. Next, if this is to be a headless server or HTPC, how are you ever going to find it with a constantly changing IP address? Winbind or samba or all those Redmond tools??? Tsk, tsk!

It will work perfectly with a static IP address in */etc/network/interfaces*. My interfaces file, with a few details disguised, is here:> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid mylilrouter
wireless-key 096xxxxAFE 

#auto eth0
iface eth0 inet dhcpBefore login, the network is up and running. I have tested and run this on home servers many times.

---

### Post by lunix- on 2010-03-19
Thanks guys for trying to help!! So far I still can't connect to wireless(WEP) from CLI.. But luckily the network-manager-gnome gets me connected at least :)

I did set up a headless gateway based on ubuntu wich also works as a samba file&print server and "torrent server".  Works beautifully, though I'd like to uninstall X. Until I know how to connect from CLI, I guess I'm stuck with gnome running..  


A strange thing that happens is when I write
iwconfig wlan0 essid "correct essid"
and then write "iwconfig".  
It returns: 
unassociated   Mode:Managed  Frequency=2.432
Access Point: Not-Associated Bit Rate etc etc etc

while when I write a "incorrect essid" and write iwconfig to check configuration, it returns:
unassociated   ESSID:"incrorrect essid"
Mode:Managed  Frequency=2.432 Access Point: Not-Associated 
Bit Rate etc etc etc

So `iwconfig` doesn't show ESSID when I type in the correct essid. Anyone with the same problem or knows how to fix it?

---

### Post by lunix- on 2010-03-21
OK, did some more research today.  I have two identical laptops. One with a updated fresh install of ubuntu 9.10 and the other one has a Backtrack4 Pre-release installed.

The first thing I do on the computer (the backtrack one) is, starting it up. It does not start X automaticly..  Then I do following:
$su

ifconfig
#eth0 and eth1 are not showing up so i:
ifconfig eth1 up
#then,
ïwconfig essid eth1 up
#SOMETHING COOL HAPPENS: IWCONFIG ACTUALLY WORKS!!!  Unlike on my three other computers with ubuntu installed, when I write iwconfig the essid shows up as it should! why why why does this not work on ubuntu 9.10 ??!!
(did not work on jaunty either)

#next I write the key
iwconfig eth1 key xxxxxxxxxx

and then dhclient eth1 to get IP,  and all works very very well.. 

Why does it work on other distros, but not on ubuntu?
What happened to ubuntu here?  

It can't be driver issues either I guess. Since on three different network cards/computers, none of them can connect this way.

Next thing Im going to try is installing ubuntu server edition on the same computer that connected nicely from backtrack. Can't say I have high hopes as I have tried to connect from cli without gdm running on ubuntu 9.10 before several times without any luck.

---

### Post by chili555 on 2010-03-21
> Why does it work on other distros, but not on ubuntu?
What happened to ubuntu here? Network Manager happened. It is very difficult, maybe impossible to grab control with manual tools, iwconfig, etc., with NM running, as you have seen.

NM is not present on Backtrack, if I remember correctly.> Next thing Im going to try is installing ubuntu server edition NM is not present on the server edition and I will be very surprised if it doesn't connect immediately.

---

### Post by 2hot6ft2 on 2010-03-21
> **chili555 said:**
> Network Manager happened. It is very difficult, maybe impossible to grab control with manual tools, iwconfig, etc., with NM running, as you have seen.

NM is not present on Backtrack, if I remember correctly.NM is not present on the server edition and I will be very surprised if it doesn't connect immediately.
You can disable NM by going to System > Preferences > Startup Applications
Uncheck the box for it and close then open it again keep repeating until it stays unchecked.
That will keep NM from loading at startup, recheck the box to re-enable and reboot.

BackTrack 4 has WICD, but you have to bring up the adapter manually and setup the connection in WICD before you can connect to anything using WICD. And if you don't set it to connect automatically then you have to connect yourself.

Since BT4 is for pentesting you don't always want it to try and connect automatically.

---

### Post by lunix- on 2010-03-21
Thanks chili555 & 2hot6ft2 for fast replies! :)
downloading server edition now

I have tried connecting from cli on 9.10 desktop edition (32 and 64bit) after 
/etc/inid-d/gdm stop
/etc/init.d/networking restart
without that helping anything either, but will be interesting to try the server edition :)

---

### Post by lunix- on 2010-03-22
Thanks for great help guys!!!

Problem finally solved:   (been struggeling with this for a looong time)
Some programs running on ubuntu desktop edition that made the iwconfig command not work.  I tried removing the default connection programs and using wicd instead, but this didnt fix the problem either.   

I ended up not using any nework manager at all, and not X or any graphical interface either. and it has been a very pleasant experience indeed! Ubuntu server is the newly installed os for gateway/samba-server and everything is just working perfectly! Sharing internet and samba up and running before logging on.  Thanks for helping everybody!

:-D

---

