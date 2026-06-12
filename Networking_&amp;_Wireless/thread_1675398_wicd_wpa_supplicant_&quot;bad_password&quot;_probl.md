---
title: "wicd wpa_supplicant &quot;bad password&quot; problem &amp; workaround"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by dchom on 2011-01-25
I have a "bad password" reply using wicd 1.7.0 with WPA and a preshared key within Ubuntu 10.10, i.e., I am unable to make automatic/repeatable wireless connections using wicd without a workaround.
 
I believe this may be a problem interaction between wicd and the way wpa_supllicant is passing the (preshared) key to the network authority (the router). In my case, I use a Linksys WRT54GL running DD-WRT v24-sp2 (10/10/09) std - build 13064 OpenSource firmware, configured as an Access Point in Mixed mode (b/g).
 
I have no problem authenticating WPA Personal TKIP or AES from Windows or Mac OS X clients with a variety of wireless adapters (Linksys, D-Link, Lucent, Airport (Mac)) (No intervention is required to produce the secure connections).
 
With wicd 1.7.0 and wpasupplicant 0.6.10-2 (wext as wpa_supplicant driver selected in wicd by default) on Linux 2.6.35.-24-generic (Ubuntu "Maverick Meerkat") and a Lucent Orinoco Gold 802.11b wireless adapter I am able to connect to the network initialy (one time) without the "bad password" error.
 
After the initial successful connection, reconnection is not possible (the "bad password" error) ***unless the wireless security settings on the router are re-applied. Once reapplied/resaved, a subsequent attempt to create a wireless connection from the Linux client will succeed without any changes having been made on the client side.
 
The psk data being sent to the router (with respect to the Wireless security settings) is being cached in such a way the connection is initially possible but defeats subsequent attempts at connection. Perhaps the passkey is cached/stored on the client side (after it is used to make the first connection) in such a way that it will be sent incorrectly upon subequent attempts at connection? Of course, I'm simply guessing, here ... it is by luck that I found the workaround to establish this wireless connection.
 
**********
BTW, FYI, I was unable to use the Gnome Network-Manager to establish any wireless connections at all. Thus, Network-Manager was uninstalled (sudo apt-get purge network-manager) during the installation of wicd (Ubuntu Software centre). wpa_supplicant was re-installed (Synaptic) after wicd was installed.

---

### Post by coheed on 2011-01-30
i'm having the same issues. it upgraded from 9.04 all the way to 10.04, and had some issues with "bad password" in the beginning that went away for probably 2 weeks. Randomly my linux box lost it's internet connection and I haven't been able to reconnect it yet...

I've already removed the network-manager, restarted wicd, and done everything short up downgrading wicd (not really sure how to be honest).

Nothing seems to be working right now... Any suggestions?

---

### Post by kyklops on 2011-04-26
Removing all the network-manager instances worked for me.

---

### Post by coheed on 2011-04-27
Glad you got it working! I tried every method I knew of to remove network-manager to no avail.

The only thing that worked for me was downgrading my AT&T 2wire residential gateway's wireless encryption to WPA instead of WPA2. Bummer, but it will suffice...

---

### Post by knowlittle on 2011-08-14
this works for me even though I use ubuntu 10.04
[http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/](http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/)

One minor change, after removing network manager, I have to re-install wicd and all packages relevant to it using synapstics. (they are all prepositioned with a green box).

---

### Post by dchom on 2011-08-15
Not me. The only thing that works is changing the wireless security policy on the router, from WPA Personal to WEP and saving the settings. After reverting them back to WPA Personal, the wireless connection can be made. And half the time I have to reboot the router before the wireless card can pick up the network. I know it sounds like a router problem yet my other wireless computers have absolutely no problem at any time both picking up the network and authenticating, even with the same wireless adapter.

---

### Post by northd_tech on 2011-08-26
> **knowlittle said:**
> this works for me even though I use ubuntu 10.04
[http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/](http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/)

One minor change, after removing network manager, I have to re-install wicd and all packages relevant to it using synapstics. (they are all prepositioned with a green box).
+1 (it also fixed my wireless under 64-bit Lucid Lynx 10.04.2 LTS), although I had already decided to "reinstall" all Wicd packages using Synaptic before I read your post.  I also used Wicd to apply some 'tweaks' to my DNS server settings (after verifying that these would work under Wicd using a cabled ethernet connection to get my Updates and and look up this Wicd 1.7.0/Network Manager conflict/"bug").

Here is a link to the Ubuntu Wicd packages, if anyone needs to download one/some using a different computer (or OS):

[http://packages.ubuntu.com/search?keywords=wicd](http://packages.ubuntu.com/search?keywords=wicd)

Wicd had been working fine (alongside Gnome Network Manager) for me for many months, until I ran some Updates, then I could not get wireless to connect at all.  Unfortunately, this also coincided with some DNS server "blocking" changes made by someone else to the WiFi router I had been using (without me knowing about it).  

I had also tried changing my Broadcom WiFi driver to the "open source" rather than the "proprietary STA" driver, so I likely had **at least 3 separate problems** converge when I tried to use this internet Access Point recently (and I just today figured out the problem(s)- so I had resorted to Microsoft for internet connections for a couple of weeks, and so I was CERTAIN that my password(s) were correct).

I suspect that some of the 'problem cases' above must still have some [Gnome] Network Manager components clinging on.  If it helps anyone, here is what I forced a "remove completely" using Synaptic Package Manager in order to get my Wicd 1.7.0 wireless working again (while I was cabled in using my Ethernet connection):

> **To be removed:**
  knm-runtime
  lubuntu-desktop
  network-manager-gnome
  network-manager-openconnect-gnome
  network-manager-openvpn-gnome
  network-manager-pptp-gnome
**To be completely removed (including configuration files)**
  network-manager
  network-manager-kde
  network-manager-openconnect
  network-manager-openvpn
  network-manager-pptpEDIT:  See also:
> Got bitten by this bug (bad password) after upgrading a machine from Ubuntu 9.10 to 10.04. It reinstalls network-manager.

Steps to fix in a terminal:
sudo aptitude remove network-manager
sudo /etc/init.d/wicd restart

Hit the tray icon and connect to a wpa2 network of your choice.[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070)
-----
How to fix wicd 1.7.0+ds1-5 Connection Failed: Bad Password on Ubuntu 10.10 (Maverick Merkaaat)

[http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/](http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/)
-----
Re: wicd 1.7 - wireless - Connection Failed: Bad Password

[http://ubuntuforums.org/showthread.php?t=1595106&page=2](http://ubuntuforums.org/showthread.php?t=1595106&page=2)

---

### Post by wildmanne39 on 2011-08-30
Deleted wrong place.

---

### Post by dontquoteme on 2012-04-06
> **dchom said:**
> Not me. The only thing that works is changing the wireless security policy on the router.

I've experienced this error message first hand, so know what you all mean.. it's pretty frustrating.

Normally this error means that there's a mismatch in the encryption between
* Router
* Windows PC
* Ubuntu (10.10, 11.10).

The bug seems in my experience to relate to routers using a preshared key 
Normally you'll have WPA personal, or WPA 2  - but there's a fly in the ointment and you might need a windows machine to read the encryption settings with finer detail.

Your laptops etc will connect in windows... check what encryption settings are on the windows pc that connects.
The art is to find an encryption setting that Windows, Ubuntu and your Router will all agree on. 

Sorry if this is at noddy level - I just don't want to confuse anyone.
Access your router via your firefox web browser.
type in: 192.168.1.1
Normally your router login page will appear.
Enter router password.
Check under wireless settings > Encryption.

Ubuntu encryption and Windows encryption aren't in total agreement.  This is the Eureka moment.

To prove that there is no actual problem with your router - remove encryption (very dangerous, and I'll bet you'll connect fine).  You only remove all encryption and run an open system for 2 or 3 minutes to rule out hardware issues.  Connecting with no encryption will prove that your router/network adapter are functioning - and that this is ONLY  an encryption setting issue.

Now start to align the encryption..
Your router is the king pin in all of this.  What options does it offer?  Write all the settings down, and then test out the windows settings...

(As for WEP - Please avoid as it's too weak - and can be broken in a couple of minutes).

The WPA options are where the fun starts...
Currently on 11.10 I'm using WPA2 - PSK  (on Windows it states WPA2 - PSK with AES encryption).

Then ensure that your windows/router and Ubuntu are all in agreement - and even if they are all WPA2 -PSK are they AES or TKIP?  What options does your router have?

Your router might have a checkbox (ensure backwards compatiablity - I had to tick this to make the set up work).  So it's AES (with backward compatibility on the router - or else it won't connect).

As I say, remove encryption as a test - to prove there's no hardware problems...but never consider leaving your connection open.

You will get there, but the bad password has always been for me an encryption issue... use a windows machine if you can to get more info on the exact encryption settings needed.

This might be feedback that the details about encryption in Ubuntu need to be more specific - so that users can immediately see the encryption protocol in use... ie wpa2 psk with AES or TKIP.

Hope that helps - as I've only learnt this the hard way... tinkering with encryption settings.

ps, if you get the router and ubuntu encryption aligned.. ensure those settings are available on windows... or your windows pc will be locked out.  You have to get a triangulation between the 3.

---

### Post by Wojosama on 2012-04-06
This may not help you guys but its worth a shot (follow previous advice first and momentarily disable security to ensure you can even connect in the first place). I was also unable to connect to my router using WPA2-PSK (or WPA2-Personal whatever you prefer to call it) due to a bad password error. I used the same password/router on 2 windows computers, 2 android phones, and a laptop with ubuntu 10.10. But on my main machine with ubuntu 11.10 and a new wireless card, I was unable to connect (unistalled nm, tried wicd, etc..). The solution ended up being surprisingly easy. I changed the psk on my router to one generated from:
[HTML]http://www.yellowpipe.com/yis/tools/WPA_key/generator.php[/HTML]I won't pretend to know why (read somewhere that it could help, would credit but I don't know where I read it), but it worked with the generated psk. Nothing else I did or tried had worked. It also works with network manager. Granted, I had to change the password on all my other devices/computers to the new one, but it could've been a lot worse. Hope this helps someone. It's worth a shot to try it before you spend hours messing with settings. Only takes a second to change back to the original password if it doesn't work.

Note that some characters generated may not be compatible with your router, this happened to me and I just generated a new one until there were no incompatible characters (there was no warning, when i pasted the key to the box on my router the characters just weren't there, no spaces or anything in their place, just gone). Only took 2 generations. Oh, i chose the minimum security (20 characters/160 bits) as I also have mac address filtering and am not overly paranoid, but choose whatever you are comfortable with.

---

### Post by vinaobraga on 2012-08-31
Hello Guys.

I'm trying to configure my wireless connection on my server but something weird is happening.
I have two cards on my server, one wired and another one wireless.
After set up all the setting of wpa_supplicant and execute the commands to connect, the wlan0 network get IP and connected on my AP.
But, when I log into my AP and ask to list all attached devices, I see the wlan0 card connected with the same MAC Address from the wired card. And if I unplug the network cabe from eth0, both connections goes down.

I will sent the steps that I followed with my configuration files to see if you can help me, please.

root@server:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:54:21:27:1f
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe21:271f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:106880 (106.8 KB)  TX bytes:80933 (80.9 KB)
          Interrupt:19 Base address:0x2c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1524 (1.5 KB)  TX bytes:1524 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:06:4f:70:f8:c8
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe70:f8c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19857 (19.8 KB)  TX bytes:21919 (21.9 KB)

root@server:~#

Follow the steps:

ifconfig wlan0 up
ifconfig
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -B
ifconfig
ps aux | grep [w]pa
iwconfig wlan0
dhclient wlan0

root@server:~# cat /etc/wpa_supplicant/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="AP-NOVO"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        #psk="H3l0m0t0"
        psk=11b00480d2b7b625fe893385ff627f55780afb3348f91a6685d9b5000c1fa0f9
}
root@server:~#

root@server:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#wireless
auto wlan0
iface wlan0 inet dhcp


Follow the output of the attached devices from router:

3	192.168.1.9	SERVER	00:08:54:21:27:1F
4	192.168.1.10	SERVER	00:08:54:21:27:1F

if you can see, the MAC is the same of the eth0.

What is wrong? I want to use only the wireless card..is it possible, right?

I'm running ubutu 12.04.

Thanks in advanced by any help.

---

