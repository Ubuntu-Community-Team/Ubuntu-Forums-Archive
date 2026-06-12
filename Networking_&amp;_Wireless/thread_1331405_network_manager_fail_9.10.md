---
title: "network manager fail 9.10"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by Shooree on 2009-11-19
Hi all, please bear with me. Since turning on my Acer Aspire 5920G this morning, I'm having major trouble with my network connections. Just last night, I was happily enjoying a lan party, through a wired connection to a windows machine. I had NO previous connection problems whatsoever, and I can't stress this enough.

Now I'm at a friend's house. She's got a hidden wireless for which I know all the settings. First I was surprised since I couldn't find the profile I thought I already had set up for this connection in my network manager, but whatever, I created a new one. 

Problem 1: clicking on "connect to hidden..." and choosing the connection profile I just made results in the "apply" button and password field being grayed out and I am unable to proceed from the window in which I choose the desired hidden network. I was able to connect to an unsecured wlan, from which I am writing this.

Problem 2: tried running apt-get, tried downloading random stuff bigger than cca 10MB through this wireless connection. What happens is that it starts great and then just dies off, leaving me with 0/0 transfer rate, after about 10 seconds. Tried restarting a dozen times, reconnecting, nothing helps. Yet, I remain connected and if I restart the download, it will do the same thing, over and over again.

Problem 3: Tried connecting to a wired network with DHCP, so just p'n'p. Did this hundreds of times before. It won't connect at all. Tried restarting and rebooting, absolutely nothing happens. checked the cable, lights are on, everything seems fine. 

Problem 4: nm-applet in my systray isn't showing since a few reboots ago. First time it happened, I was able to get it to show by calling it from the terminal, but now not even that helps. There's an empty spot in the systray where it should be, but it's not there (tried clicking, heh). (EDIT: I foud this bug being reported as Bug #482684 on Launchpad) Running the nm-applet command in the terminal, both then and now, results in the following messages:

```
** (nm-applet:2390): WARNING **: <WARN>  request_name(): Could not acquire the session service as it is already taken.  Return: 3


** (nm-applet:2390): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

```

I know nothing about this, but I suspect this Dbus thing should initialize, for me to have proper networking. 

Being that this is a laptop, with a hardware on/off switch for wireless, it is on by default at system reboot. I seem to be getting some error messages right before the GRUB fully loads, but they go away too fast and I don't know where to find them. Tried pressing the wireless button during grub loading process, and it gave some more messages on that same screen, I saw ERROR written at least once, but not much else. 

I just can't believe that a thing like this can happen by itself. I repeat, I touched absoultely NOTHING since last night, when it all worked just fine. Please be so kind and pass me some advice, I'll be here refreshing the page... You can also find me with the same nick on IRC #ubuntu and #xubuntu if you can help. My biggest problem is that at home I only have a wired connection, so if I don't resolve this now, I'm screwed royally. Please help and thanks for your time spend reading this.

---

### Post by Iowan on 2009-11-19
Check */etc/network/interfaces* to see if something may have changed it - there should be only a couple of lines defining "lo".

---

### Post by Shooree on 2009-12-01
I checked the interfaces and indeed it just says

```
auto lo
iface lo inet loopback
```

Still absolutely no idea what to do in order to get the hidden network going. I've included a screenie of the offending window. Any ideas welcome.

---

