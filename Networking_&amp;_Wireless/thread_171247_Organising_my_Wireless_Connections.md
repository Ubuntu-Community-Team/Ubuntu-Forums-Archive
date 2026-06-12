---
title: "Organising my Wireless Connections"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by Aramis on 2006-05-06
Hi y'all,

Thanks to the HOWTO: WPA on Ubuntu 5.10 (Breezy Badger) , I now have wireless connection on my laptop YEAH. Unfortunately, it is a bit of a mess. I use ndiswrapper in order to use my PCMCIA card, and I have configured the wpasupplicant.

However, when I do
```

sudo sudo invoke-rc.d wpasupplicant start
ok
sudo invoke-rc.d networking restart
ok

```
my wireless card "link" goes green, I have OSI model layer 2 activated. cool ...
Unfortunately, the card does not start a DHCP request :(
I have to do the following
```

sudo dhclient wlan0

```
It works GREAT...

now, for a n00b like myself spending 90 minutes configuring a network card is far from the idea of fun. In addition, I am planning to use this wireless enabled laptop both at home and at work.

My questions are thus as follows:
* When I invole wpasupplicant how can I determine the file(s) that this process reads in. I would like to create wpa* files that would reflect their purpose. For instance wpa_home and wpahome.conf would be the files to use at home, same for work :mrgreen: 
* is there a tool out there that allows organising Wireless Connections by SSID/configuration details
* if not, is there a resource that could teach me how to write a shell script that would iterates throught the necessary commands in order to connect to a network, and possibly adapt to have a choice between available network.

Please note that my home and work network require WPA-PSK or LEAP/PEAP therefore I think the setup is far from being easy... Well; I guess I would not be asking for help otherwise :oops:  In addition, I have not setup my operating system in such way that wpasupplicant is started at boot time. Indeed, I want to be sure that my wireless connections work fine first...

Thanks to future helpers

PS: I apologise for the poor redaction of this message but I am WAY behind schedule for house keeping duties... so I am in a hurry - cheers :wink:

---

### Post by Aramis on 2006-05-06
I am back :!: But I think I have messed up something badly. When I posted the message above I was first connected to my router via cat5 cable, then literaly *fiddled* my way through the configuration of ndiswrapper WPA and the rest of it. After that I switched off the computer, move it somewhere nicer where Wireless is a must have... yeah you guessed it ! it does not quite work :(

On my first try I have noticed that the card was *ra0* as opposed to *wlan0* I have minutes before. I tried my best my probing in order for ndiswrapper utils to pick up the device. I stop/started networking and wpasupplicant as well as editing the associated config file ... but I did not avail . I swithed off the computer again.

Second try, well the applet for the wireless network appeared on my desktop much to my surprise :confused: The applet informed me that the wireless card was not configured properly. I started the ndiswrapper utils: NO CARD. Gah! Unplug the card and plug back in. Prob... nothing. Again Nothing.. after 3 or so trial the utility shows that I now have a card name... **wlan0**. Ok... I stopped *networking* and *wpasupplicant*. I edit the CONF file. Go through the steps I describe in the post above and OH ! it works. Indeed, this very message is being typed from quite a distance from the Router :mrgreen: and Wireless :wink:

Nevertheless, I don't have the first clue about why the card is not detected at system boot (it was plugged in before I switched the computer on), nor do I understand why I have the **SIOCGIFFLAGS** error when I arrive at the desktop. So, please please please tell how I can make this configuration easier to use (cf. original question). I posted this message as a complement to the above just in case it shows that there are issues with my computer.

Ar@mi$

---

