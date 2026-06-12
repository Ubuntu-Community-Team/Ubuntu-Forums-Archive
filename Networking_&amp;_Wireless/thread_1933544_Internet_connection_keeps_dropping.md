---
title: "Internet connection keeps dropping"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by Kramer2010 on 2012-02-29
Hi all

Just over a week ago my internet connection started to drop out after every couple of pages. My wireless router (Virgin Super Hub 30meg) is has a good signal and i dont think it is the problem as I am using Windows 7 boot side of my laptop with no problems. Have no idea what has happened as I have been using ubuntu since 10.04 upto 11.10 flawlessly. At the moment I can only run Ubuntu through the ethernet cable.

Any ideas?

Packard Bell Easynote TJ68

Pentium Dual Core T4400 2.20GHz

4GB Ram

Mobile Intel 4 Series Express Chipset (first graphics card thats not caused any problems!)

Atheros AR5B93

---

### Post by dandnsmith on 2012-02-29
Is there any software update which corresponds to the start of the trouble?
When the trouble occurs, have you looked at the state of the interface with ifconfig etc, tried ping, traceroute ... ?

---

### Post by Kramer2010 on 2012-03-01
> **dandnsmith said:**
> Is there any software update which corresponds to the start of the trouble?
When the trouble occurs, have you looked at the state of the interface with ifconfig etc, tried ping, traceroute ... ?

Can probably find out how to do ifconfig, ping, traceroute etc, but I not sure if I would fully understand the results. I have recently dabbled with Wine and I think I may have downloaded a dodgy windows application which I became suspicious of and cancelled. I know ubuntu is more resistant to virus/malware, but is it resistant to the users stupidity? Do you think I may have infected my Ubuntu installation?

---

### Post by dandnsmith on 2012-03-01
Linux, as such, is not subject to the same problems as Windows, and cannot catch the same sort of virus infection (but it looks as if some people are working on this). Usually what you have to watch for is trojans.

It's quite possible to mess up a Ubuntu installation all by yourself (I've done it several times).

I strongly recommend using the information available to you with *man* pages from a terminal window, to find about the various commands mentioned (or just google for it).

I don't think downloading a dodgy windows application and then cancelling will harm the Ubuntu system - but I couldn't guarantee it.

---

### Post by hishmaj on 2012-04-03
I am having the same problem. The connection drops everytime I start a video stream or download a file. In short, the connection drops when it uses a higher bandwidth, not necessarily when browsing webpages.

I am using the Netgear SuperHUB provided by Virgin Media too. So I am guessing it has nothing to do with any virus or update. 

It works fine on Windows and Kubuntu, which run on the same machine.

---

### Post by alex.nucleo on 2012-04-04
> **hishmaj said:**
> I am having the same problem. The connection drops everytime I start a video stream or download a file. In short, the connection drops when it uses a higher bandwidth, not necessarily when browsing webpages.

I am using the Netgear SuperHUB provided by Virgin Media too. So I am guessing it has nothing to do with any virus or update. 

It works fine on Windows and Kubuntu, which run on the same machine.


Exactly the same problem for me with every version of Ubuntu since 10.04 or so, but I don't use Netgear. So it has nothing to do with Netgear. I think this is a problem with Network Manager. If you find how to fix this, please, let me know here.

---

