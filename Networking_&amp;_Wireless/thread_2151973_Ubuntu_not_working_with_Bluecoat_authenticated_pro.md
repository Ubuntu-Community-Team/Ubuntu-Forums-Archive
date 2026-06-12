---
title: "Ubuntu not working with Bluecoat authenticated proxy"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by Brattex on 2013-06-06
Hi guys

First post here; new to Ubuntu but familiar with Linux in general. Proudly South African, much like the founder of Ubuntu :)

Basic details are as follows:


[LIST]
[*]An IT department manages the corporate network here and is running Bluecoat as their proxy tool.
[*]Running any version of Windows using WPAD (auto-detect) is 100% with authenticated proxy.
[*]Running Fedora (any version up to FC18) is 100% with manually defined authenticated proxy.
[*]Ubuntu v11.04 and earlier works 100% with manually defined authenticated proxy.
[*]Ubuntu v12.10 and upwards do not work. On auto-detect they work with the internal webpages (as defined in 'bypass' mode on the proxy configuration) but the moment we set up a defined proxy and it would usually ask Bluecoat to authenticate, it just freezes and the OS becomes unusable, whether we attempt to browse internally or externally.
[*]Have tested on 64bit and 32bit machines and mixes of OSes and it is definitely not the browsers (Chrome and Firefox, any version, work on earlier versions of Ubuntu but not later versions)
[/LIST]

Is this a known bug with Ubuntu and Bluecoat? Is there some fundamental changes to the way Ubuntu does things WRT internet protocol from v11.04 to v12.10 and upwards?

The details if you need them:

[TABLE="width: 1024"]
[TR]
[TD]VM[/TD]
[TD]OS[/TD]
[TD]Ping[/TD]
[TD][/TD]
[TD]Internal[/TD]
[TD]External[/TD]
[/TR]
[TR]
[TD]x64[/TD]
[TD]13.04-desktop-i386[/TD]
[TD]replies[/TD]
[TD]defined proxy freezes OS[/TD]
[TD]works on auto, not on defined[/TD]
[TD]freezes[/TD]
[/TR]
[TR]
[TD]x64[/TD]
[TD]13.04-desktop-x64[/TD]
[TD]replies[/TD]
[TD]defined proxy freezes OS[/TD]
[TD]works on auto, not on defined[/TD]
[TD]freezes[/TD]
[/TR]
[TR]
[TD]x64[/TD]
[TD]12.10-desktop-i386[/TD]
[TD]replies[/TD]
[TD]defined proxy freezes OS[/TD]
[TD]works on auto, not on defined[/TD]
[TD]freezes[/TD]
[/TR]
[TR]
[TD]x64[/TD]
[TD]10.04.4-desktop-i386[/TD]
[TD]replies[/TD]
[TD]defined proxy works[/TD]
[TD]works[/TD]
[TD]works[/TD]
[/TR]
[TR]
[TD]x64[/TD]
[TD]11.04-desktop-i386[/TD]
[TD]replies[/TD]
[TD]defined proxy works[/TD]
[TD]works[/TD]
[TD]works[/TD]
[/TR]
[TR]
[TD]i386[/TD]
[TD]11.04-desktop-i386[/TD]
[TD]replies[/TD]
[TD]defined proxy works[/TD]
[TD]works[/TD]
[TD]works[/TD]
[/TR]
[/TABLE]

---

### Post by remy-vand on 2013-11-05
Hi, I too have this problem. I think it is a bug in debian/ubuntu.
The only browser that seems to work with the proxy on ubuntu is Opera.

I installed a fedora distribution and there all seems to work fine.

Another thing that would be nice, is to have multiple locations where you can define multiple proxies. This option was silently removed.
As a contractor, this is would be EXTREMELY handy, since I come to a lot of different sites with all there own network configurations.

---

### Post by srinivas7 on 2014-04-08
Hi I've similar problem like browser freezes under proxy settings

I solved this problem by simple steps in this [link]("http://askubuntu.com/questions/130690/isa-proxy-server")
Just add line stating your proxy ip in /etc/hosts file
E.g..,
"172.16.10.33   proxy" to /etc/hosts

---

