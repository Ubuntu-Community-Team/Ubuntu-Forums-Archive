---
title: "Cannot get wpa working in 9.04"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by olbertc on 2009-06-26
I'm having trouble -- have been since 8.10 -- connecting to wireless networks.  I can connect to unsecured networks, but e.g. wpa gives me nothing but headaches.  I'm on a Lenovo T61p laptop.  lspci gives the following output:
-----
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
-----

Trying to connect via nm-applet, it hangs out for a while before saying that I'm disconnected.

Trying to connect via the command line, I run the following script via sudo:
-----
dhclient -r wlan0
ifconfig wlan0 down
ifconfig wlan0 up 
iwconfig wlan0 essid "network-ssid"
iwconfig wlan0 key s:network-key
iwconfig wlan0 key on
iwconfig wlan0 power off
dhclient wlan0
-----
and get the following output:
-----
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:e2:c9:a8:85
Sending on   LPF/wlan0/00:1f:e2:c9:a8:85
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
-----

dmesg -tail:
-----
[ 7727.772129] wlan0: authenticate with AP 00:1a:70:e6:d9:4a
[ 7727.972159] wlan0: authenticate with AP 00:1a:70:e6:d9:4a
[ 7728.172174] wlan0: authentication with AP 00:1a:70:e6:d9:4a timed out
[ 7740.588025] wlan0: authenticate with AP 00:1a:70:e6:d9:4a
[ 7740.593129] wlan0: authenticate with AP 00:1a:70:e6:d9:4a
[ 7740.792915] wlan0: authenticate with AP 00:1a:70:e6:d9:4a
[ 7740.992188] wlan0: authenticate with AP 00:1a:70:e6:d9:4a
[ 7741.192166] wlan0: authentication with AP 00:1a:70:e6:d9:4a timed out
[ 7872.388463] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7906.657261] ADDRCONF(NETDEV_UP): wlan0: link is not ready
-----

I've tried via wpa-supplicant with the following results (on the command line)
-----
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1a:70:e6:d9:4a (SSID='network-ssid' freq=2462 MHz)
Associated with 00:1a:70:e6:d9:4a
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
-----

I'm really at a loss.  I feel like I've tried everything, and if I can't get this working I feel like that's a deathblow to continuing to use Ubuntu.  It never worked out of the box, so please someone help! :)

Thanks!

---

### Post by carml on 2009-06-26
I solved part of my problems installing Wicd,now I don't remember how Network Manager was :D.
If you install Wicd you'll be prompeted to remove Network Manager,because there would be a conflict. :)

---

### Post by olbertc on 2009-06-26
Believe me, I've tried wicd.  It helped to get WEP validation to work, but not WPA.

---

### Post by carml on 2009-06-26
You can also save all you need to connect to a particular Wireless channel under Network,then all you need to do in order to connect to that channel is to select the right  profile under Network.
I hope this can solve your problem.

---

### Post by jimv on 2009-06-26
Meh, some hardware just doesn't have great Linux support...I ended up spending a whole $10 and buying a new card on eBay for my laptop.  Goodbye troubles.

Of course, if you don't want to spend money, you could try the 2.6.30 kernel to see if it supports your hardware any better.

---

### Post by olbertc on 2009-06-26
carml: if I could get *any* wpa network to work, that would be a useful suggestion, but until then my quest continues!

I will try the new kernel.

---

### Post by jimv on 2009-06-26
Just to tempt you ;)

[http://cgi.ebay.com/NEW-Intel-4965-4965AGN-MM2-wireless-card-802-11-AGN_W0QQitemZ350206144905QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item5189e9b189&_trksid=p3286.c0.m14&_trkparms=65%3A12|66%3A2|39%3A1|72%3A1234|240%3A1318|301%3A1|293%3A1|294%3A50](http://cgi.ebay.com/NEW-Intel-4965-4965AGN-MM2-wireless-card-802-11-AGN_W0QQitemZ350206144905QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item5189e9b189&_trksid=p3286.c0.m14&_trkparms=65%3A12|66%3A2|39%3A1|72%3A1234|240%3A1318|301%3A1|293%3A1|294%3A50)

It is the right slot for your laptop and works out of the box with Linux.

---

### Post by carml on 2009-06-26
> **olbertc said:**
> carml: if I could get *any* wpa network to work, that would be a useful suggestion, but until then my quest continues!

I will try the new kernel.

With my last suggestio AFAIK,I am able to connect to a channel that uses WPA ;)

---

### Post by Hobgoblin on 2009-06-26
> **olbertc said:**
> I'm having trouble -- have been since 8.10 -- connecting to wireless networks.  I can connect to unsecured networks, but e.g. wpa gives me nothing but headaches.  I'm on a Lenovo T61p laptop.  lspci gives the following output:


I had trouble with my IBM/Lenovo laptop with ana Atheros card when I upgraded the 8.10

I fixed it by installing linux-backports-modules-intrepid-generic then enabling the ath5k driver. (as per [this thread](http://ubuntuforums.org/showthread.php?t=1020232&highlight=backports))

Not upgraded that machine to 9.04 yet but I have other Atheros equipped machines which work fine (with a fresh install).

---

### Post by steelsparky on 2009-06-26
I had some trouble as well, I eneded up resetting my router, connecting to my unsecured wireless via cat5 and disabled wireless. Then edited WPA settings, unpluged cat5 and turned wireless back on it this worked for me.

---

### Post by olbertc on 2009-06-26
Hobgoblin: after installing the package, nothing for network drivers appears under System-Administration-Hardware drivers.  All that's there is what was already there, namely nvidia drivers.

Edit: also confirmed that wicd is a no-go.  Stalls at "validating authentication" before eventually disconnecting.  Here's the dmesg | tail:
-----
[15943.157514] ADDRCONF(NETDEV_UP): eth0: link is not ready
[15944.573063] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[15944.573072] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[15944.573549] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[15954.916064] eth0: no IPv6 routers present

---

### Post by fbugnon on 2009-06-26
ok, I know this should sound stupid, but I had great problems trying to get WPA to work in between a Gateway laptop running 9.04 and a DI-604.

The solution I found - and I have no idea whether this make sense or not, technically I mean - was choosing the right length for the password.  If I can remember, the good number of characters should be 14.

---

### Post by olbertc on 2009-06-27
OK, I had a couple(!) wireless cards in the garage.  When I put them into the laptop, no light comes on and I have no idea what to do next.  Are they even registered by the OS?  I have no idea.  I've been on google for 30 minutes trying to figure out what to do next to no avail.  Any tips, or shall I just migrate back shamefully to Windows?>

---

### Post by irv on 2009-06-27
> **olbertc said:**
> OK, I had a couple(!) wireless cards in the garage.  When I put them into the laptop, no light comes on and I have no idea what to do next.  Are they even registered by the OS?  I have no idea.  I've been on google for 30 minutes trying to figure out what to do next to no avail.  Any tips, or shall I just migrate back shamefully to Windows?>

Maybe you should start a new thread you might get more help with this problem. Also give some details on what wireless cards you tried? Any info you can give would be helpful.

---

### Post by irv on 2009-06-27
> **carml said:**
> I solved part of my problems installing Wicd,now I don't remember how Network Manager was :D.
If you install Wicd you'll be prompeted to remove Network Manager,because there would be a conflict. :)

Yes, I love wicd. I love the way it just finds any wifi when I am on the road. Ubuntu should use this for it's default Network manager instead of gnome network manager.

---

### Post by olbertc on 2009-06-27
Sorry to be a bother.  I did manage to get it working through using b43-fwcutter.  Many thanks.

---

