---
title: "Wireless says Disconnected, but it isn't."
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by Karly on 2010-10-01
I'm far to frustrated for this... 
I'm having problems with my Internet. I just recently downloaded 10.04 (went from 8.04) and now I can't get online! I could yesterday!!! I don't have access to the router, but the internet works great on all my Windows computers. On my panel it show's my wireless connection bars with an exclamation mark and says disconnected. I don't know what to do! 
If any one could help, you'd be my hero forever! I don't know what info you need from me. It's a Toshiba Satellite computer. 

Thanks!
Karly


Also, I can't update anything, or install anything because I don't have direct access to the router. I know there is a lot of information about this problem already, but everything I've seen needs me to download new drivers. If you know how to do it from one computer to another I can do that. I'm just not very techy.

---

### Post by kreggz on 2010-10-02
Maybe the password is incorrect? Try re-adding the Wireless network by right clicking on Network Manager in the top bar and going to Edit Connections.

Then go to the Wireless tab and delete the connection. Close this window, left click on network manager and try and connect again.

---

### Post by Karly on 2010-10-02
No, I can't get to the networks at all, even if it was the password. My computer itself has has a switch for the wireless and its on, but I can't see any of the wireless networks in the area. It used to ask for a "Keyring" when I logged in, but its stopped doing that (and I didn't change that setting). It's like it doesn't know I have wireless capabilities!

---

### Post by hunters1094 on 2010-10-02
> **Karly said:**
> No, I can't get to the networks at all, even if it was the password. My computer itself has has a switch for the wireless and its on, but I can't see any of the wireless networks in the area. It used to ask for a "Keyring" when I logged in, but its stopped doing that (and I didn't change that setting). It's like it doesn't know I have wireless capabilities!

did u install Wireless driver?
if not, u can use network manager to connect to the internet via wired connection. it is easy, just plug your wire. and then install the wireless driver. don not use network manager to connect via wireless. it is very bad ^^ u can try wicd.

---

### Post by Karly on 2010-10-02
> **hunters1094 said:**
> did u install Wireless driver?
if not, u can use network manager to connect to the internet via wired connection. it is easy, just plug your wire. and then install the wireless driver. don not use network manager to connect via wireless. it is very bad ^^ u can try wicd.



I don't have access to the router to plug directly into it... I live in a house that shares internet, and the people upstairs have the router and don't speak English. Do you know a way I can load the driver onto another computer and then move it to this computer? I have another computer in my house that runs on Window's it works fine.

---

### Post by hunters1094 on 2010-10-02
> **Karly said:**
> I don't have access to the router to plug directly into it... I live in a house that shares internet, and the people upstairs have the router and don't speak English. Do you know a way I can load the driver onto another computer and then move it to this computer? I have another computer in my house that runs on Window's it works fine.


in linux, u can run the command

>  lshw -C network

it will show like this:

>  *-network
       description: Wireless interface
       [COLOR=Black]product: [COLOR=Red]BCM4322[/COLOR] 802.11a/b/g/n Wireless LAN Controller[/COLOR]
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:20:15:23
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36  ip=192.168.0.27 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f1ffc000-f1ffffff

u find the driver for your wireless card, and try to install into Ubuntu laptop:)

---

### Post by Karly on 2010-10-02
> **hunters1094 said:**
> in linux, u can run the command



it will show like this:



u find the driver for your wireless card, and try to install into Ubuntu laptop:)



I can get all of that, it says I have a Atheros AR5001 Card, but I don't know how to install drivers for it. As I said, I can't use the internet from the computer that has Ubuntu (I'm using a different computer right now). I found a site [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072) , and it explains how to get drivers, but I can't even get past the first step! I put into the Terminal "sudo nano /etc/apt/sources.list" and it brings up a blank screen in Terminal with "GNU nano 2.2.2          File: /ect/apt/sources.lst" at the top and "[ New File ]" at the bottom and some other actions, but there is nothing in between. Just a blank, white space that I can type in.

---

### Post by kreggz on 2010-10-03
Maybe try using the NDISwrapper method:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

You need to get the *.inf file for your card from Windows.

If you try downloading Madwifi you have to compile it and you probably don't have all the utilities to do that at the moment.

If you still want to pursue Madwifi see this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

another suggestion is you could try a live cd of Maverick Meerkat Release Candidate. If for nothing else to have a look.

---

