---
title: "DWL-G510 no longer working in Dapper"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by sambram on 2006-06-09
Hey everybody. After I messed up my upgrade to Dapper, I did a clean install. At first "lspci" didn't detect my wireless adapter, though it did after switching the PCI slot it was in with another card. It's a DWL-G510, with a Marvell chipset.

Next I installed ndiswrapper-utils (From the Dapper CD). When I went to install the driver it balked about not finding a zeroconf section, and so i edited the .inf to uncomment an empty zeroconf section. It claims to install okay, and ndiswrapper -l tells me "driver present, hardware present."

Now, when I first looked at my etc/network/interfaces file after install it only had lo. Adding wlan0 manually hasn't helped at all... 

ifdown tells me the device isn't configured
iwconfig claims it doesn't exist.

I'm fairly stumped, and just want my wireless, so any help will be greatly appreciated. :)
By the way, the card DID work under Breezy.

---

### Post by Patsoe on 2006-06-10
Can you post the output of iwconfig?

Also, can you try "sudo modprobe ndiswrapper" and then "iwconfig"? Let's see what it says, and we can take it from there...

---

### Post by sambram on 2006-06-10
iwconfig yields

```

lo             no wireless extensions
eth0         no wireless extensions
sit0          no wireless extensions

```

no difference after modprobe ndiswrapper.

---

### Post by Patsoe on 2006-06-10
[QUOTE=sambram]Now, when I first looked at my etc/network/interfaces file after install it only had lo. Adding wlan0 manually hasn't helped at all... 
[/QUOTE]
I just reread this line, and was thinking... on my machine, the wlan interface is not called wlan0, but eth1. You might want to try that in there instead?

---

### Post by sambram on 2006-06-10
I'll try, I had put in wlan0 because that's what the interface worked as under Breezy.

---

### Post by sambram on 2006-06-10
No change after changing the interface name to eth1.

---

### Post by Patsoe on 2006-06-10
[QUOTE=sambram]No change after changing the interface name to eth1.[/QUOTE]

Uhm, right. :-? There's probably a very straightforward method of finding out what the interface should be called. But I don't know that method....

What I did (that was in Breezy) when I had messed up my /etc/network/interfaces, was backing it up and then just removing everything except the lo bit. Then, if you use the menu System->Administration->Networking you can (hopefully) see all interfaces and configure them graphically.

Note: I think you need to set the ndiswrapper alias first. This is through "sudo ndiswrapper -m". Which writes an entry to /etc/...?.../aliases ...

---

### Post by twotonz on 2006-07-19
Hi Sambram,
I think we could be possibly sharing the same problem. Was happily useing my D-Link card, under dapper for many weeks. I then had the bright (?) idea of experimenting a bit, and after reading about the wonders of "zeroconf", figured that it could be something to use at work, installed it, & everything was fine on my side.
 Unfortuantly, my neighbour, who's wlan I use, got a bit upset with me (or rather zeroconf), because his router was getting pinged every 30 sec's, & was constantly recieving e-mails from the router warning about a hacker attack(!!!).
 Anyway, promtly dumped everything to do with zeroconf (2 packets got removed), and since then, try as I might, am getting no connection at all with the wlan. 
 Is it possible that you have also installed at some time "zeroconf"?
 As regards to changing the interface name, hummm, I have read that more than once people have gotten in a right mess, after fiddling with the names. I could be wrong on this, but, as I understand things it doesn't matter how your card is called, as long as it is the same system-wide. (Some of my pc's have wlan interface's called eth1, some with ra0, and others with wlan0).
 Anyway as usuall, I have rattled on here, without contributing much. Basically I am really interested in your answer to the question concerning zeroconf.

Love & Peace (to all)
anthony

---

