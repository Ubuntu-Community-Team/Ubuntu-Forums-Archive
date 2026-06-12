---
title: "guru, link aggregation need failover to wlan0 using mode=4 gbit+ethernet&amp;router $incl"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by swimfish on 2010-11-06
if you can solve my problem its worth $7.50 to me paypal verified.  thank you

i was hoping you all could assist me.  i'm using link aggregation under ubuntu.  it works great.  this is my /etc/network/interfaces file [http://pastebin.com/2f8XnJmR](http://pastebin.com/2f8XnJmR)  what i would like to do is keep mode=4 which i believe is fastest and try to implement the features of lagg -- link aggregation and failover interface for connecting wireless should bond0 be broken.  

[http://manpages.ubuntu.com/manpages/maverick/man4/trunk.4freebsd.html]("http://manpages.ubuntu.com/manpages/maverick/man4/trunk.4freebsd.html")[http://manpages.ubuntu.com/manpages/maverick/man4/trunk.4freebsd.html](http://manpages.ubuntu.com/manpages/maverick/man4/trunk.4freebsd.html)


eg. i would like to switch over to wlan0 if bond0 is ever broken due to cable disconnect. that seems to be the only time bond0 gets broken for me, is a disconnect while in use, and recovering from that, is somewhat daunting.   

i would also like to know if there is anything faster than mode 4 that your standard realtek gigabit ethernet ports can handle, perhaps additional packages or configuration.  

i have minimal ifconfig/iwconfig wlan0 skills if any.  though i can google things myself.  to make things simple, if you could adjust my interfaces file to suit this purpose assume my SSID is HotelCali  using WPA2 Personal AES and key is "AppliedPhysics0928"

i also am wondering if miimon could equal 1000 for gigabit router and dual gigabit ethernet, or any other relevant settings could be tweaked.

this is my /etc/modules

[http://pastebin.com/cSFn58PE](http://pastebin.com/cSFn58PE)

this is what i used to choose my options and get up and running for those new to link aggregation.  [https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation)

the ubuntu channel bonding documentation for some reason never works out.  never establishes a working internet connection.  

thank you

---

