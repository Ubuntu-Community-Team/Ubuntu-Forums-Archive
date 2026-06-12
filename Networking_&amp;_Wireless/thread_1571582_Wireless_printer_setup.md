---
title: "Wireless printer setup"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by dontbugmee on 2010-09-09
I bought a wireless printer Samsung ML-2525W, now I am trying to add it  as a network printer through WI-FI. Is there any way to do it if I use a  WEP network, how will printer know the key?

---

### Post by BkkBonanza on 2010-09-09
The manual is available online,

[http://downloadcenter.samsung.com/content/UM/200911/20091116163657828/EN/english/start_here.htm](http://downloadcenter.samsung.com/content/UM/200911/20091116163657828/EN/english/start_here.htm)

On Linux you would config first time via network cable. After that should be able to do change by wifi. It's a typical web control panel so you use your browser to enter various options like WEP key. (Why aren't you using WPA?)

Samsung are fairly good with Linux. I have an older model, not wireless and it works well. The web site even mentions some Linux support.

It actually supports WEP and WPA.

---

### Post by dontbugmee on 2010-09-09
[BkkBonaza]("http://ubuntuforums.org/member.php?u=550406") Thanks for the reply. So I need to connect it to router using network cable and it will assign an IP that will be used in future as printer address when I will unplug the printer? What if the router will be turned off, will the address stay the same? I use WEP because it is a WI-FI of my landlord and I have not direct access to it, only on request.

---

### Post by BkkBonanza on 2010-09-10
No. You will connect it to your network (or to your laptop diectly) with a cable just so you can access it (using a factory default address) and set some options. It tells you in the manual how to do this.

Normally you set the mode to DHCP (probably default) and the wifi "station id" (it gives you a list of wifi APs it can "see") and the WEP key (password) which you need from the router (landlord). 

After that the printer will be assigned an IP address by the router each time it powers up. Ideally the router would be configured to give it a "static lease" but that's another story.

As is always the case in a wifi network, if the wifi router is off then you cannot access the network, and hence the printer. If you don't have control over the wifi router you may prefer to just plug the printer into your USB port and use it like a normal printer.

---

