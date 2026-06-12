---
title: "Network setup - WTF?"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by minimustangs on 2009-08-01
Look, I don't consider myself an computer idiot in the least. For the most part I'm pretty self sufficient, I guess I should be since it's what I do for a living. Ubuntu is a new beast for me. Had Fedora Core 10 working fine on my desktop, so I can appreciate the differences with Linux versions and Linux in general over M/S Os's .

Still the concept of inputting values for networking isn't any different from 1 OS to the next, so that's what I'm so exasperated with Ubuntu. I can't find the location that actually controls the network settings. Initially, the networking "worked", so having done this for the 3rd time (install Ubuntu) it's getting a bit tired. What seems to happen is this:

I can get onto the interenet via wired connection. Not sure if I'm supposed to be setting up "Wired" or "DSL" connection types, since I have a DSL via Ethernet connection it makes sense that I need both. So when I get the ethernet/DSL combination working, the next step is to disconnect from the Ethernet cable and go wireless. I can never get onto the internet in this situation, yet I can print via wireless to a wired network printer. This tells me that

- since I can get on the internet via Ethernet, that setup is correct
- since I can print to network printer while disconnected from ethernet, wireless is working.
- can't ping anything
- ifconf given me all sorts of info, but I don't seem to have the syntax right or am not getting it. The couple areas I'm concerned with don't seem to have the right values, and attempts to locate where to change them isn't helping resolve the problem.

I've been trying to get it all to come together, and the more I try differnt things the further isolated I get. Right now, I can't connect anyhow to the internet, wired, wireless, both. Either. Nothing's working.

Very frustrated. Considering going back to M/S on this laptop. At least I know that will behave in a manner I'm used to.

I'm just about to re-install Ubuntu for the 3rd or 4th time (I've lost count). I really don't wnat to HAVE to do this every time something gets mis-configured in Ubuntu.

S~

---

### Post by slakkie on 2009-08-01
man interfaces

```

       For  advice  on  configuring this package read the Network Configuration chapter of the Debian Reference manual, available at http://www.debian.org/doc/manuals/refer&#8208;
       ence/ch-gateway.en.html or in the debian-reference-en package.

       Examples of how to set up interfaces can be found in /usr/share/doc/ifupdown/examples/network-interfaces.gz.



```

No need to reinstall after such issues, Ubuntu != MS.

---

### Post by minimustangs on 2009-08-01
Sorry if I seem a bit harsh... is that link a joke?  404...

I'll take a look at the other doc in a minute, so I'm now sitting nere woth Ub.... installed for the nth time. This time I grabbed a network config tool: XFLD. 

What I find weird is that it has picked up the gateway as 66.225.160.1 and the namesrver as 209.91.128.11.


My router uses 192.168.0.1, and all the other systems are quite happy on that.

All I was really looking for as somewhere to authenticate a DSL connection, similar to WinXP's Dial up connection, which works on Xp bhoxes. I was looking for the equivalent item for Ubuntu. Save me the greif of reading all those 404 errors, please...

S~

---

### Post by slakkie on 2009-08-02
Clickedyclick [http://qref.sourceforge.net/Debian/reference/ch-gateway.en.html](http://qref.sourceforge.net/Debian/reference/ch-gateway.en.html)

And if you google for debian reference you end up here: [http://www.debian.org/doc/manuals/debian-reference/ch05.en.html](http://www.debian.org/doc/manuals/debian-reference/ch05.en.html)

Google is your friend mate.

---

### Post by minimustangs on 2009-08-02
Slakkie..Aut

thanks for putting p with my "harshness"... was a bit of a "burn the candle at both ends" kind of day yesterday. Probably should have just laid off the laptop untill today. Sorry.

In the interim, I've upgraded to 9.04. Instead of just patching patching patching, if you know what I mean.

I see the link you provided has me at the Debain docs page, thanks... going off to read that shortly.

here's what I can tell you before I sliip over there

- Networm Manager shows 3 network conenctions:
  - DSL 1 (winred)
  - Auto Eth0 (wired)
  - dlink (wireless)

I can connect to the internet using "DSL 1"
I cannot connect to the internet using "Auto Eth0"
I cannot connect to the internet using "dlink" (wireless)

I can print to LAN printer (192.168.0.4)  on DSL 1
I can print to LAN printer (192.168.0.4)  on Auto Eth0
I can print to LAN printer (192.168.0.4)  on "dlink" (wireless)

Therefor I would have to guess that one of the primary problem - the wireless card drivers working/not working is not an issue.

I'm off to read....

S~

---

### Post by slakkie on 2009-08-02
-misread-

Can you post a ifconfig -a and a netstat -rn?

---

### Post by minimustangs on 2009-08-02
> **minimustangs said:**
> Slakkie..Aut

thanks for putting p with my "harshness"... was a bit of a "burn the candle at both ends" kind of day yesterday. Probably should have just laid off the laptop untill today. Sorry.

In the interim, I've upgraded to 9.04. Instead of just patching patching patching, if you know what I mean.

I see the link you provided has me at the Debain docs page, thanks... going off to read that shortly.

here's what I can tell you before I sliip over there

- Networm Manager shows 3 network conenctions:
  - DSL 1 (winred)
  - Auto Eth0 (wired)
  - dlink (wireless)

I can connect to the internet using "DSL 1"
I cannot connect to the internet using "Auto Eth0"
I cannot connect to the internet using "dlink" (wireless)

I can print to LAN printer (192.168.0.4)  on DSL 1
I can print to LAN printer (192.168.0.4)  on Auto Eth0
I can print to LAN printer (192.168.0.4)  on "dlink" (wireless)

Therefor I would have to guess that one of the primary problem - the wireless card drivers working/not working is not an issue.

I'm off to read....

S~


UPDATE:

In order to be thorough, I was check the configuration of my network gear. At some point for some reason ( I think to make connection to the internet "manual" instead of automatic, I change the port connection from the modem to the router from WAN to LAN. No biggie there. As soon as I switched it back from LAN to WAN Ubuntu connected on Auto Eth0, and when I unplugged the cable, Wireless network was picked up... and worked! 

OK so I think "hey that's great"... and off I go. Well I just rebooted the laptop for good measure... and now i can't even find the Wireless connection. Network Manager says (under wireless0

"device not managed".

So, after a reboot I've lost the configuration that was just working flawlessly. I didn't change anything!

UPDATE#2

SO I noticed that the Preferred..."not free" drivers for the Wlan were deactivated. 
Deleted my Wlan settings. 
Enabled drivers. 
Rebooted. 

WLan now recognized, managed. I'm in the kitchen surfing - wirelessly. This is how it should be, but I still am curious why it took all this to get here, and will setings evaporate at the most innoportune time: when I'm not hope and my wife wants to use it.....

---

### Post by slakkie on 2009-08-02
If you want to spent some extra time and have it working without having to worry about networkmanagers:

[http://ubuntuforums.org/showpost.php?p=5752871&postcount=2](http://ubuntuforums.org/showpost.php?p=5752871&postcount=2)

---

### Post by Iowan on 2009-08-02
Network Manager is much better than the previous versions, but it still has a "personality". "Networm Manager" (Freudian slip?) doesn't handle interfaces set up in */etc/network/interfaces* (someone correct me if I'm wrong - again)... though there is a way to tell it to do so (but I don't have the link handy...)
I have a DSL connection, but the modem handles all the setup, so my Ubuntu box uses the "Auto eth0" to connect.

---

### Post by minimustangs on 2009-08-03
Iowan:

Well you're right on the mark with the DSL login, that was my original problem -  I couldn't locate a place/feature/app to let me "Login" to my DSL service. I had set that up on my router -  Username and  P/W but deactivated it to keep connection type to "manuall activated". I see that with our use we've got at least one computer on the web all the time, so that's pretty much a pointless excercise anyways.

Once I changed my modem / router connection over to the WAN port on the router, everthing just clicked. The only downside is that I have one important computer that I hav to remove from the network all the time to isolate it from the internet. 

So far, since my posts yesterday -  and mulitple reboots, updates, hiberation cycles, the WLAN hasn't stopped working. Seemed to settle down greatly with 9.04.

I'll take a look at the other suggestions for network interface setup mentioned above as well.

Thanks for the sounding board!!

[FONT=Arial][COLOR=Blue]Steve
Huntsville, Ontario
Canada[/COLOR][/FONT]

---

