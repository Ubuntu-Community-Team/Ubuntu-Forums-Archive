---
title: "Lucid Lynx Connection Problem"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by Stephen Shellard on 2010-05-22
I recently upgraded to Lucid Lynx which went smoothly, requiring just a few adjustments to get things working.  Yesterday however my internet connection ceased to work.  I booted into an earlier version of the kernal [2.6.31.21]  which works fine so far as my internet connection is concerned, and I assume means that all my hardware is in order.

On rebooting to the default kernel [2.6.31.22] The connection is again not working and indeed I have tried repeatedly to reboot but so far with the same outcome. 

My system is wired and set up with static IP addresses,  which all appear in order.  I did try temporary reversion to DHCP, but this did not make any difference. 

The connection carries the default Auto Ethernet name.  The computer on which lucid lynx is installed is 192.168.0.2; the subnet mask is 255.255.255.0  and the gateway address is 192.168.0.1

Using  the Network tools [Administration/Network Tools] I have attempted to ping the router/gateway [192.168.0.1], but I get zero return on transmission statistics which would I assume means there is no connection.   This is about the extent of my knowledge of how to use the Network tools.  

I have been unable to find anything in the forums which matches my particular problem and so advice on further steps which I might take to correct this would be greatly appreciated.

---

### Post by Stancel on 2010-05-23
I experience this same problem. The Internet sometimes works for some time then suddenly I get kicked off the wi-fi network. I have to reboot the computer to get it working again. This only started happening once I upgraded to Lucid. 

I disabled ipv6, which is the only thing I've found on how to stop this. It still kicks me off, so, I wouldn't recommend that solution.

---

### Post by kennethmaclean on 2010-05-23
Same problem with the 32 bit. I've tried everything, even the kitchen sink. Nothing works. It's must be lucid's kernel (2.6.31.22) which is causing a lot of problems with network connectivity. As a workaround, revert to 2.6.31.21 and wait till some whiz kid tells us what to do. Or build a new kernel yourself!

---

### Post by Stephen Shellard on 2010-05-28
Thank you for these responses. 

As regards Stancel's comments:  I have set IPV6 to "ignore" which would appear to be the default.  However I noticed the following link: [http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)  which shows how to disable IPV6 in some more definitive way. I've done this, but all to no good, as my connection continues not to work with Kernel 2.6.31.22.  Still, I am glad to have ruled out this as an issue.  

It would seem that, as Kenneth MacClean suggests, that I must wait for some whiz kid to tell me what to do.  Surely though, if this problem is at all widespread, whiz kids would have been at work and remedies would already be in place? Since none have been forthcoming I conclude that the problem is relatively rare and arising from circumstances which are hard to pin down. I'm stuck, that's for sure.

---

### Post by Stephen Shellard on 2010-05-29
A strange thing has happened today.  

I briefly lost power to my Netgear router.  This does not reliably pick up the Internet when switched on and as on previous occasions I had to switch off and on a few times before getting the green lights which tell me an internet link has been established.  

Out of curiosity I booted into the 2.6.31.22  Kernel and to my surprise find that I have the Internet.  So is this related?  Was there a problem with my router relative to this Kernel all along?  I have just done a restart to check this was not a complete fluke and everything seems to be in order.  

I shall report back if there are further developments in this curious tale.

---

