---
title: "D-Link DSL 200 USB"
date: 2005-01-31
forum: Networking &amp; Wireless
---

### Post by Skorpius on 2005-01-31
[SIZE=3][FONT=Times New Roman]Hi!!

Anyone knows how can I configure my USB modem D-Link DSL 200 to connect to internet?
Please, don't say to me that the only way to make a simple connection is to buy an ethernet one... :-( 

Thank to all...[/FONT][/SIZE]

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=Skorpius][SIZE=3][FONT=Times New Roman]Hi!!

Anyone knows how can I configure my USB modem D-Link DSL 200 to connect to internet?
Please, don't say to me that the only way to make a simple connection is to buy an ethernet one... :-( 

Thank to all...[/FONT][/SIZE][/QUOTE]


The question is not "will the hardware work?" The question is "will I spend the time to get the hardware to work?"

Here is good tutorial here:

[http://home.pacific.net.au/~twhitema/linux_adsl.html](http://home.pacific.net.au/~twhitema/linux_adsl.html)

Only change the part about 

"You can download usermode from the eciadsl website, or just simply use this link for the rpm eciadsl-usermode-0.5-2.i586.rpm"

Instead install the debian .deb package from here:

[http://eciadsl.flashtux.org/download.php?lang=en](http://eciadsl.flashtux.org/download.php?lang=en)

Good luck!

---

### Post by ajwatts on 2006-01-21
I feel like such a dunce. :(

I'm using the latest version of Kubuntu (5.10) and need to set up my own USB D-Link DSL-200 modem - however, I am completely new to Linux in general (I have had Kubuntu installed for all of ten minutes) and don't have the faintest idea what I am doing. So when I read tutorials telling me to download and install certain files... well, I don't really know how. :P

I had the foresight to not remove Windows, so I am in there now posting this message. I don't suppose someone could give me a 'For Morons' guide on downloading and installing EciAdsl and the like, could they? As in, exactly what to type at the terminal, etc.?

It would, of course, be very helpful - and once I can get online I can actually learn what I'm doing. :)

Cheers in advance,
Adrian

---

### Post by GTvulse on 2006-01-25
[QUOTE=Skorpius]Hi!!

Anyone knows how can I configure my USB modem D-Link DSL 200 to connect to internet?
Please, don't say to me that the only way to make a simple connection is to buy an ethernet one... :-( 

Thank to all...[/QUOTE]

It depends on the type of connection used by your ISP. If your ISP uses something like VCM_RFC2364 or LLC_RFC2364, it is as simple as installing eciadsl-usermode 0.11 from the developers' website, grab the deb package and install with:
```
sudo dpkg -i eciadsl_usermode_0.11-1_i386.deb
```

**But I don't recommend you use the deb file from the flashtux site because it contains a bogus (as in not needed, superflous) dependency on rp-pppoe. **I strongly recommend you compile it yourself. Grab a copy of both the source package and the synchronization file archives from the developer's site, check the database to see what firmware file is needed for your particular aDSL bridge and:
```

sudo apt-get install build-essential
tar jxf eciadsl-usermode-0.11.tar.bz2
cd eciadsl-usermode-0.11
export PATH=/usr/sbin:"${PATH}"
./configure --prefix=/usr
make
sudo make install
sudo cp rc.adsl /etc/init.d/eciadsl
cd ..
rm -rf eciadsl-usermode-0.11
tar jxf eciadsl-synch_bin.tar.bz2
cd eciadsl-synch_bin
sudo cp the_synch_file_you_found_reported_in_the_modem_database.bin /etc/eciadsl
cd ..
rm -rf eciadsl-synch_bin
cd
sudo eciadsl-config-tk

```
Fill in with the connection data pprovided by your ISP. Basically, your username, your password and the VCI and VPI numbers. If your ISP is a known one, the latter as well as the DNS server IPs will be set up automatically when you select the ISP from the list. If not, the data has been supplied by your ISP and it is a matter of placing it in the proper boxes. *Don't use DHCP* unless your ISP told you to. Same goes for the aDSL bridge parameters when you select the proper model, if it is in the list. If for some reason the proper synch file is not selected, you can change it there too. Click save and you are done.

Now, if your ISP uses VCM_RFC2364 or LLC_RFC2364 you are basically done. Type
```
sudo eciadsl-start
``` and if the link goes up you have successfully configured your modem. Now, you need to add it to the system start up (only if you want to).

Remeber the file copied to /etc/init.d? That's a start up script. Type:
```
sudo update-rc.d eciadsl start 39 S . stop 84 0 1 .
```
To establish your connection when you boot up (even in single user mode.

If your ISP uses something more exotic, you still need to set up a PPPoE connection to actually use your network linkup.

If your ISP uses LLC_SNAP_RFC1483_BRIDGED_ETH_NO_FCS or VCM_RFC_1483_BRIDGED_ETH, type ```
sudo pppoeconf tap0
``` and follow the prompts. If you answer yes to everything, you'll end up with a PPPoE connection that start up at boot up time immediately after settiing up the link up.

If your ISP uses LLC_RFC1483_ROUTED_IP or VCM_RFC1483_ROUTED_IP, type ```
sudo pppoeconf tun0
``` instead.

BTW, Feel free to add this to the Wiki.

---

