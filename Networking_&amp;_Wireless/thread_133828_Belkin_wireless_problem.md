---
title: "Belkin wireless problem"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by jrwitt on 2006-02-20
I just installed Ubuntu about an hour ago on an HP laptop. It is set up as dual boot with Windows XP. This is my first attempt at Linux. The dual boot is working fine as far as I can tell. I am posting this via Windows. 

The problem is ... Ubuntu does not see the Belkin Pre-N wireless card. I haven't a clue where to go from here.

I am looking for a web site that has instructions on how to set up wireless cards in Linux. Is there such a site? Any other suggestions?

Any help appreciated. 

Jack

---

### Post by Lambert on 2006-02-20
Welcome to ubuntu and linux :)

Depending on who's pre-n chipset is in the device, it might not work in linux as there are no drivers for pre-n devices.

There is an app called ndiswrapper which uses the windows drivers in linux. Breezy comes with 1.1 installed (you have to install ndsiwrapper-utils to get it to work though) but 1.1 doesn't support any pre-n chipsets

Recently v 1.9 and shortly after 1.10 versions were released. In version 1.9 they added support for the airgo chipset. 

So you will need to compile and install the latest ndiswrapper version. See this page for help. It should have everything you need, if not there are links to the ndiswrapper wiki support site for more help.

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper")

Of course I will say if this is your first shot at linux, this can be confusing and a task only because of poor driver support from vendors, not linux's fault. Take your time, keep track/document everything you do and of course come back here for any help and someone will try to help you. Maybe someone else here has a working pre-n card but I haven't seen it yet her in this forum.

I would also suggest contacting the manufacture of the device and ask them about linux driver support. Airgo supposedly said they would release a linux driver but I haven't seen it yet.

---

