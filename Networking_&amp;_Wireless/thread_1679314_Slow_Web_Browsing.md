---
title: "Slow Web Browsing"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by Cakebatter on 2011-01-31
I have a decent internet connection as far as down and up speeds go, above average for my location, however, when browsing the internet via Firefox or Chrome, it is taking far too long to load web pages.

I have been to several "tweak" websites for Firefox and none of the recommendations have proven to be any help.

As much as I hate to say this, the browsing speed is much faster on Windows 7 when I dual boot back to it.  Any help here would be appreciated.

[[IMG]http://www.speedtest.net/result/1136744500.png[/IMG]](http://www.speedtest.net)

specs for laptop:

Microprocessor	2.40 GHz AMD Turion II Ultra Dual-Core Mobile Processor M600
Microprocessor Cache	2MB L2 Cache
Memory	4096MB
Memory Max	8192MB
Video Graphics	ATI Mobility Radeon HD 4650 (M96)
Video Memory	Up to 2815MB (1024MB dedicated)
Hard Drive	640GB (7200RPM)
Multimedia Drive	LightScribe Blu-Ray ROM with SuperMulti DVD±R/RW Double Layer
Display	17.3&#65533;? Diagonal HD+ High-Definition HP LED BrightView Widescreen Display (1600 x 900)
Fax/Modem	High speed 56k modem
Network Card	Integrated 10/100/1000 Gigabit Ethernet LAN
Wireless Connectivity	
802.11a/b/g/n WLAN

---

### Post by nd456 on 2011-01-31
I would look into the wireless (try a wired cable to your computer)

---

### Post by Cakebatter on 2011-01-31
The problem is both wired and wireless.  Having the same problem on my desktop Ubuntu 10.10.  Went to the store and purchased a new router to rule it out, but the problem still persists which is why I am starting to think it's something in Ubuntu.  Laptop is wireless and Desktop is wired.

---

### Post by Cakebatter on 2011-01-31
fresh install of 10.10 hasn't improved the speed either. Dang!

---

### Post by nd456 on 2011-02-02
dose this happen when you try it off of a live cd?
(try Ubuntu without installing)

---

### Post by nogger on 2011-02-06
I've had this problem and I think I've solved it.

Looking at the Network Connection Information it was using my router address as the Primary DNS. So I edited the connection and under the IPv4 tab changed the method to *Automatic (DHCP) addresses* only and added my Internet provider's DNS addresses in the DNS server box.

You should be able to find the address of your DNS servers by typing  *cat /etc/resolv.conf* in a terminal.

---

### Post by arjuntank on 2011-02-06
if firefox says, "Looking for *putyourwebsite*.com.." then its a DNS problem. also, "about:config -> network.dns.disableIPv6 = true" may work. OR if that doesnt work, manually put name servers on resolv.conf or network manager, and disable dhcp. OR blacklist ipv6 module.

---

### Post by ripat on 2011-02-07
I don't think that disabling ipv6 is a good idea. The central pool of ipv4 addresses officially ran dry (one week ago) after the Internet Assigned Numbers Authority (IANA) allocated the last remaining blocks of address space.
[http://www.theregister.co.uk/2011/02/02/ipv4_exhaustion/](http://www.theregister.co.uk/2011/02/02/ipv4_exhaustion/)

But if you do, make a note to yourself of what you have done so to be able to reverse the process.

On modern linux systems (not only Ubuntu) the latest version of the glibc resolver sends two DNS request in parallel: a ipv4 (A) request and a ipv6 (Quad-A) request. This is a correct way of doing things. But some buggy ISP DNS servers or even some router devices do not respond properly and make the requests time out.

The most simple solution, as also suggested above, is to change the default DNS server in your lan's configuration. They are plenty of free and fast DNS servers around. For example Google's 8.8.8.8 and 8.8.4.4 or OpenDNS's 208.67.222.222 and 208.67.220.220. These servers respond correctly to valid ipv4+6 requests.

You can also change the DNS servers localy on your box using either the prepend option in the /etc/dhclient3/dhclient.conf file or by editing the lan connection parameters in NetworkManager.

---

