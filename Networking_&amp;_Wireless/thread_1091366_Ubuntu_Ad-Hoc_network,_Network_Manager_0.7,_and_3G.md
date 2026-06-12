---
title: "Ubuntu Ad-Hoc network, Network Manager 0.7, and 3G Internet surfing"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by Stray63 on 2009-03-09
Hey all,

I've done some searching but can't seem to find anything that's going to work for what I need.

Basically, what I'm hoping to do is connect my Ubuntu 8.10 Laptop to my Ubuntu 7.10 PC. 

My laptop has internet - a 3G card, to be exact, which I run with the Vodafone Mobile Connect software (from Betavine, I think). 

My PC has no internet.

I want to be able to hook up my PC and Laptop to an Ad-Hoc network, where I can:

1) Exchange files.
2) Surf the internet through my PC.
3) Possibly control my Laptop through my PC remotely.

(If I can surf the internet, mayhaps I can upgrade my PC to Hardy). The Wireless on my PC works fine, as I have used it to connect to a wireless network before, but I have moved premises now so now need to rely solely on my 3G.

Step one is the Ad Hoc network, of course, which I can't get going. I click on the network manager icon and say 'create new wireless network', type in a name and give it a WEP key, and it doesn't connect. It does the same on both 8.10 and 7.10, with 8.10 providing me the 'edit networks' option with a right-click.

Upon doing some searching it appears that I may have the wrong Network Manager installed. What I want to do appears easy on a tutorial I found on Network Manager 0.7 at Ubuntu Geek - but I seem to only have 0.6.6 installed. Trouble is, Synaptic doesn't provide any other version but 0.6.6 as the latest Network Manager version, so this may be why my Network Manager looks very different to the tutorials I found at Ubuntu Geek (?). I don't know enough off-hand to download a Network Manager from the Gnome site and build it into Ubuntu. Secondly, I can't get a new Network Manager to my PC on 7.10 because it has no access to the internet.

Once I can actually create an Ad-Hoc network, I suspect I may be able to figure out how to get the PC to use my 3G card in my laptop for the internet - although, if anyone can provide a how-to on that it would be appreciated very much as well. I suppose, from there, the remote software should be pretty straight forward (it seems so).

Thanks in advance!
Stray63

---

### Post by KennyHAA on 2009-05-17
I've been having similar troubles trying to get ad-hoc networking going on my netbook.  First you'll need to upgrade your network-manager to >=0.7.  I was able to get network-manager 0.7.1 installed by following these instructions: [http://andrewalliance.wordpress.com/2008/09/11/how-to-network-manager-07-svn/](http://andrewalliance.wordpress.com/2008/09/11/how-to-network-manager-07-svn/).  I used 'apt-get install network-manager' (to upgrade just network-manager) instead of 'apt-get upgrade' and it worked pretty good for me.

Anyway, I still haven't been able to create and connect to an ad-hoc network.  When I create one and try to connect, I connect for an instant and then get disconnected right away.  However, I am able to connect to other ad-hoc networks that other computers create.  Let me know if you have any success!

---

