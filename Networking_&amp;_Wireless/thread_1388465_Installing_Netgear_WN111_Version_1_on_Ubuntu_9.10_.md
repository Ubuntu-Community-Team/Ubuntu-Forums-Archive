---
title: "Installing Netgear WN111 Version 1 on Ubuntu 9.10 Karmic Koala"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by skysurf76 on 2010-01-23
I've been trying to get a MythTV rig setup for days now and just keep running into one problem after the other and knocking them out one at a time by reading posts made by other people and I ran into a network problem and I got it figured out so I thought I would do my part my posting my fix.

I just bought a recertified Netgear WN111 from TigerDirect and I believe it is a version 1.  I am 98% sure.  I just haven't spent the 30 minutes researching how to find out which it is, but I believe if it was Version 2 it would have been autodetected by Ubuntu 9.10 according to my research.

Make sure the WN111 is plugged into a working usb port before starting this.

Anyway, on to the install.

1) Go to System. Administration, Synaptic package manager.

2) Go to the networking section (not networking universe, or networking multiverse, just plain networking) and select ndisgtk.  When the window pops up click mark to install, then up at the top of the Synaptic package manager window click "apply".  The package will install.  It will install several packages and we need them all.

3)  Download this file (I found it on another post, but I'm too tired and drunk to give credit currently). [http://www.mediafire.com/?2d0ndtxzlye](http://www.mediafire.com/?2d0ndtxzlye)

4) Go to system, administration, and you will see windows wireless drivers near the bottom.  Click on it.

5) One it opens up click on "Install new driver".  Point to the .ini file that I just had you download.  What I had you download has two files in it, but we only need the .ini file.

6) It will tell you that it can't detect the hardware, close that message box, and you will see your network adapter in the list and it will say "hardware detected" even though it just told you it couldn't detect it.  ( I chuckled )

7) Now here is what took me so much time.  At this point if you do a ifconfig in a terminal window the adapter shows up, but when you go into system, preferences, network connections it doesn't show up.  To work around this go into the synaptic package manager again (see earlier step for getting to synaptic package manager), and go to the network (Universe) section and find wcid, select it, mark it for install, then hit apply up top as before.

8)  This will uninstall the network connections program that came with ubuntu, but don't worry about it, in my opinion wicd is better.  Its prettier, has more buttons, the layout is better, and it works when the other one didn't. =P

9) Once all that is done go into Applications, then Internet, then Wicd Network Manager and the WN111 should show up right there.  When you first start Wicd Network Manager its going to yell at you about it not having the resources it needs or some garbage but just close that box and keep going.  Whatever its missing it apparently doesn't need because I'm typing this on a connection on my WN111.  Configure your adapter in Wicd and you're good to go.  Configuration in Wicd is VERY straightforward unless you're new to networking and that is beyond the scope of this how to.

Hope this works for you because I poured through 20 posts with more lines of commands than I could shake a stick at, and after every one I cracked open another beer.  

I hope this guide solves your problem if you're trying to get your WN111 working.  If it just causes you more frustration I apologize.  I just figured I would post what worked for me since it took me so long to figure out.

Now if you'll excuse me, I got the next disc of True Blood from netflix today. :)

P.S. HDMI sound won't work on the Asus M4a785TD-M EVO board until you go into hardware drivers in Ubuntu and install the AMD driver.  Don't try to install the driver by yourself by going to the AMD website and using their installer.  Yeah, that one cost me about 2-3 hours. =/

---

