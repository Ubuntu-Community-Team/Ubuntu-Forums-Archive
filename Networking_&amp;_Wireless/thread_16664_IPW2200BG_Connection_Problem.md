---
title: "IPW2200BG Connection Problem"
date: 2005-02-23
forum: Networking &amp; Wireless
---

### Post by Vesperan on 2005-02-23
Hate to add another 'I cant connect to the network!' thread - but I cant.

The system is a Dell 600m laptop with Intel Pro Wireless 2200BG pcmcia card. I followed instructions [here](http://ubuntuforums.org/showthread.php?t=13576) to install the drivers. The driver number is 1.01, and the latest firmware was used.

I believe the drivers are working fine. **After following the instructions and using wifi radar, I connected to my wireless network fine using DHCP. However, after resetting I cannot connect** - DHCP requests are sent, but no reply is received.

Just in case, I had better layout the network here. There is an ADSL/4  (Dynalink RTA300) port switch that handles assigns the IP addresses to computers connecting. This is connected to a wireless bridge (Netgear), which in turn is connected to a wireless router (Netgear). 

I'm not the greatest at Linux, but it seems to me that my laptop is setup fine and is trying its hardest to connect, but that something is stopping a reply back (or stopping the request from being sent even though it says it is going?). The driver modules (ipw2200, ieee80211) are loaded fine and a modprobe gives the correct response. Something that was 'opened' or setup right during the driver installation is 'closed' or not starting correctly after resetting, and now I'm stuck. 

This is the second time it has occurred to me, as a couple of weeks ago the same thing happened, and only now after a Ubuntu reinstall have I gotten around to trying it out again - to meet the same problem.  So, any help is welcome, just tell me what to do.

---

