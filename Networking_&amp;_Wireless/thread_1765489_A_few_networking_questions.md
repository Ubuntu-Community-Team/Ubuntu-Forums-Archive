---
title: "A few networking questions"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by fractalman on 2011-05-23
Ok i'm running 11:04 natty, i have been having a look at kismet and aircrack just to see what they actually do and to learn how to secure my network 100% and totally lock it down.  Whilst running kismet my wifi network is showing 2 cleints, only thing is i haven't actually configured any wifi devices and there are none on the router config pages.  The only device on my router table is my pc on a wired connection,  the pc was connected at the time i ran kismet, i have only been using ubuntu for about 3 months so i'm still new to all this,  i have a few questions if anyone has a few minutes to help a noobie it would be much appreiated

Could one of the devices showing up in kismet be my pc on a wired connection?

Can someone still hack a wifi network if it doesn't actually have any wifi devices on it's config table but the wifi has been enabled - no clients at all as opposed to having clients that just aren't powered up?

What are probe networks? are they people doing the same as me and running a programme such as kismet or airodump?

If my wifi is disabled but i leave the usb adapter plugged into my pc, can that be usb adapter be hacked and entry gained to my pc? if yes, how do i secure the actual adapter to prevent this?

How can i see if anyone else is on my network?  i had a quick google and tried tcpdump which gave me this 

```
phil@JAHWEH:~$ sudo tcpdump 
[sudo] password for phil: 
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
12:09:46.538515 IP JAHWEH.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? _daap._tcp.local. (34)
12:09:46.540947 ARP, Request who-has WANConnectionDevice.home tell JAHWEH.home, length 28
12:09:46.541100 ARP, Reply WANConnectionDevice.home is-at XX:XX:XX:XX:XX:XX (oui Unknown), length 46
12:09:46.541139 IP JAHWEH.home.51061 > WANConnectionDevice.home.domain: 5323+ PTR? 251.0.0.224.in-addr.arpa. (42)
12:09:46.686091 IP WANConnectionDevice.home.domain > JAHWEH.home.51061: 5323 NXDomain 0/1/0 (100)
12:09:46.787389 IP JAHWEH.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
12:09:47.788387 IP JAHWEH.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
12:09:49.788568 IP JAHWEH.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
12:09:51.687735 IP JAHWEH.home.48458 > WANConnectionDevice.home.domain: 24174+ PTR? 10.1.168.192.in-addr.arpa. (43)
12:09:51.751715 IP WANConnectionDevice.home.domain > JAHWEH.home.48458: 24174* 1/0/0 PTR JAHWEH.home. (68)
12:09:51.752187 IP JAHWEH.home.46198 > WANConnectionDevice.home.domain: 58227+ PTR? 1.1.168.192.in-addr.arpa. (42)
12:09:51.797319 IP WANConnectionDevice.home.domain > JAHWEH.home.46198: 58227* 1/0/0 PTR WANConnectionDevice.home. (80)
12:11:23.028956 IP WANConnectionDevice.home.2056 > 239.255.255.250.1900: UDP, length 324
12:11:23.029427 IP JAHWEH.home.48804 > WANConnectionDevice.home.domain: 14955+ PTR? 250.255.255.239.in-addr.arpa. (46)
12:11:23.133078 IP WANConnectionDevice.home.2056 > 239.255.255.250.1900: UDP, length 324
12:11:23.173025 IP WANConnectionDevice.home.domain > JAHWEH.home.48804: 14955 NXDomain 0/1/0 (103)
12:11:23.237488 IP WANConnectionDevice.home.2056 > 239.255.255.250.1900: UDP, length 333
12:11:23.274148 IP JAHWEH.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
12:11:23.342939 IP WANConnectionDevice.home.2056 > 239.255.255.250.1900: UDP, length 333
12:11:23.447518 IP WANConnectionDevice.home.2056 > 239.255.255.250.1900: UDP, length 396
12:11:23.552968 IP WANConnectionDevice.home.2056 > 239.255.255.250.1900: UDP, length 396
12:11:23.658060 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 368
12:11:23.763007 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 368
12:11:23.868238 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 333
12:11:23.972983 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 333
12:11:24.077547 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 372
12:11:24.182996 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 372
12:11:24.275247 IP JAHWEH.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
12:11:24.288039 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 404
12:11:24.393045 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 404
12:11:24.498238 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 333
12:11:24.603033 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 333
12:11:24.707609 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 392
12:11:24.813095 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 392
12:11:24.918089 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 386
12:11:25.023115 IP WANConnectionDevice.home.2057 > 239.255.255.250.1900: UDP, length 386
12:11:26.275622 IP JAHWEH.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
12:11:28.040936 ARP, Request who-has WANConnectionDevice.home tell JAHWEH.home, length 28
12:11:28.041072 ARP, Reply WANConnectionDevice.home is-at XX:XX:XX:XX:XX:XX (oui Unknown), length 46


```Is this normal for a pc with a wired connection and a usb wifi adapter plugged in but the router hasn't had its wifi activated?

What does this mean? is this my pc sending a request or someone sending a request to my pc? if it's my pc why does it do this when it's sitting idle and already connected?

```
12:09:46.540947 ARP, Request who-has WANConnectionDevice.home tell JAHWEH.home, length 28
12:09:46.541100 ARP, Reply WANConnectionDevice.home is-at XX:XX:XX:XX:XX:XX (oui Unknown), length 46
```

I have googled to try and find some answers but not really had much luck so any help is much appreciated :D

thanks

---

### Post by chili555 on 2011-05-23
> Could one of the devices showing up in kismet be my pc on a wired connection?No.> Can someone still hack a wifi network if it doesn't actually have any wifi devices on it's config table but the wifi has been enabled - no clients at all as opposed to having clients that just aren't powered up?Yes, with some details. A hacker will try to get into your network by gaining an IP address from your router. It doesn't matter if you have a computer with a wireless device working or not. Think of file sharing on a network. My laptop is connected wirelessly but I can access files on my wife's computer that is hooked up wired. If a hacker gains access to your network, all the computers that are connected, wired or wireless, are vulnerable. If you are not yet using wireless on your network, disable wireless in the router. Do it now! We'll wait until you return.

All done? Good!

Kismet is not showing two clients on your router, it is showing your router and a neighbor's router. If I step out to the front porch with my laptop, I see six or eight separate networks.> What are probe networks? are they people doing the same as me and running a programme such as kismet or airodump?In Kismet, a network being probed is *your* Kismet probing everything else it sees to gain information about its security details.> If my wifi is disabled but i leave the usb adapter plugged into my pc, can that be usb adapter be hacked and entry gained to my pc? if yes, how do i secure the actual adapter to prevent this?I believe it's theoretically possible. The best defense is to simply unplug it. Of course, a hacker is unlikely to spend hours and hours and many resources to hack you and me; why not hack the bank down the street. > What does this mean? is this my pc sending a request or someone sending a request to my pc? if it's my pc why does it do this when it's sitting idle and already connected?
It all looks pretty normal. Your wireless, in either monitor or managed mode, will listen for networks. Even if it is not connected to a router, it will send a short signal and listen for a reply; more or less, "Are you there?"; "Yes, I'm here."

If you have Network Time Protocol running to keep the clock on your computer updated accurately, requests will come and go fairly frequently. Once a day, Update Manager will query the repositories to see if any updates are available. These processes go on either wired or wireless.

Now that you have disabled wireless on your router, you know that no-one is on your network except the computers that are plugged in. If you decide to use wireless, I'd use MAC filtering *and* WPA2 with a strong password. Don't use your last name or your address, don't use something likely to be in a password dictionary file, use something truly random, such as eF4Ve1$$10#bfFrD&D4 or some such. MAC filtering means only devices whose unique MAC address is on an approved list in the router can connect *AND* they have to offer the correct password in WPA2 format. Is hacking impossible? No. Is it very difficult? Yes, indeed.

---

### Post by fractalman on 2011-05-23
Thank you, much appreciated :D

---

