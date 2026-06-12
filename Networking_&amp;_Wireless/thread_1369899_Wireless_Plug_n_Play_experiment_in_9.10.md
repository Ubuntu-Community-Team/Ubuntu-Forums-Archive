---
title: "Wireless Plug n Play experiment in 9.10"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by phreakshew on 2010-01-01
Hello all - just wanted to share with you my experience trying several different wireless adapters to see which ones would work "out of the box".

I purchased 5 different wireless adapters from our local big box electronics store, and tried them out one by one. I did not attempt to reconfigure anything, nor did I use ndiswrapper. I merely wanted to see if I could simply plug in a wireless adapter and start surfing the net.

Desktop computer is a Dell Optiplex GX270 running Ubuntu 9.10.
We are using a Linksys WRT300N Wireless N Broadband Router.
Our network has WPA encryption.

Here are the items I quickly tried:

1. "Refurbished" Netgear WPN111-NAR USB adapter - absolutely nothing happened when I plugged this in. It was as if there was nothing there.

2. D-Link DWA-125 Wireless N (Wireless 150) USB adapter - my network manager said I was connected to our network, but no bars were lit up, and I could not get online.

3. Trendnet TEW-644UB N USB adapter - this seemed to work automatically. I was able to use Synaptic Package Manager and download and install updates for this computer. I was able to briefly get online via firefox; I could type in "test" for instance, and google would bring up a list of websites. However, for some reason I could not get past the first page. It would just hang and keep trying to load various websites, and eventually would declare I was offline. Restarting firefox would help, but still I could not seem to get past a preliminary google search. 

4. Trendnet TEW-423PI Wireless G PCI adapter - after installing this card Ubuntu would not load. The computer would post, and then stay on the black screen, never loading the desktop. I read that other people had this issue and they had to take the card out, load the correct ndiswrapper drivers, then reinstall the card to get it working. Here's the link: 
[http://ubuntuforums.org/showthread.php?p=7794144]("http://ubuntuforums.org/showthread.php?p=7794144")

5. Netgear WG111US Wireless G USB adapter - Success! This was truly plug 'n play. All I had to do was enter in the WPA code and my user password, and voila! Internet works. Right now I'm watching "Family Guy" on Hulu. :-)

This brief experiment does not suggest that any of these cards cannot be made to work - I was just feeling lazy and wanted to see what would work automatically. Now I have to find my receipt so I'm not stuck with all this extra stuff!

):P

---

### Post by gordintoronto on 2010-01-01
Cool!  For people who want to buy one wireless adapter and have it work, here is the place to go:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) 

One of the least expensive PCI adapters is the D-Link DWL-G510, which "just works."

---

