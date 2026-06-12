---
title: "No network after suspend mode."
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by lightnin on 2011-02-10
Hi all

I have never had a working suspend. But ... every year or so I try it DOH!!! to see if the updates have solved it .

Nope ! 

I used suspend mode today, and when I woke the system up , all seemed fine untill I tried to browse the internet.

It told me I was offline.  no ammount of clicking "go online" would work.

So, then I noticed the network connection was broken.

I did a few things to get connected, and I want you all to tell me what I need to put back again ! :D


IPV4 and IPV6, I unclicked the box to require this for connection to complete.

Somewhere else, there was a list of servers to ignore.  I removed them all. (I think there werre 3) one was localhost another was similar, and the third was a number.

I just want to know what these should be set at, because just because it works - doesn't make it right !

Thanks

Rich

---

### Post by lightnin on 2011-02-10
Anyone ?

---

### Post by ajgreeny on 2011-02-10
> So, then I noticed the network connection was broken.

I did a few things to get connected, and I want you all to tell me what I need to put back again ! :grin:


IPV4 and IPV6, I unclicked the box to require this for connection to complete.

Somewhere else, there was a list of servers to ignore.  I removed them  all. (I think there werre 3) one was localhost another was similar, and  the third was a number.Your explanation of what you did is not very helpful.  More information please, with details of what you did, where you changed any ipv4 and ipv6 settings, and finally, where the server list was found.

---

### Post by P4man on 2011-02-10
Used to have that issue with a VIA chipset. Only way around it was running
```

rmmod via_rhine
modprobe via_rhine
```

That obviously only works if you use via rhine network driver. If you give the output of lspci, I can give you the correct driver to unload/load.

---

### Post by lightnin on 2011-02-11
OK - thanks to all who replied.

I have retraced my steps and made notes.

This is what I did...

______________________________



Top Right, I have my connection icon.

If I right click and select EDIT CONNECTIONS

Select AUTO ETHO

Select EDIT

I have 4 tabs 
  WIRED | 802.1x Security |IPv4 Settings  | IPv6 Settings

it's the last two that I de-selected the requirement to use them.


Network Proxy Settings in System Preferences has an ignored Hosts list.

I cleared the list.


________________________


So, is this OK ?  I did it to get back online, but I didn't really know what I was doing !

Ubuntu networking has always 'just worked' before !

---

### Post by lightnin on 2011-02-12
:d

---

### Post by lightnin on 2011-02-13
So, it seems my onboard ethernet is failing :(

I spent an hour or so trying to get my connection working again thismorning.  then I tried a live cd aned it was the same, so I tried a USB to Ethernet adapter and it worked striaght away.

so, I would still like to put everything back (software settings) like it should be.

Help please :)

---

