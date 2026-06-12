---
title: "Share 3G over WIFI"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by lancest on 2009-11-04
9.10
I'm trying to find the right way to share my 3G connection over WIFI or Ethernet. Anybody know?

---

### Post by puppywhacker on 2009-11-04
It's the same as any other sharing, enable ip forwarding and setup a NAT masquerade in iptables for the external interface (probably ppp0)

```
sysctl -w net.ipv4.conf.all.forwarding=1
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables-save

```

---

### Post by lancest on 2009-11-12
Thanks, I'm on this. Looks simple.

---

### Post by Nerd King on 2009-12-06
Would it be possible to have a line-by-line explanation of what each bit is doing? I need this but I also want to understand it, rather than blindly typing stuff into the terminal!

---

### Post by jaxxed on 2010-04-09
# turn on routing for standard ipv traffic (enable it at the system level)
#EDIT (to further explain) - routing means passing packets between interfaces, so applying routing rules to incoming packets as well as outgoing.)
sysctl -w net.ipv4.conf.all.forwarding=1

# add a firewall rule, to pass traffic going out on the ppp0 interface (the 3g modem), NAT tabling the packets, masquerading on behalf of the sources.  (this is complicated, and you should read an iptables tutorial, or a routing tutorial)
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

# commit the changes to the iptables rules queue
iptables-save

---

### Post by adi p on 2010-08-27
How do you create a WiFi net that you can join afterwards, like, say, from an iPhone?

And also, how do you set up that wi-fi so that it gives an IP address automatically to a device that connects to it?

---

### Post by 905jay on 2011-06-08
*BUMP*

I have a similar question if anyone may have a solution. 

I am in Canada with a Wind 3G Data Stick and want to share it's internet connection via my laptops wlan0 interface to my various Andriod devices. I can buy a hardware dock-style router for it for $80 but would rather use my Ubuntu laptop as the dock needs a constant AC power supply.

Ubuntu 11.04
3G Data stick Interface: ppp0 
     IP: 10.x.x.x
Laptop WLAN card = wlan0

A guide would be awesome and greatly appreciated! Thanks in advance!

---

### Post by Plumtreed on 2011-06-08
If you set up an 'Ad-Hoc' connection on your lap-top you create a Wifi network or 'hot-spot' that can be accessed by any device capable of doing so. It would be essential to set up WEP protection, at least, and use the password to access the connection.

Have you tried this?

---

### Post by lancest on 2011-06-09
> **Plumtreed said:**
> If you set up an 'Ad-Hoc' connection on your lap-top you create a Wifi network or 'hot-spot' that can be accessed by any device capable of doing so. It would be essential to set up WEP protection, at least, and use the password to access the connection.

Have you tried this?

Renewed interest with new tablet.
Yes I have tried this several times by NM GUI to share 3G. 
On two different laptops and one Android tablet that I own. 
 Network Man setup was easy , but unable to view (Droid) or connect (PC's) to new Ad-Hoc network on devices.
No success with this
: [http://www.sailsarana.com/share_3G_data_internet_over_wifi.php](http://www.sailsarana.com/share_3G_data_internet_over_wifi.php)

This made me hopeful but is the same failed method:
[http://www.greenhughes.com/content/how-turn-your-netbook-3g-mobile-broadband-wifi-hotspot](http://www.greenhughes.com/content/how-turn-your-netbook-3g-mobile-broadband-wifi-hotspot).

I wonder if having the right WIFI chip would allow me to *actually function* in Master mode?  Is Network Manager fooling me?  Seems really flakey. 

Any help would be appreciated

---

### Post by Plumtreed on 2011-06-13
I have re-visited my earlier successful installs and found that AD-Hoc is no longer the simple process it used to be. 

I wonder if we have lost some functionality by keeping up to date with upgrades.

PS have been able to connect via WEP or nil encryption only

---

### Post by Plumtreed on 2011-06-13
@lancest......I was actually replying to previous post but I see that you are OP.

I have AD-Hoc setup via NetworkManager GUI and it has worked OTB but recently 1 netbook fails to connect. That netbook has been upgraded but when it is loaded with LiveCD 10.04 it finds and connects successfully. The 'master' laptop is running 10.10 upgraded.

I have restored the netbook so that the install doesn't include recent upgrades and it connects the way it should.

I don't know any 'tricks' to make it work but I recall struggling to get WPA to work but abandoned that for WEP which is a minimum.

---

### Post by macflav on 2011-06-30
> **905jay said:**
> *BUMP*

I have a similar question if anyone may have a solution. 

I am in Canada with a Wind 3G Data Stick and want to share it's internet connection via my laptops wlan0 interface to my various Andriod devices. I can buy a hardware dock-style router for it for $80 but would rather use my Ubuntu laptop as the dock needs a constant AC power supply.

Ubuntu 11.04
3G Data stick Interface: ppp0 
     IP: 10.x.x.x
Laptop WLAN card = wlan0

A guide would be awesome and greatly appreciated! Thanks in advance!

For some very strange reason, Android doesn't support connections to ad hoc networks. See this: [http://code.google.com/p/android/issues/detail?id=82](http://code.google.com/p/android/issues/detail?id=82)

---

### Post by lancest on 2011-06-30
Gave up on Ad-Hoc, I think the three WIFI chips I own are not compatible.

Bought a 3G router, works great with Ubuntu PC's, but Android won't allow me to VPN on it.

So I'm working on that now. May require custom solution.

---

### Post by forgewire on 2011-09-25
I've tried everything from all these methods to share 3G over wifi:
[http://www.google.ie/search?sclient=psy-ab&hl=en&rlz=1G1GGLQ_ENIE267&source=hp&q=how+to+share+3g+connection+over+wifi+ubuntu&btnG=Search#q=how+to+share+3g+connection+over+wifi+ubuntu&hl=en&tbo=1&rlz=1G1GGLQ_ENIE267&output=search&source=lnt&tbs=qdr:y&sa=X&ei=8819TrWVPPO00QXl-pnoDw&ved=0CAsQpwUoBQ&fp=1&biw=1128&bih=473&bav=on.2,or.r_gc.r_pw.&cad=b](http://www.google.ie/search?sclient=psy-ab&hl=en&rlz=1G1GGLQ_ENIE267&source=hp&q=how+to+share+3g+connection+over+wifi+ubuntu&btnG=Search#q=how+to+share+3g+connection+over+wifi+ubuntu&hl=en&tbo=1&rlz=1G1GGLQ_ENIE267&output=search&source=lnt&tbs=qdr:y&sa=X&ei=8819TrWVPPO00QXl-pnoDw&ved=0CAsQpwUoBQ&fp=1&biw=1128&bih=473&bav=on.2,or.r_gc.r_pw.&cad=b)
with ad-hoc or master mode without any success. When client connects it has no access to the Internet.
I've tried GUI and CLI, firestarter and ip tables to route and share the traffic with DNS and manual setup but nothing works. I'm using Mint 11

---

### Post by Mitchbw on 2011-10-17
> **puppywhacker said:**
> It's the same as any other sharing, enable ip forwarding and setup a NAT masquerade in iptables for the external interface (probably ppp0)

```
sysctl -w net.ipv4.conf.all.forwarding=1
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables-save

```

@[puppywhacker]("http://ubuntuforums.org/member.php?u=644991") you da man! :KS

Connected my USB 3g modem (E160G, APN=3intnernet, location = uk) copied your code into an Admin terminal, pressed enter, no errors.

Created 'New Wireless Network' with wep with 128-passphrase

On other computer, 'Connect to Hidden Wireless Network', entered the credentials and Boom connected and worked :p

P.S. works well with Linux Mint DE! (installed Mint Debian - 20111001 to  a USB drive to minimize hardware usage)

---

