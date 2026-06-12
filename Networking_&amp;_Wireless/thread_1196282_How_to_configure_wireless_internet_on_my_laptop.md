---
title: "How to configure wireless internet on my laptop"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by g35celicaz on 2009-06-24
I have ubuntu 8.10 running on my HP Pavilion ze4800 laptop. However I don't know how to get wireless internet on it.

Please Help!

 - Thanks:D

---

### Post by quixote on 2009-06-25
There's not enough information to know how to help.  Do you have the little wireless icon thingy in your taskbar panel?  Does it try to connect and give up, or does it never even try?  Do you have a wired connection?  Does that work?  

It's gotten much easier than in the Bad Old Days to connect to wireless, so this should be solvable with a bit more information.

---

### Post by MaindotC on 2009-06-25
Please try viewing the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  When you are done reading it and following the directions, please let us know if you have any difficulty and precisely with what you are having difficulty.

---

### Post by Iowan on 2009-06-26
):P Jaunty *seems* a bit easier to set up than Intrepid, but there are folks anxious to try. If there is a problem getting the information (much of which is available from a terminal), toss out a question. 
We don't bite...
very hard...
usually...
:D

---

### Post by ourAri on 2009-06-26
This helped me a lot:
[http://help.ubuntu.com/8.04/internet/C/troubleshooting.html](http://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

A couple of tips that might help:
1. Install and use NetworkManager (should be installed by default )
2. Comment out all the lines in /etc/network/interfaces so that NetworkManager manages your network interfaces. Then restart your system
3. A good test to see if your wireless card is installed correctly and powered on, is to run this command:
> sudo iwlist scan

This should give you the wireless networks around you.

---

