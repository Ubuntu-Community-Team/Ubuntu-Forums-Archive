---
title: "InProComm IPN2220 WiFi HOW-TO"
date: 2006-05-19
forum: Networking &amp; Wireless
---

### Post by lst1017 on 2006-05-19
InProComm IPN 2220 based WiFi Card HOW-TO

After hours of reading, searching and pounding my head against the wall, I finally got my InProComm IPN 2220 miniPCI WiFi card to work properly with ndiswrapper and Ubuntu Breezy 5.10.  Consequently, I thought I would share with the rest of the class so as to (hopefully) save someone else the level of frustration I experienced.

My particular hardware consists of a Dell Inspiron 8200 Pentium 4 1.7Ghz w/ 512Mb memory, DVD/CDRW, nVidia GeForce 440 Go, Samsung 80Gb and Maxtor 60Gb hard drives and the infamous InProComm WiFi card.  The WiFi card was added by me as an after thought.  I purchased it separately from someone on EBay and performed a self-install.  The driver CD supplied with the card was, to say the least, very outdated and contained NT, Win98 and an old 2.4 kernel driver.

Finding current drivers for this card / chipset was not easy for me.  There is no manufacturer site that I could find and native Linux drivers do not seem to exist.  Fortunately, there were a number of posts out there that pointed my to available Windows drivers.  I got my particular drivers from the Acer Euro support site ([ftp://ftp.support.acer-euro.com/notebook/aspire_1360/driver/80211g.zip)](ftp://ftp.support.acer-euro.com/notebook/aspire_1360/driver/80211g.zip)).

Initially I attempted to use the drivers shipped with the card.  Big mistake.  As it turned out, this actually caused a number of problems which prevented me from getting the system working with the updated drivers I originally acquired.  I finally learned that I had to uninstall the original (bad) drivers (ndiswrapper -e) and then REBOOT THE SYSTEM prior to installing the new drivers.  Uninstalling and immediately installing the new drivers failed miserably.

The steps that actually worked:

1.  Acquire your chosen driver set (see above for mine).  Copy the driver files from the appropriate directory of the installation media to a temporary directory in which you have read/write access (very important).  DO NOT ATTEMPT TO INSTALL FROM A CD/DVD (read-only) DIRECTORY!

Note:  I'm using the Acer Windows XP drivers.

2.  Make sure you have installed the ndiswrapper-utils package.

3.  For the command line steps, you must either become superuser (su) or use sudo to execute each step in the process.  I'm lazy and su to root.

4.  Change your current working directory to be that where you have copied the Windows driver files.

5.  Issue the following commands (Items in parens are my comments):

    modprobe ndiswrapper        (Loads ndiswrapper module)
    dmesg                       (The last line should say something similiar to "ndiswrapper version 1.1 loaded")
    ndiswrapper -i neti2220.inf (neti2220.inf is the name of my particular INF file.  YMMV)
    ndiswrapper -l              (That is lowercase 'L', not a one.  The output should be something similar to "neti2220    driver present, hardware as present".)
    ndiswrapper -m              (This adds the alias to /etc/modprobe.d/ndiswrapper)

6.  Edit /etc/modules and add "ndiswrapper" as the last line in the file (no quotes).

7.  REBOOT.   Don't ask why, just do it.

8.  Bring up the Network Configuration applet (System->Administration->Networking).  Your Wireless connection should appear in the list as WLan0 and as not configured.  Double click the connection (or alternatively, highlight and select "Properties"), select "Enable this connection" and configure according to your local network requirements.  This will put the settings in the /etc/network/interfaces file.
9.  Add the line "auto wlan0" to the end of the /etc/network/interfaces file.  This will allow your WiFi connection to start automatically at boot time.

10.  REBOOT.  Don't ask why, just do it.

11.  Enjoy.  Your WiFi connection should now work assuming you followed all of the steps to the letter.


In the event of failure to follow this process EXACTLY, issue the following:

    ndiswrapper -e neti2220

and then REBOOT and start over.

This worked for me.  I even removed and repeated the process a couple of times to make sure I had not missed anything.  Let me know if you have problems and I can try to help.


Leonard Thornton
[email]leonard@swizzlesoft.com[/email]

---

### Post by noog on 2006-05-29
root@simonslaptop:/home/simon# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
 

:-(

---

### Post by ericcmi on 2006-08-12
to the above post, just do

sudo apt-get remove ndiswrapper-utils
sudo apt-get install ndiswrapper-utils



--------------------

To the author, i get the same result using this method as all of the others. The card appears to be there in all ways, except that i get no signal whatsoever. it just will not work.

i keep getting this

```

$sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:0f:66:8f:1f:c0
Sending on   LPF/wlan0/00:0f:66:8f:1f:c0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9

```

I have a linksys WPC54G with the same chipset. the IPN2220 v01

ive tried the linksys driver as well and its just will not work. This is the fourth or fifth tutorial i have followed and still i get the same results.

I have another card that has native drivers. I popped it in, rebooted and bam, it worked as soon as I changed the encryption-key. So I know there is nothing else terrible wrong. I am also certian that this card works, it flies under xp.

any hhelp would be appreciated.

BTW its sharing IRQ11 with my eth0, is that a problem ?

---

### Post by abh83 on 2006-12-03
hey there,

i'm new to ubuntu and linux in general!

let me start off with my system specs:

Acer Aspire 1520 series (1525WLMi)
AMD Athlon 64, 3700+
InProComm IPN 2220 based WiFi Card

Now, after installing ubuntu, setting it up and following this HowTo i managed to get my Internet working. However, the link to the drivers on this page does not exist anymore so i used this link instead: [ftp://ftp.support.acer-euro.com/notebook/aspire_1360/driver](ftp://ftp.support.acer-euro.com/notebook/aspire_1360/driver)

(i assume its the same)

Anyway all seems to work fine but i keep loosing internet connection frequently and then i have to reconnect manually.

Any idea why this might be happening? Maybe there are better driver i can use? I tried the drivers cd which came with my notebook originally but they don't seem to work in linux at all!

After a while this problem started getting on my nerves real bad so i decided to reinstall the drivers using this same HowTo but now i just get the message: invalid drivers, even though i am able to install them!

Your help is greatly appreciated!

Thx
ABH

---

### Post by jokerxs on 2007-05-11
This thread is relatively old but it shows up in google so people with problems will probably check it.
So here is my experience:

I have Acer Aspire 1520 notebook and have had a simular problem with wifi connection - it used to loose/reset (or whatever) connection to AP on every 5-10min.

I solved my problem by installing the Linksys drivers instead of those provided by Acer.
It looks like the mini pcmcia wireless card Acer Aspire 1520 uses is a Linksys WPC54G V4 (version 4) - they have the same identity string when viewed with lspci.

What I did is:
- downloaded the latest Linksys WPC54G v4 driver from linksys.com (the url changes so it's no use to put it here)
- unzipped the WPC54Gv4_dr.zip
- removed the ndiswrapper kernel module - # rmmod ndiswrapper
- dropped the old driver - # ndiswrapper -e neti2220
- installed the new one -  # ndiswrapper -i WLIPNDS.INF
- load the ndiswrapper kernel module - # modprobe ndiswrapper
- up the wlan0 interface - # ifup wlan0
- voila - it works :) 

No drops 1 hour later - I'm happy :)

jokerxs
[email]joker@notany.net[/email]

---

### Post by remij on 2007-05-15
> remi@remi-laptop:~$ sudo ifup wlan0
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

I keep getting this. I followed author's guide. The only problem I got during the guide is after editing the modules file. wlan0 won't show up. 

When I type "sudo ndiswrapper -l"  I get:
neti2220 : driver installed
        device (17FE:2220) present

I have Acer Aspire 1524 (IPN 2220) my version is Ubuntu 7.04

Edit: And yes, I'm new to Linux

---

### Post by FreeJersey2007 on 2007-06-08
I'm in the EXACT same position as the last thread (same hardware, same errors).  I was about to create an identical post but just stumbled on this by chance.

So - did this ever get resolved for you?  If so, let me know.  If anyone else has thoughts, that would be great. 

I know it pretty trivial in the grand scheme of things, but I'd really like to have the wireless going too.

Thanks all!

---

### Post by bkaskar on 2007-07-11
Hi, 
Following Leonard and jokerxs' steps exactly it got the card working and recognized.

I've a Dell Dimenssion 8100 with a IPN2220 PCI card; not PCMCIA on a Laptop though. but I believe if you see your hardware with 'sudo lspci' and sudo lshw' and the card shows up as UNCLAIMED, following above instructions you'll see it in the network manager. Mine worked (as in came up as wlan0) with both ipn2220.inf and WLIPNDS.INF. 
You guys ROCK!! :guitar:

But now the problem I have is still I'm unable to connect, WPA supplicant not working, If I disable security and/or run my router in WEP, it shows some DHCPDISCOVER messages and then goes back to sleep but doesn't connect. Could someone point me to exact settings?

Till now this is what I tried - my card shows up as wlan0.
So I generated the passwd using wpa_passphrase
```

network={
        ssid="ArghNotWorking"
        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA
        key_mgmt=WPA-PSK
        psk=64bit_length_here
  }

```
I don't have a wired network card so removed the eth0, 1 and 2 and ath0 altogether... In /etc/network/interfaces now I only have lo and wlan0, and under auto wlan0 block I added the following
```

auto wlan0
iface wlan0 inet dhcp
        wpa-driver ndiswrapper
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

Then I run
```
sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dndiswrapper -w
```
I've a bit of confusion here, as somewhere I saw that this command line is being used with -Dwext and not -Dndiswrapper, why is that?

It tries to associate but fails
```
Trying to associate with 00:ff:00:1e:a7:7d (SSID='ArghNotWorking' freq=2437 MHz)
```
unable to associate 00:00:00:00:00:00 (I'll paste the exact error as I'm posting this from work)

One thing I forgot to mention, My router is running on WPA2, so should I be using this kind of a block in my wpa_supplicant.conf instead? Also do I have to modify my /etc/network/interfaces accrodingly as well? :confused: Please help.
```

#need wpa2 with tkip
network={
        pairwise=TKIP
        group=TKIP
        ssid="youressid"
        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA
        key_mgmt=WPA-PSK
        psk=f7cab7b6ecd68702dd989956568b6ecd68349343b6ecd68943b6bf95fa08079dad7
}

```

Any help will be greatly appreciated Thanks a lot
-B

---

### Post by bkaskar on 2007-08-06
^^ Any Takers? ^^

---

### Post by poscaman on 2007-09-18
when i type
 sudo ndiswrapper -l

i get
neti220 : invalid driver!
neti2220 : invalid driver!

any ideas???what is going wrong?

---

