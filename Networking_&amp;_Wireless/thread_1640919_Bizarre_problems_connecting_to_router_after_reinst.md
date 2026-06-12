---
title: "Bizarre problems connecting to router after reinstall that weren't present before."
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by ellnic on 2010-12-08
Hi All, 

I am having some bizarre problems with a 10.10 install which I am hoping someone here can give me a little input on. Due to Ubuntu being my favorite distro and it never giving me any headaches, this is my first post in 5 years of Ubuntu use!

Some background info: 

I have a laptop which I had originally put 10.10 on about 4 weeks ago. I was using the Network Manager applet to change the MAC address by entering a valid MAC in the "Cloned MAC Address" field, and then connecting to a network. This suited me fantastically as the applet applies the MAC to any interface that connects - ie. the internal Intel card or the more often used external USB RTL8187L. For reasons which would take a lot of explaining (and now kicking ones self in the head) I had to install Windoze on the machine for a week to get some specific stuff done - but have now come back to 10.10.

The problem:

So just as before, I installed 10.10, connected to my router (without changing MAC) installed system updates and other packages such as Macchanger etc and got the system working and customised how I like it. Problem is, now when I enter an address in the Cloned MAC address field and attempt to connect, the applet just sits there with the pulsing waves likes it's trying to connect but it cannot. Whilst this is happening, ifconfig -a shows that the MAC has indeed been changed. Until I remove the Cloned MAC address entry, I cannot hop on my router - or any other for that matter. Before, these steps were enough to ensure correct and functional cloning.

Things to know: This happens whether I am logged in as me or root. There is no MAC address filtering on 3 routers I have tested on (different brands). There is only MAC filtering on a 4th, and in that case, the cloned MAC is in the routers whitelist. This happens whether I specify IP details and if DHCP is used. All 3 routers without MAC control have been reset. All settings to do with wlan0/wlan1 in the network applet have been removed and re-entered. It happens on 2 different wifi cards (Intel and RTL8187L) but they worked before re-installation. I have also tried the usual commands in the terminal such as:

su
ifconfig wlan0 down
macchanger --mac (mac here) wlan0
ifconfig wlan0 up

also tried hwaddress ether 12:34:56:78:90:00 etc - The problem *doesn't* seem to be in changing the MAC, more the functionality of wlan0/wlan1 afterwards.

I have also tried (although, it worked fine without this before) adding lines to /etc/rc.local and /etc/network/interfaces. It would be worth noting that either networking was restarted or the machine was rebooted after each alteration. No avail.

I can't think of anything significantly different that I have done to this re-installation compared to the first time, so I am not sure if perhaps in the time that it took me to reinstall 10.10, a package update has come out which has altered something and it's chucking a spanner in the works. Having said that, I even reinstalled AGAIN without applying any updates and same result. I would consider myself moderately experienced with Linux - so I am pretty sure that I am not making a complete n00b mistake... this situation is just so puzzling. I have been googling for quite some time and can find others with similar problems, but no actual solution.

Any help would be very much appreciated indeed - as I have been scratching my head for about 12 hours and am about ready to get a can of petrol and some matches :( I don't care too much for other distros, so I am really set on getting this fixed.

---

### Post by ellnic on 2010-12-09
Bump. Anyone?

I have been searching again through the forums and can find some similar problems but none solved. 

This thread has the same symptoms as mine: [http://ubuntuforums.org/showthread.php?t=1539737](http://ubuntuforums.org/showthread.php?t=1539737)

"Wireless Connection never gets established, after every couple of minutes it asks me again for the key and finally gets disconnected e.g. stops trying to make a connection."

And this: [http://ubuntuforums.org/showthread.php?t=1459176](http://ubuntuforums.org/showthread.php?t=1459176)

And this too: [http://ubuntuforums.org/showthread.php?t=1165870](http://ubuntuforums.org/showthread.php?t=1165870)

This one has the same symptoms but I am not using a Broadcom: [http://ubuntuforums.org/showthread.php?t=1134853](http://ubuntuforums.org/showthread.php?t=1134853)

I have already considered this, [http://ubuntuforums.org/showthread.php?t=606939](http://ubuntuforums.org/showthread.php?t=606939) But then why did it work before re-installation? :/

Once again, any advice would be very much appreciated.

---

### Post by ellnic on 2010-12-09
Bumpety bump bump....

So should I be submitting this as a bug then or what? This is really odd. No one know what could be causing this at all? I am open to ANY suggestions.

---

### Post by ellnic on 2010-12-09
Ok - so just to see what would happen, I installed 10.04 to see if I had any luck with Spoofing the MAC addresses of either one of the wlan's. Sadly the results were the same... 

Is there anything obvious in any of the following that shouts out at anyone?

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

/etc/network/interfaces:

auto lo
iface lo inet loopback

---

ifconfig -a (working connection)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:49:6e:25
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe49:6e25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99678882 (99.6 MB)  TX bytes:4118806 (4.1 MB)


Please help me with this!! I am sorta resigned to the fact that it has to be a package or something that I have mistakenly installed, or forgot to install.... I really must get this working... Anyone? Pretty please? :)

Just grabbed this too - lshw -C network:

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:49:6e:25
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-24-generic firmware=15.32.2.9 ip=192.168.0.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:44000000-44000fff

---

### Post by ellnic on 2010-12-10
More info attached.... Info from things like dmesg, lspci, lsusb, lsmod, lshw etc.

Please help! :P

---

### Post by tredegar on 2010-12-10
If it is your router, you should easily be able to update it with your MAC, and you would have no need to spoof it.

If it is not your router, we shouldn't be helping you access it.

Please direct your neighbour's attention to [this page]("http://www.ex-parrot.com/pete/upside-down-ternet.html"), but maybe they have already taken the appropriate steps.

---

### Post by ellnic on 2010-12-10
You've obviously been stung in the past - which is why you would be suspicious of someone you don't know. 

I have legitimate reasons for spoofing a MAC address, in this case, a hardware failure. 

In any case - if I were going to use MAC address spoofing for foul means, do you think I would post my efforts on a PUBLIC forum??

Thanks for you input though.

---

### Post by bobmarley2021 on 2010-12-11
Hi ellnic. I have the same issue as you. In 10.10 I cannot spoof my MAC address and then connect to a wifi AP. It doesn't make a difference if encryption is on or not. Encryption is mostly not on as I have to use wifi in hotels and venues. Call me paranoid, but I always spoof in public places. But now I can't? I used to have suse on this laptop and it worked fine. I can't spoof from network manager or macchanger. anyone got any pointers on what could be up?

---

### Post by ellnic on 2010-12-11
@bobmarley2021 - that's odd. You got me thinking. 

You say you can't connect even when there is no encryption? I thought i'd have a play around and disable the encryption on my router temporarily. Oddly enough, I can connect after spoofing my MAC when there is no encryption at all! I then changed it to WEP and same thing! I can connect. So I changed it back to WPA and we're back in the same boat again.

So it appears to only be an issue on my end when WPA is in use, not WEP or no encryption. Are you certain that the access points you are using don't have WPA?

Maybe this is an issue with WPA supplicant? 

The router which I need to connect to is unlikely to be changed to WEP with it being so insecure - it would be easier to wait for the powers that be to add my new MAC address... our IT guys are rubbish... it'll take them days to dispatch an engineer to our office.

Anyone have any clue why WPA might be the issue and how to fix?

---

### Post by ellnic on 2010-12-12
Got it! Was having a play around with it this evening and managed to get the problem solved. 

@bobmarley2021 - if you still have issues, drop me your number in a PM and I'll give you a call and run you through it.

---

### Post by Sauce of legends on 2010-12-13
Hi ellnic    After trudging through pages of documentation over the last few days I came upon this post. I have exactly the same problem: can spoof my MAC address using either sudo ifconfig wlan0 hw ether (MAC), macchanger(which i guess does exactly the same) or the nm-applet, but can't connect to my AP. It does seem to be a problem with the way dhclient configures the IP... I would much appreciate it if you could give me some help here. Judging by the number of posts from people with similiar problems I think you would gain some popularity points by posting a solution. Alternatively you could PM me at my username...

---

### Post by Sauce of legends on 2011-01-03
Hi guys  Ok, it's been a while but I seem to have solved my problem. After mucking about with config files and dhclient for a while... I solved my problem by simply uninstalling nm-applet and replacing it with wicd . Can't say for sure what the problem was, but nm seems to screw up dhcp. I can now successfuly spoof my MAC with ifconfig and then use wicd to connect to a WPA encrypted network. Don't know if this will work for anyone else...

---

### Post by karit on 2011-01-08
Just wondering is there a bug number for this? As does seem like a regression.

---

### Post by alberto666 on 2011-05-05
I am having exactly the same problems.

No MAC address except for the original one can be spoofed.

I have an AP which I configured a long time ago with a MAC Address. As I change my laptop, I just spoofed the Mac Address to the former one.

But now... I am stuck :(

Any hint?

In Windows I got a similar problem with a different PC. I couldn't change the MAC address except for a list starting like this (it is only an example, not the real one):
34:XX:XX:XX:XX

Meaning that I could change the MAC but constrained to a MAC starting with that. I got the solution going back to an older driver of the card. So... in Linux there should be no problem in the drivers are opensource. Are they opensource?

---

### Post by alberto666 on 2011-05-05
BTW: I forgot to say that I am using Ubuntu 11.04 (the last one so far).

---

### Post by alberto666 on 2011-05-06
I have just tried with an USB Wifi Card, and the same problem.

It doesn't seem to be the card, but Ubuntu itself...

---

### Post by bobmarley2021 on 2011-10-16
The problem /IS/ with Ubuntu. You can spoof when connecting to WEP but not WPA. That is the issue. I solved the same way as others, by using wicd, but I hate it. I wish the devs would fix this issue!!!

---

