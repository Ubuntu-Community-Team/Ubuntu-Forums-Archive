---
title: "Toshiba NB100 &amp; Atheros AR242x Failure"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by freechiru on 2009-10-03
OK, I am trying desperately to connect my Toshiba NB100 netbook to the internet via wireless (the ethernet connection, after some trial and error and much rebooting, seems to be working).  I've done a lot of reading today; I know the problem is because my wireless card (Atheros AR242x 802.11abg) is not very well supported by Ubuntu,and I know that other people have managed to fix it.  I've tried following their step-by-steps (e.g. [http://ubuntuforums.org/showthread.php?t=1063370](http://ubuntuforums.org/showthread.php?t=1063370) ) but each time something has gone wrong -- not worked as the step-by-step says it should.

This is probably because I really don't know the first thing about computers, let alone how to work Ubuntu.  When the terminal refuses to make Madwifi because it needs me to "set the KERNELPATH stop" I simply do not understand and a google search didn't turn up anything more meaningful to me.

So could anyone explain to a completely inexperienced user how to make my wireless card work, please?  (:

---

### Post by t0mppa on 2009-10-03
That would likely be caused by you not having the kernel (the core package that is shared by all Linux distros) headers installed. They're required when compiling packages manually and for some odd reason, they're not installed during the default Ubuntu install.

Try running **sudo apt-get install linux-headers-generic** from the terminal. That will install a meta package which will ensure that you always have the latest headers installed.

---

### Post by chili555 on 2009-10-03
Please make sure you have *build-essential* and *linux-headers-generic* installed. You can install them with System -> Admin -> Synaptic. Afterwards, open a terminal and do:```
make clean
make
```Please post any errors. You may get warnings, but those are OK.

---

### Post by freechiru on 2009-10-03
Getting somewhere, thank you!  (:  OK, I had build-essentials installed already; I re-installed it just to make sure.  But I can't find linux-headers-generic; when I tried t0mppa's way, I got:

Reading package lists...  Done
Building Dependency Tree
Reading state information...  Done
E: Couldn't find linux-headers-generic

And when I tried to search for it with Synaptic, it didn't find it; a search for "linux-headers" produced a long list of linux headers with kernel numbers (I assume) after them.  Which one of those do I want?  Or where is generic?  (My kernel number is 2.6.24-24-lpia).

Thank you!

---

### Post by freechiru on 2009-10-03
I've jumped the gun and installed the ones which instead of generic have the kernel number after them.  Is that a good move?

---

### Post by t0mppa on 2009-10-03
Ah yes, you're not on a generic kernel, that'd be why it's not found. Try looking for *linux-headers-lpia* instead. Anyway, what you did should work for the moment. But the reason why installing the meta package makes life so much easier is that you won't run into this same problem later, when you've updated your kernel to a new one and then forgotten to install the headers manually.

---

### Post by freechiru on 2009-10-03
Thanks, I'll try that (and I think I understand what you mean, too, which is nice!)

OK, I managed to install Madwifi, I think, like the step-by-step I linked to said.  After the "sudo make install" command, I got a message telling me that there were traces of older Madwifi installations (failed ones, if that was anything to do with me).  It said that if I were uninstalling them, to select r(emove), or if I was installing, to consider removing old modules.  Which confused me; in the end, I clicked "r", and it seemed to do something -- how do I tell if it has installed Madwifi?

Then I followed the rest of the step-by-step anyway and have rebooted.  But I can't see the network manager icon at the top of the screen; it seems to have disappeared after I updated last night, but sometimes (and I have no idea when) it seems to reappear.  Do you know how I can access it or something else to see what networks are available/connect to them (if Madwifi *is* installed)?

Thanks again...

---

### Post by t0mppa on 2009-10-03
It's always a good decision to remove any older versions of programs you're installing to avoid possible conflicts.

If the make did not specifically end on an error message, the compilation was successful. You can check if there are any Atheros drivers (just to be sure, you're not having multiple ones, as ath5k is the default one and multiple drivers for a single interface is always a bad thing) loaded by running **lsmod | grep ath**.

You can do a manual scan by running **sudo iwlist scanning** from the terminal. If that gives you an error, then run **lshw -C network** and post the results.

---

### Post by freechiru on 2009-10-03
OK, stupid question: is there any way I can copy out of terminal to paste here?  Or do I have to type it out?  I did lsmod, and I don't think I can interpret the results myself.  I also did iwlist, which came up with a long result under wlan0 which again I don't understand.  Continuing thanks for your help (:

Also, while I'm thinking about it...  Considering that Atheros cards are such a problem for Ubuntu, do you reckon it would work to just disable the inbuilt card and buy a linux-compatible USB wireless card?  Or would that be even more complicated?

---

### Post by freechiru on 2009-10-03
Also, I get "command not found" for "lshw".

---

### Post by halitech on 2009-10-03
for lshw, it doesn't come installed by default so you need to install it
```
sudo apt-get install lshw
```

to copy from the terminal, use your mouse to highlight what you want to copy and then right click - copy. To paste it you can also right click - paste.

If you want to use the terminal, its CTRL - ALT - C to copy and CTRL - ALT -V to paste.

---

### Post by freechiru on 2009-10-03
Thanks, halitech, I hadn't realised that...  And big thanks for how to c&p!  That'll save a lot of time and effort.

OK.

lsmod | grep ath produces:
ath_pci               100000  0 
wlan                  205424  1 ath_pci
ath_hal               192464  1 ath_pci
ath5k                 100608  0 
lbm_cw_mac80211       216180  1 ath5k
lbm_cw_cfg80211        36192  2 ath5k,lbm_cw_mac80211
led_class               6020  1 ath5k

sudo iwlist scanning:
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:D2:12:46:3F
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=98/100  Signal level:-41 dBm  Noise level=-104 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000198223a008
                    Extra: Last beacon: 1040ms ago
          Cell 02 - Address: 00:14:7F:96:CA:6E
                    ESSID:"BTHomeHub-E84F"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=7/100  Signal level:-98 dBm  Noise level=-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000b945257847b
                    Extra: Last beacon: 464ms ago

lshw -C network:
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:1e:33:7d:75:54
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.10 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:a2:c5:df
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

If someone could interpret those for me (or point me in the direction of an explanation), I would be very grateful (:

---

### Post by halitech on 2009-10-03
I'm no wireless expert but it looks like everything is up and loaded properly

[color="red"]Quality=7/100 Signal level:-98 dBm Noise level=-103 dBm[/color]
[color="red"]product: AR242x 802.11abg Wireless PCI Express Adapter[/color]

what does ```
sudo dhclient wlan0
```give for a result?

---

### Post by t0mppa on 2009-10-03
Ok. You still have the ath5k loaded and it's the one that's associated with your wireless interface. Also, it appears to be working, since it's picking up networks.

So, could be you went through all this trouble for no reason. Is the first network your own AP? 98% signal strength sure means it's right next to your laptop. If so, can you connect to it? Or are you still having problems with your Network Manager not showing up?

Oh and run a **sudo modprobe -r ath_pci** for now to unload the Madwifi and comment out (add a # in front of the line) the ath_pci line from the */etc/modules* file, so that the Madwifi doesn't get loaded during boot and we can first see if the ath5k works for you, as that's already up and running.

---

### Post by freechiru on 2009-10-03
We tried pinging the wireless router, but it doesn't connect when the ethernet's not plugged in, although I'm told we were pinging the wireless bit of the router, not the ethernet -- might it be that any connection's coming down the wire rather than through the wireless?

As you can tell, I have no idea what I'm talking about.  Anyways.

sudo dhclient wlan0:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:63:a2:c5:df
Sending on   LPF/wlan0/00:21:63:a2:c5:df
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Apologies if the paste is hard to read; it doesn't seem to like copying with the same formatting as in the terminal. Does that help at all?

---

### Post by freechiru on 2009-10-03
The router's literally a metre away.  I don't know what an AP is, but it's our home network. My network manager still isn't showing up -- is there any way of getting to that other than through the top right of the screen?  And I ran sudo modprobe -r ath_pci, but nothing appreciable happened -- just got the command line again -- does that mean it worked or not?

Thank you!

---

### Post by t0mppa on 2009-10-03
The paste is simple enough to read (but to make it look like it does on your terminal, ie. no autoformatting, you can put it inside [ code][ /code] tags without the spaces). There are no DHCP offers from the AP, so a connection isn't made. Have you set up the details of your network anywhere yet? Can't just make a random connection, especially if your network is secured.

Oh and pinging through the wireless won't work before you have established a connection to a network.

> **freechiru said:**
> The router's literally a metre away. I don't know what an AP is, but it's our home network. My network manager still isn't showing up -- is there any way of getting to that other than through the top right of the screen? And I ran sudo modprobe -r ath_pci, but nothing appreciable happened -- just got the command line again -- does that mean it worked or not?

Ah, sorry. AP is an abbreviation of Access Point, which is the term used for wireless routers. 

Well, I'm not sure how to do it the fancy way on the Netbook Remix, as I've never used it, but this should work for restarting the Network Manager from the terminal:```
killall nm-applet
sudo nm-applet --sm-disable &
```

And yes, the modprobing worked, if it didn't display any output. If you want to be sure, you can check with **lsmod | grep ath** again to make sure that only ath5k shows up.

---

### Post by freechiru on 2009-10-03
I looked, and the modprobing did work -- excellent!  AP -- Access Point -- I'm sure I should have been able to guess that...  Ah well.

Um.  Since you last posted I had a hunt around myself; on a similar post (about disappearing applets), someone had advised the person whose applet had disappeared to just scrap it and install WICD.  His instructions worked perfectly, so that's what I have done...

I'm going to try and use that to establish a connection now.  I could always re-install network manager, though, if that would make it easier for you to know what's (not) working.

Wish me luck...

---

### Post by freechiru on 2009-10-03
I've tried connecting through WICD.  I'm effectively coming up against the same problem as I started out with: the computer can see the network, and I can input all the details for it, but when I press connect is simply tries to and then gives up, with no error message but no connection.  (This is exactly what's been happening to me with Network Manager earlier.)

It may be that I'm not entering all the information right, but it's the information my dad gave me (before he went to bed...) so I think it's OK.  And if it isn't, then I can't do any more to it until tomorrow.

Is there any way of determining where exactly the connection is failing?

---

### Post by t0mppa on 2009-10-03
Yeah, my bad, wasn't thinking about the obscurity of said term for people who don't play with these things daily.

Well, you can run **less /var/log/syslog | grep DHCP** to check if the DHCP handshake goes through, but I'd guess it says the same as before about no DHCPOFFERS found.

Since you went through all the trouble of installing the Madwifi driver, can always test that one by unloading ath5k first and loading it up afterwards (check with lshw that it gets associated) with ```
sudo modprobe -r ath5k
sudo modprobe ath_pci
``` and trying to connect again. But as it's picking up networks, I'm fairly sure it's not a driver issue, never hurts to try though.

One possibility that would explain this kind of behavior is that your dad has enabled MAC filtering on the router and forgot to add your cards MAC address into the list of allowed addresses, which means the router is simply ignoring any traffic from your card.

I think I'll head off to bed myself, so unless you can get it working by yourself or with the help of someone else, ask your dad on the morning, if you have the correct key and if he has enabled MAC addressing just to be sure you have the right details, could be something else as well, but I can't come up with any brilliant solutions this late and it never hurts to play safe. I'll check back on this thread tomorrow.

---

### Post by freechiru on 2009-10-03
OK, I'll see if that comes up with anything and, if not, better check on the details in the morning.  Thanks for all your help so far -- I really appreciate it!

---

### Post by freechiru on 2009-10-03
For the record:

I tried ess /var/log/syslog | grep DHCP and it looks to me like there may have been some activity at some point; I would need someone else to interpret it for me, though.

I tried loading Madwifi instead, but it didn't work -- no difference.

I found this thread: [http://ubuntuforums.org/showthread.php?t=1237716&highlight=atheros](http://ubuntuforums.org/showthread.php?t=1237716&highlight=atheros) which seems to relate to an at least similar problem; I tried to follow it through, but got bogged down.

Hopefully I've managed to return Madwifi to the state it was in before that, and I have switched back to ath5k anyway.

Still have no clue...

---

### Post by pdc on 2009-10-03
sorry: error

---

### Post by t0mppa on 2009-10-04
Oh, something other than just DCHPDISCOVERs? Just paste it here then and let's have a look.

Well, the only substance on that thread was to rebuild the Madwifi with the latest snapshot, but you had already done that earlier, so it wouldn't have made a difference anyway.

---

### Post by freechiru on 2009-10-04
```
Oct  2 14:05:49 TOSHIBA-User NetworkManager: <info>  Activation (ath1) Beginning DHCP transaction. 
Oct  2 14:05:49 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath1 
Oct  2 14:05:50 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath1 
Oct  2 14:05:50 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 14:05:55 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 11
Oct  2 14:06:06 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 14
Oct  2 14:06:20 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 1
Oct  2 14:06:21 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 14:06:30 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface ath1 
Oct  2 14:06:30 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ath1 
Oct  2 14:07:07 TOSHIBA-User NetworkManager: <info>  Activation (ath1) Beginning DHCP transaction. 
Oct  2 14:07:07 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath1 
Oct  2 14:07:09 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath1 
Oct  2 14:07:13 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 14:07:18 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 14
Oct  2 14:07:32 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 14:07:44 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 14:07:52 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface ath1 
Oct  2 14:07:52 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ath1 
Oct  2 14:11:18 TOSHIBA-User NetworkManager: <info>  Activation (ath1) Beginning DHCP transaction. 
Oct  2 14:11:18 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath1 
Oct  2 14:11:20 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath1 
Oct  2 14:11:23 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 14:11:26 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 14:11:33 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 10
Oct  2 14:11:43 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 10
Oct  2 14:11:53 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 1
Oct  2 14:11:54 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 14:12:03 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface ath1 
Oct  2 14:12:03 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ath1 
Oct  2 14:13:12 TOSHIBA-User NetworkManager: <info>  Activation (ath1) Beginning DHCP transaction. 
Oct  2 14:13:12 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath1 
Oct  2 14:13:13 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath1 
Oct  2 14:13:16 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 14:13:22 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 14:13:30 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 14:13:39 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 14:13:47 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 14:13:57 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface ath1 
Oct  2 14:13:57 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ath1 
Oct  2 14:17:41 TOSHIBA-User NetworkManager: <info>  Activation (ath1) Beginning DHCP transaction. 
Oct  2 14:17:41 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath1 
Oct  2 14:17:42 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath1 
Oct  2 14:17:42 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 14:17:47 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 14:17:52 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 13
Oct  2 14:18:05 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 14:18:13 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 14:18:21 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface ath1 
Oct  2 14:18:21 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ath1 
Oct  2 14:18:49 TOSHIBA-User NetworkManager: <info>  Activation (ath1) Beginning DHCP transaction. 
Oct  2 14:18:49 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath1 
Oct  2 14:18:50 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath1 
Oct  2 14:18:52 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 14:19:00 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 21
Oct  2 14:19:21 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 2
Oct  2 14:19:23 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 14:19:33 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface ath1 
Oct  2 14:19:33 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ath1 
Oct  2 14:30:55 TOSHIBA-User NetworkManager: <info>  Activation (ath1) Beginning DHCP transaction. 
Oct  2 14:30:55 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath1 
Oct  2 14:30:56 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath1 
Oct  2 14:30:56 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 14:31:04 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 19
Oct  2 14:31:23 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 4
Oct  2 14:31:27 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 14:31:36 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface ath1 
Oct  2 14:31:36 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ath1 
Oct  2 15:16:07 TOSHIBA-User NetworkManager: <info>  Activation (ath1) Beginning DHCP transaction. 
Oct  2 15:16:08 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath1 
Oct  2 15:16:09 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath1 
Oct  2 15:16:12 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 15:16:15 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 15:16:23 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 15
Oct  2 15:16:38 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 15:16:43 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 15:16:54 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface ath1 
Oct  2 15:16:54 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ath1 
Oct  2 19:53:42 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 19:53:45 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 19:53:52 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 19:54:01 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 15
Oct  2 19:54:16 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 19:57:10 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 19:57:15 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 19:57:23 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 14
Oct  2 19:57:37 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 4
Oct  2 19:57:41 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 20:10:02 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 20:10:09 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 20:10:21 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 20:10:28 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 2
Oct  2 20:10:30 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 20:13:23 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 20:13:31 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 10
Oct  2 20:13:41 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 13
Oct  2 20:13:54 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 20:20:03 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 20:20:09 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 21
Oct  2 20:20:30 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 4
Oct  2 20:20:34 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 20:24:49 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 20:24:54 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 20:25:03 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 17
Oct  2 20:25:20 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 20:25:50 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:20:33 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:20:34 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:20:34 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:20:38 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:20:38 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:20:44 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 21:21:02 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:21:02 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:21:09 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:21:09 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:24:48 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:29:52 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:29:52 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:29:52 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:29:54 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:29:58 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:30:00 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 18
Oct  2 21:30:04 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 13
Oct  2 21:30:17 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 21:30:18 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:30:25 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:30:29 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:30:33 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:32:33 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:32:33 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:32:33 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 21:32:35 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 21:32:35 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 21:32:43 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 16
Oct  2 21:32:43 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 16
Oct  2 21:32:59 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:32:59 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:33:06 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:33:06 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:34:15 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:34:22 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 21:34:34 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 21:34:46 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:38:09 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:38:16 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 18
Oct  2 21:38:17 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:38:24 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 18
Oct  2 21:38:34 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:38:40 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:38:42 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:38:48 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:39:41 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 21:39:44 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 21:39:47 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 21:39:52 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 21:40:01 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 11
Oct  2 21:40:12 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:41:13 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 21:41:18 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 21:41:30 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 14
Oct  2 21:41:44 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:45:07 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 21:45:10 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 21:45:13 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:45:19 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:45:26 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 21:45:36 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 21:45:38 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:45:39 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:45:44 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 21:45:46 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 15
Oct  2 21:45:47 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:45:54 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 15
Oct  2 21:46:01 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:46:07 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:46:09 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:46:15 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:48:24 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 4
Oct  2 21:48:28 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 10
Oct  2 21:48:38 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 21:48:50 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 21:48:55 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:51:08 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:51:14 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 21:51:22 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 10
Oct  2 21:51:32 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:51:39 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:53:26 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:53:33 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 15
Oct  2 21:53:34 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:53:41 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 15
Oct  2 21:53:48 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 21:53:56 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 21:53:57 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:54:05 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:54:30 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:54:37 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 15
Oct  2 21:54:51 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:54:52 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 21:54:57 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 15
Oct  2 21:55:01 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:55:12 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 10
Oct  2 21:55:22 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:57:42 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 21:57:49 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 10
Oct  2 21:57:59 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 21:58:07 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 21:58:13 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 21:59:53 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 21:59:53 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  2 22:00:01 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 22:00:10 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 10
Oct  2 22:00:20 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 4
Oct  2 22:00:24 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 22:02:22 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 22:02:25 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 22:02:28 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 22:02:35 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 14
Oct  2 22:02:49 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 4
Oct  2 22:02:53 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 22:03:39 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 22:03:46 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 22:03:58 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 22:03:59 TOSHIBA-User NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct  2 22:03:59 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct  2 22:04:00 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct  2 22:04:01 TOSHIBA-User dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Oct  2 22:04:03 TOSHIBA-User dhclient: DHCPOFFER of 192.168.1.64 from 10.0.0.138
Oct  2 22:04:03 TOSHIBA-User dhclient: DHCPREQUEST of 192.168.1.64 on eth1 to 255.255.255.255 port 67
Oct  2 22:04:03 TOSHIBA-User dhclient: DHCPACK of 192.168.1.64 from 10.0.0.138
Oct  2 22:04:03 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct  2 22:04:03 TOSHIBA-User NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct  2 22:04:10 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 22:05:47 TOSHIBA-User dhclient: DHCPRELEASE on eth1 to 10.0.0.138 port 67
Oct  2 22:05:48 TOSHIBA-User NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct  2 22:05:48 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct  2 22:05:49 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct  2 22:05:52 TOSHIBA-User dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Oct  2 22:05:52 TOSHIBA-User dhclient: DHCPOFFER of 192.168.1.64 from 10.0.0.138
Oct  2 22:05:52 TOSHIBA-User dhclient: DHCPREQUEST of 192.168.1.64 on eth1 to 255.255.255.255 port 67
Oct  2 22:05:52 TOSHIBA-User dhclient: DHCPACK of 192.168.1.64 from 10.0.0.138
Oct  2 22:05:52 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct  2 22:05:53 TOSHIBA-User NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct  2 22:05:58 TOSHIBA-User dhclient: DHCPRELEASE on eth1 to 10.0.0.138 port 67
Oct  2 22:06:01 TOSHIBA-User NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct  2 22:06:01 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct  2 22:06:02 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct  2 22:06:03 TOSHIBA-User dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Oct  2 22:06:03 TOSHIBA-User dhclient: DHCPOFFER of 192.168.1.64 from 10.0.0.138
Oct  2 22:06:03 TOSHIBA-User dhclient: DHCPREQUEST of 192.168.1.64 on eth1 to 255.255.255.255 port 67
Oct  2 22:06:03 TOSHIBA-User dhclient: DHCPACK of 192.168.1.64 from 10.0.0.138
Oct  2 22:06:03 TOSHIBA-User NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct  2 22:06:03 TOSHIBA-User NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct  2 22:07:51 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 4
Oct  2 22:07:55 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 22:08:01 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 22:08:07 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 22:08:14 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 8
Oct  2 22:08:22 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 22:08:39 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 4
Oct  2 22:08:43 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 22:08:49 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 22:08:56 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 22:09:08 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 2
Oct  2 22:09:10 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 22:10:02 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 22:10:08 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 22:10:14 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 22:10:21 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 22:10:30 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 22:10:33 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 22:11:06 TOSHIBA-User dhclient: DHCPRELEASE on eth1 to 10.0.0.138 port 67
Oct  2 22:12:03 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 3
Oct  2 22:12:06 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 22:12:11 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 22:12:17 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 12
Oct  2 22:12:29 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
Oct  2 22:12:34 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 22:12:59 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
Oct  2 22:13:05 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 22:13:14 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 14
Oct  2 22:13:28 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 2
Oct  2 22:13:30 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  2 22:14:39 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 4
Oct  2 22:14:43 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 9
Oct  2 22:14:52 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 7
Oct  2 22:14:59 TOSHIBA-User dhclient: DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 11
Oct  2 22:15:10 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  3 19:09:00 TOSHIBA-User NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct  3 19:09:00 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  3 19:09:00 TOSHIBA-User NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit 
Oct  3 19:09:04 TOSHIBA-User dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Oct  3 19:09:06 TOSHIBA-User dhclient: DHCPOFFER of 192.168.1.66 from 10.0.0.138
Oct  3 19:09:06 TOSHIBA-User dhclient: DHCPREQUEST of 192.168.1.66 on eth1 to 255.255.255.255 port 67
Oct  3 19:09:06 TOSHIBA-User dhclient: DHCPACK of 192.168.1.66 from 10.0.0.138
Oct  3 19:09:06 TOSHIBA-User NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Oct  3 19:11:16 TOSHIBA-User NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 5270 
Oct  3 19:11:16 TOSHIBA-User NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct  3 19:11:16 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  3 19:11:16 TOSHIBA-User NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Oct  3 19:11:16 TOSHIBA-User dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct  3 19:11:16 TOSHIBA-User dhclient: DHCPOFFER of 192.168.1.66 from 10.0.0.138
Oct  3 19:11:16 TOSHIBA-User dhclient: DHCPREQUEST of 192.168.1.66 on eth1 to 255.255.255.255 port 67
Oct  3 19:11:16 TOSHIBA-User dhclient: DHCPACK of 192.168.1.66 from 10.0.0.138
Oct  3 19:11:16 TOSHIBA-User NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Oct  3 23:50:21 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  3 23:50:23 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct  3 23:50:27 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct  3 23:50:38 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct  3 23:50:50 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct  3 23:50:54 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  3 23:56:37 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct  3 23:56:45 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct  3 23:56:56 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct  3 23:57:08 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  4 00:01:32 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct  4 00:01:40 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct  4 00:01:48 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct  4 00:02:03 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  4 00:07:58 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct  4 00:08:02 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct  4 00:08:13 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct  4 00:08:24 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct  4 00:08:29 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  4 00:11:54 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct  4 00:11:58 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct  4 00:12:07 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct  4 00:12:25 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  4 00:13:35 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  4 00:13:37 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct  4 00:13:42 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct  4 00:13:48 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct  4 00:13:57 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct  4 00:14:08 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  4 00:17:02 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct  4 00:17:10 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct  4 00:17:19 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct  4 00:17:30 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct  4 00:17:33 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  4 00:24:53 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct  4 00:25:01 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct  4 00:25:20 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct  4 00:25:23 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  4 00:27:15 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  4 00:27:16 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct  4 00:27:22 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct  4 00:27:33 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct  4 00:27:43 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct  4 00:27:47 TOSHIBA-User dhclient: No DHCPOFFERS received.
Oct  4 00:28:42 TOSHIBA-User dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct  4 00:28:46 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct  4 00:28:49 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct  4 00:28:56 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct  4 00:29:07 TOSHIBA-User dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct  4 00:29:17 TOSHIBA-User dhclient: No DHCPOFFERS received.


```I'm not positive, but it looks like there are a couple of bits in the middle where something interesting happened.  Apparently this AP has a static IP address, though, and doesn't support DHCP.  Any joy?

---

### Post by freechiru on 2009-10-04
I don't think I do have the latest Madwifi installed -- the version I had was -0.9.4, whereas all the supposed solutions I have found (e.g. [http://ubuntuforums.org/showthread.php?t=902860&highlight=toshiba+nb100](http://ubuntuforums.org/showthread.php?t=902860&highlight=toshiba+nb100) ) have used -hal-0.10.5.6  I've been trying to follow the solution in that link above (thereasoner's one) to download that version of Madwifi, but when I try the line:

```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
```

I get:

```
svn: PROPFIND request failed on '/madwifi/branches/madwifi-hal-0.10.5.6'
svn: PROPFIND of '/madwifi/branches/madwifi-hal-0.10.5.6': could not connect to server (https://svn.madwifi.org)

```

Presumably the server information is out of date.  I'm going to try and download a copy of the file through my browser from the Madwifi website, but I'm not sure I'll recognise the right one.  I don't understand what this "subversion" thing is.

---

### Post by freechiru on 2009-10-04
Problem partly solved -- found new address for the subversion repository at [http://madwifi-project.org/wiki/news/20090528/subversion-repository-moved](http://madwifi-project.org/wiki/news/20090528/subversion-repository-moved) .  Continuing with thereasoner's how-to.

---

### Post by freechiru on 2009-10-04
Result: downloading Madwifi-hal-0.10.5.6 has absolutely no effect -- same problem as before, I can see the networks, I can even try to connect to them, but for some reason the connection simply won't go through.

I'm going to search and see whether any of the solutions suggest anything other than simply downloading this version of Madwifi.

---

### Post by freechiru on 2009-10-04
A couple of people have suggested that they had no problems with the wireless card being supported in 9.04, so I'm going to try upgrading to that and see if it works.  Might as well.

---

### Post by t0mppa on 2009-10-05
> **freechiru said:**
> I'm not positive, but it looks like there are a couple of bits in the middle where something interesting happened.  Apparently this AP has a static IP address, though, and doesn't support DHCP.  Any joy?

Those bits in the middle were your wired connection and it worked perfectly well. If you still have this same issue after updating to Jaunty (9.04), then should probably widen the search a bit and try **less /var/log/syslog | grep -e dhclient -e NetworkManager -e wlan0**

In theory the wireless first connects to the AP, then authenticates itself and only if both worked, then tries to do the DHCP handshake, but I never tested, if this is all automated in Linux, so that it does all three steps anyway, even if either of the first two fails.

---

### Post by EJeanmaire on 2009-10-05
> **freechiru said:**
> A couple of people have suggested that they had no problems with the wireless card being supported in 9.04, so I'm going to try upgrading to that and see if it works.  Might as well.

I was having trouble with Atheros 5008 (slow, intermittent internet).  I decided to updgrade the kernel as a shot in the dark to the latest 2.6.31.1 and it has much better Atheros driver support (the opensource drivers re greatly improved), and no issues now.  If you can compile a new kernel I would recommend giving it a shot, it shouldn't take too much effort if you follow the Master Kernel thread (search for it).

---

### Post by freechiru on 2009-10-05
Thanks for both your suggestions.  I had trouble upgrading to 9.04 for some reason, so I'm probably going to wait until 9.10 is fully released and then just work from that.  Although I may well try upgrading the kernel first and see what that does.  We're getting somewhere...  XD

---

