---
title: "internet over firewire"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by anatra on 2009-12-05
Hi everyone

I had an old Apple eMac which i didn't use for anything, so i decided to install Ubuntu, which is running well.

My problem is: I'd like to have Internet access on my old eMac AND my new iMac. The iMac is connected to the Internet over Ethernet and I'd like to share this connection with my Ubuntu machine. That's pretty much the only way - the eMac doesn't have WiFi and there's only one Ethernet cable available in my room.

So far, I have successfully set up a network connection between the two over FireWire.

The iMac is running Mac OS X's "Internet sharing" which basically means it acts like a virtual router - it provides its Internet connection through FireWire. Since I can access the iMac from my Ubuntu machine (eg. through SSH), it should be possible to establish an Internet connection.

**Has anybody got an idea how to convince the NetworkManager to use the FireWire connection instead of the Ethernet connection?** It only seems to recognize the Ethernet connection, ignoring the FW one, competely refusing to to anything if there's no Ethernet cable plugged in.

***EDIT: Ok, I got the whole thing working, very nice **(Not working after system restart, doing a bit of trial and error now... Alright, I can get it to work, but only sometimes; it seems I first have to have a connection over Ethernet, then unplug it - very confusing - still trying)**. I remembered that most of Mac OS X's network services run with Bonjour ([http://developer.apple.com/networking/bonjour/faq.html](http://developer.apple.com/networking/bonjour/faq.html))

Google then provided me with a Bonjour solution for Ubuntu ([http://blog.gotchi.at/2006/03/06/Rendezvous-oder-Bonjour-unter-Ubuntu/](http://blog.gotchi.at/2006/03/06/Rendezvous-oder-Bonjour-unter-Ubuntu/))

Yes, it's written in German; what you need to know is the command to install it.

```

sudo aptitude install avahi-daemon avahi-discover avahi-dnsconfd avahi-utils
```I now have working Internet (over FireWire!) and lots of other stuff, eg. file sharing.

So for all those (well, I don't think anybody will ever use this but me, but who cares) who'd like to do this:

1. Load FireWire support: ```
sudo modprobe eth1394
```2. Check network device number: ```
ifconfig -a
``` (I'll be referring to your respective device with *eth#*)
3. Configure IPs: ```
sudo ifconfig eth# <CUSTOM IP> netmask <CUSTOM NETMASK> up
```4. Configure your FireWire under Mac OS X manually to have the same netmask.
5. Install AVAHI

---

### Post by anatra on 2009-12-06
*bump*

---

### Post by anatra on 2009-12-06
*bump*

---

### Post by anatra on 2009-12-07
Nobody has got any ideas at all?

Little more information: My FireWire connection is set up as eth0, the Ethernet as eth1.

**So what I'd need to do is get NetworkManager to build up a connection over eth0 instead of eth1**, but I guess it's not as simple as it sounds :rolleyes:

---

### Post by teward on 2009-12-07
I'm not certain that you can.  According to Cisco Corporation's Networking Academy, they run on completely different protocols.  If I may ask, where did you get the idea of getting internet via firewire?

---

### Post by anatra on 2009-12-07
> **TrekCaptainUSA said:**
> I'm not certain that you can.  According to Cisco Corporation's Networking Academy, they run on completely different protocols.  If I may ask, where did you get the idea of getting internet via firewire?

Well, as I said, i have two Mac machines. My now-Ubuntu machine once had Mac OS X installed. Back then, I activated Internet sharing over FireWire on my new iMac, which basically turns it into a router with a FireWire cable. This was the only way I could get Internet on both machines.

It's not my idea, really, but I still like it :D

---

### Post by teward on 2009-12-07
Well, just like I compare Windows and Ubuntu, I'm going to compare Mac OS to Ubuntu:

**Mac OS and Ubuntu are different.  They may be *similar*, but they don't have the same functionality.**

I'm guessing (maybe) that Ubuntu doesn't like the idea of firewire = internet connection.  How's your other computer hooked up to the internet, may I ask?

***EDIT: If all you want to do is disable one of the eth entries in the system, do this in the Terminal on Ubuntu:

```
sudo ifconfig eth# down
```
where the # is the interface number.  This makes the system think its disabled.  You'll have to do this at every startup though.

---

### Post by anatra on 2009-12-07
> **TrekCaptainUSA said:**
> Well, just like I compare Windows and Ubuntu, I'm going to compare Mac OS to Ubuntu:

**Mac OS and Ubuntu are different.  They may be *similar*, but they don't have the same functionality.**

I'm guessing (maybe) that Ubuntu doesn't like the idea of firewire = internet connection.  How's your other computer hooked up to the internet, may I ask?


Cable Internet modem -> router ----(Ethernet cable)---->my iMac-----(FireWire cable)---->Ubuntu machine

The thing is, though, that Ubuntu accepts the FireWire connection as a network connection; I can ping my iMacs IP address.

> ***EDIT: If all you want to do is disable one of the eth entries in the system, do this in the Terminal on Ubuntu:

```
sudo ifconfig eth# down
```where the # is the interface number. This makes the system think its disabled. You'll have to do this at every startup though.I'll try that.

***EDIT: Didn't work. It just disables eth1, NetworkManager doesn't switch to eth0.

***EDIT2: Works! See post 1

---

### Post by teward on 2009-12-07
> **anatra said:**
> ***EDIT: Didn't work. It just disables eth1, NetworkManager doesn't switch to eth0.

***EDIT2: Works! See post 1

If that doesn't work, then just edit your connections under Network Manager (right click the network manager icon, edit connections (wired), only list the ethernet for your Mac.

I didn't see your "EDIT2".  Did it work or not?  Because the "EDIT2" shows up in the quote, but not on the page.

**EDIT: It shows up now :P ***

---

