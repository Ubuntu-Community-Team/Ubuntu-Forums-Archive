---
title: "Hang trying to connect to router via ethernet"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by ianhaycox on 2006-07-05
Hi,

I have a dual boot Ubuntu 6.06/Windows XP box connected to my router (Wanadoo Sagem Livebox) via ethernet and I am having troubles accessing the router configuration pages via [http://192.168.1.1/](http://192.168.1.1/)

Trying both Firefox and Opera when connecting to [http://192.168.1.1/](http://192.168.1.1/) I get prompted with a dialog for the admin username/password and after OKing the dialog both browsers just sit there Loading...  No config pages are displayed. Eventually I get the Firefox error "The connection was reset
The connection to the server was reset while the page was loading."

Booting to XP and using Firefox works as expected. I.e. the router config pages are presented after entering the username/password.

I have a gut feeling it's some sort of 'firewall' issue, but I haven't installed a firewall or messed with any network settings that I'm aware of. It's a fairly vanilla Ubuntu installed from the downloaded CD. I even tried faking the browser type in Opera to IE to see if that was the problem but no joy. Searching Google didn't help.

Any help diagnosing the problem, or info on where to look would be appreciated. Still a unix newb but I'd like to migrate from Windows.

Regards,

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:AF:1D:E6
          inet addr:192.168.1.30  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:feaf:1de6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2996 errors:12 dropped:0 overruns:0 frame:12
          TX packets:2780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2810373 (2.6 MiB)  TX bytes:518209 (506.0 KiB)
          Interrupt:209 Base address:0xdead

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:369241 (360.5 KiB)  TX bytes:369241 (360.5 KiB)

---

### Post by Iowan on 2006-07-05
I'd be tempted to blame **ipv6 ** (and would probably be wrong).  There are instructions around on how-to turn off **ipv6** in Firefox (at least for Breezy).

---

### Post by ianhaycox on 2006-07-05
Turned ipv6 off in Firefox and added an entry to /etc/modprobe.d/blacklist, rebooted but no change.

Thanks for the idea.

If I can provide any more info to help then please let me know.

Thanks Ian.

---

### Post by kagashe on 2006-07-06
Once the router is configured on Windows XP it should work on Ubuntu as well. Why do you want to reconfigure it? Just click on System/Administration/Networking and see whether Ubuntu has configured it through DHCP and the device is "active" or not.

I was also facing this problem for my router (and I don't have Windows XP) for configuring first time. I removed the telephone wire from the router and switched it on. The router tried to connect and stopped (since there was no line to connect to). I could access the router by typing [http://192.168.1.1/](http://192.168.1.1/) in the browser. After configuration, I connected the telephone line and rebooted and it worked.

kagashe

---

### Post by ianhaycox on 2006-07-06
Sorry kagashe I didn't make it clear in the original post, but my Internet connection is working fine. No problems. I'm posting this from Ubuntu.

Ubuntu is DHCPed from the router and I can ping the router and surf the web etc.

The router config is OK today, but in order to complete the transition from Windows to Linux I need access to the router to change the config for general maintenance, firmware updates, opening ports, etc. etc. I didn't really want to keep a Windows installation around just to perform one infrequent task cos Ubuntu can't do it.

Any other ideas ?

---

### Post by kagashe on 2006-07-06
[QUOTE=ianhaycox]Sorry kagashe I didn't make it clear in the original post, but my Internet connection is working fine. No problems. I'm posting this from Ubuntu.

Ubuntu is DHCPed from the router and I can ping the router and surf the web etc.

The router config is OK today, but in order to complete the transition from Windows to Linux I need access to the router to change the config for general maintenance, firmware updates, opening ports, etc. etc. I didn't really want to keep a Windows installation around just to perform one infrequent task cos Ubuntu can't do it.

Any other ideas ?[/QUOTE]Ok. My router (it is of different make) was having same problem and I solved it by removing the line connection (so that the router could not connect to internet and hence not getting busy). Did you try it?

kagashe

---

### Post by ianhaycox on 2006-07-06
Just tried that and still no luck. The browser just sits there waiting.

On a hunch I also used the UserAgent Switcher of Firefox to pretend to be IE6/XP in case the router was picky about my browser, no still no.

---

