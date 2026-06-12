---
title: "Automated DNS Server Polling/Updating?"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by promet on 2009-10-10
Hey there,

I am on a cable modem network with RoadRunner Cable in Manhattan NYC on which I operate my machine from behind a router. It seems that domain name resolution is frequently problematic and so I manually poll and  change my Ubuntu 9.04 DNS servers to various public options from time to time.

This works pretty well as I use various web tools, i.e. dnsserverlist.com, etc. to find favorable servers at any given time, when the previous ones get annoyingly slow for my location and change them in:

Gnome-Network-Manager settings
resolv.conf
dhclient.conf

I am wondering if anyone is aware of any applications, scripts or other automated methods for going about this? 

I would love to have an automated method of polling public DNS servers, retrieving the, say, three fastest, having those appended cleanly to my system settings and throwing in a "sudo /etc/init.d/networking restart" in there for good measure.

I seem to recall Ubuntu being able to do something similar to this with the Repository sites which would auto-magically determine the fastest and update your "/etc/apt/sources.list"? At any rate...

I dream of a gnome-panel icon that I can just click which will do this for me. I am even considering undertaking this myself, but I'd love to have any thoughts or input regarding this as I am not the most cracker-jack shell-scripter or programmer to ever come down the pike.

Maybe even running my own DNS server on my box? Anyways, I just thought I'd throw it out there if anyone has any interest in discussing it.

Cheers

---

