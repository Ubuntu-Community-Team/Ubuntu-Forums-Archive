---
title: "Wireless signal strength indicator"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by TiredBird on 2009-08-31
I am trying to adjust a directional antenna and need a real-time signal strength indicator. (Bar strength not fine enough - need db or % indication, preferably with a constantly updated moving graph.)

Jaunty Jackalope 9.04 with Gnome desktop

Netgear WPN111 wireless USB adapter with ndiswrapper

---

### Post by uylug on 2009-08-31
Well, you can run this command several times:

> sudo iwlist scan

---

### Post by TiredBird on 2009-09-14
> **uylug said:**
> Well, you can run this command several times:
Thanks, but thats what I've been using. I would like something that is a more real-time, such as a moving graph of signal strength. I would like to be able to be adjusting the antenna and see how it is effecting the signal at the same time.

---

### Post by JakP on 2009-09-14
Hovering pointer on wicd display in pannel gives % connection and this can be changed to -db in preferences, don't know how quickly it updates though.

---

### Post by TiredBird on 2009-09-14
> **JakP said:**
> Hovering pointer on wicd display in pannel gives % connection and this can be changed to -db in preferences, don't know how quickly it updates though.
Thanks, I've tried that too. It works, but like you, I'm not sure how often it updates. I would prefer to watch a moving graph. Some of the wardriving packeages have that capability but I can't find one that works with the Gnome desktop.

---

### Post by LAD29 on 2009-09-18
I'm looking for something like this too.  If I find something that works I'll let you know. Please do the same.

Cheers.

---

### Post by TiredBird on 2009-09-26
> **LAD29 said:**
> I'm looking for something like this too.  If I find something that works I'll let you know. Please do the same.

Cheers.

Try RutilT. 

I've been using that and although its not the moving graph I really wanted, at least it does update continuously without any input from me. 

(I do believe however that there is delay in updating. The delay could be coming from the interface though. I usually wait about 30 seconds for it to settle after making any adjustment.)

---

### Post by TiredBird on 2009-10-13
I am still looking for a solution to this. I will appreciate any suggestions offered.

---

### Post by TiredBird on 2009-10-15
bump

---

### Post by drubdrub on 2009-10-15
Howdy,

I know this is a little tangential, but you may get some alternative ideas.  [http://www.usbwifi.orconhosting.net.nz/]("http://www.usbwifi.orconhosting.net.nz/")

They use "netstumbler" which runs on Microslop, unfortunately, but certainly provides the functionality you are requesting.  Worth a look.  [http://www.netstumbler.com/]("http://www.netstumbler.com/")

BTW, the first link is a great site for ***cheap*** ways to build wireless antennas using ***cheap*** components.  If you are having signal or range problems, it has lots of DIY solutions!

All the best!

---

### Post by TiredBird on 2009-10-15
> **drubdrub said:**
> Howdy,

I know this is a little tangential, but you may get some alternative ideas.  [http://www.usbwifi.orconhosting.net.nz/]("http://www.usbwifi.orconhosting.net.nz/")

They use "netstumbler" which runs on Microslop, unfortunately, but certainly provides the functionality you are requesting.  Worth a look.  [http://www.netstumbler.com/]("http://www.netstumbler.com/")

BTW, the first link is a great site for ***cheap*** ways to build wireless antennas using ***cheap*** components.  If you are having signal or range problems, it has lots of DIY solutions!

All the best!

Thanks, but the first link you offer is the exact reason I asked the question. I have built several DIY antennas as a result of that site and now I am trying to evaluate and tune them. 

I have seen 'netstumbler'. I think I even had it installed on a Windows system I used to have. I have also seen similar programs for Kubuntu, (KDE), but I would like to have one that works on Gnome. 

Since this thread is now a month and half old, I'm about to conclude that there is no such thing.

Thanks for your post anyway.

---

### Post by tripzilch on 2011-12-04
Equipped with the **iwlist** command, I put together this not-so-little oneliner:

```
while true; do sudo iwlist **wlan2** scan | grep -B2 "**MyWirelessNetwork**" | head -n1 | python -c "ss=int(raw_input().split('=')[1][:2]);print '%02d %s' % (ss,'='*ss)"; sleep 1; done
```

Replace "**wlan2**" with your wireless interface (or leave it out to scan all of them) and "**MyWirelessNetwork**" with the SSID of the network you want to monitor.

It's not quite graphical, displays the signal strength as a number and a line of '=' characters. But it *is* real-time, so it should suit your needs.

It also goes completely haywire if the interface is down or some other error occurs, which is why I put the "**sleep 1;**" there, so any errors don't immediately swamp the screen. You can remove it or tweak the number if you like.

For my own usage, because I needed something like this as well (just wasn't aware of the **iwlist** command), I put it in a shell script, so I can call it easier and/or modify it into something fancier:

```
#!/bin/bash
WSIF=${1:-wlan2}
WSSSID=${2:-MyWirelessNetwork}
while true
do 
  sudo iwlist $WSIF scan |
     grep -B2 "$WSSSID"  |
     head -n1            |
     python -c "ss=int(raw_input().split('=')[1][:2]);print '%02d %s' % (ss,'='*ss)"
  sleep 1
done
```

Again, replace the "**wlan2**" and "**MyWirelessNetwork"** with your own defaults, but with this script you can also specify them as respectively the first and second command-line parameters.

Hope this is useful to anyone!

---

