---
title: "Issues with xfinity wireless"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by seuzy13 on 2012-05-29
Hello!

I recently had Comcast internet installed in my apartment, and they hooked up an xfinity wireless router for me. Everything seems to work fine, except for when it comes to wireless on my ubuntu laptop. My Windows laptop does not experience any problems as far as I can tell. Also, wired access on my ubuntu laptop works fine.

Here's what happens:
Sometimes I can load web pages no problem. Other times, the network decides it doesn't know where anything is, and I get those "server not found" errors when trying to visit webpages despite still being connected to the network. This lasts for about five minutes or so, and then everything will spontaneously work for another few minutes, and then spontaneously stop working... Basically, it's hit or miss.

I've had some issues with the wireless card on this laptop before on a different network, but they were of a different nature, and I don't believe they are related. It should be noted that this laptop works fine on most networks.

I'm using Ubuntu 12.04 on a Thinkpad T420. My wireless card is RealTek RTL8188CE. Please ask for any other information that you may need to diagnose this problem.

Thanks, everyone! ;)

---

### Post by seuzy13 on 2012-05-30
Weird. The wired internet appears to be experiencing similar problems. Instead of occasionally deciding the Internet doesn't exist, it occasionally decides certain websites don't exist and is just as flaky as the wireless it seems.

---

### Post by hghpandaman on 2012-06-03
Hey everyone if anyone knows a way to fix this it would be very helpful. I have the same problem. I've narrowed it down to the wireless xfinity router comcast set up because I've used my laptop at a few different places and wireless works fine, but at home its so sporadic i cant even install Blender, or Gimp from the ubuntu software center because the internet keeps dropping out. I'm using a Toshiba Satellite L755 and am very new to Ubuntu.
Thanks!!!

---

### Post by seuzy13 on 2012-06-03
Oh, hey. Forgot I posted this problem here as well. I had a [thread]("http://forums.comcast.com/t5/Home-Networking-and-Router-Help/Problems-Connecting-on-Ubuntu/td-p/1297015") going in the comcast forums for a while.

Basically, the solution I found was to add the following lines to my /etc/resolvconf/resolv.conf.d/head file:
nameserver 8.8.8.8
nameserver 8.8.4.4

This tells the computer to look at the Google DNS servers, as apparently it was having problems with the comcast ones that were automatically written to /etc/resolv.conf. I don't really know why.

This may not be an elegant fix, as it was only the one I stumbled upon. Let me know if this works for you!

---

### Post by jfand72 on 2012-07-01
Same problem. For me, internet navigation begins with no problem. After a few minutes my laptop do not recognizes my wifi. I'm in Mexico and obviously I have another cable carrier. 
It be very helpful is someone has a solution for that

---

### Post by kurt18947 on 2012-07-01
It might be worthwhile for those having problems with RealTek 8188xxx WiFi adapters to try RealTek's drivers.  I have a RealTek 8188Cus adapter(tiny USB) and it's recognized by native drivers but doesn't connect.  It keeeps coming back to "enter the network password" page.  I downloaded RealTek's drivers - they include install scripts - and am in business.  That tiny adapter works really well.  I did have to blacklist the 'native' drivers on some installs but not on Ubuntu 12.04.  I *did* have to blacklist on Mint 13 which is based on 12.04, who knows why.  Do keep RealTek's drivers/install script where you can find them.  You have to rerun the script after kernel upgrades.

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

---

### Post by mattsvensson on 2012-07-13
I had connectivity issues as well and was able to finally narrow it down (with help from other forums) to adding the below entries to the below two files. Looks like Ubuntu was trying to resolve the DNS servers and having DNS resolution issues doing so (ironic, no?).

Entries to add - these are Comcast DNS servers.  no need to add the Google ones unless you want to:
nameserver 75.75.75.75
nameserver 75.75.76.76

Files to add it to:
/etc/resolv.conf
/etc/resolvconf/resolv.conf.d/head

Before there was just:
nameserver 127.0.0.1
search hsd1.ga.comcast.net

---

### Post by mongoosehuman on 2012-08-05
Thank you very much for this!  I was having the same problem for months, but your solution fixed it.

---

### Post by c. elegans on 2012-08-20
This site [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/")has what sounds like useful info.


> See specifically "I really don’t want a local resolver, how can I turn it off?"
To turn off dnsmasq in Network Manager, you need to edit /etc/NetworkManager/NetworkManager.conf and comment the “dns=dnsmasq” line (put a # in front of it) then do a “sudo restart network-manager”.

---

### Post by Easy Limits on 2012-08-20
I have found performance to be much better both wired and wireless not using Comcasts DNS servers.  I let my router handle the DNS stuff so I don't have to program each computer on my network.

I use 4.2.2.6 and 4.2.2.5

---

### Post by c_wilson on 2012-12-10
Thaaaanks all!

commenting out dnsmasq and adding nameservers (i used goog) to resolv.conf fixed the dns issues that had my walls punched full of holes

---

### Post by jdthood on 2012-12-11
> **c_wilson said:**
> commenting out dnsmasq and adding nameservers (i used goog) to resolv.conf fixed the dns issues that had my walls punched full of holes

Glad to hear it.

1. Disabling "dns=dnsmasq" in /etc/NetworkManager/NetworkManager.conf is the solution for various problems, especially this one: [https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1003842](https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1003842)

2. Malfunctioning or slow remote nameservers is another issue. In Ubuntu 12.04 and later you should not edit resolv.conf directly, and putting static addresses in /etc/resolvconf/resolv.conf.d/ files is also not ideal. If you are using NetworkManager then the correct way of overriding nameservers received via DHCP is to set "Edit Connections... | <name> | Edit... | IPv4 Settings | Method" to "Automatic (DHCP) addresses only" and enter other addresses in the "Additional DNS servers" field.

---

