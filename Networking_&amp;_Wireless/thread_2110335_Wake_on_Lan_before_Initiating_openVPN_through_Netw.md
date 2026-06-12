---
title: "Wake on Lan before Initiating openVPN through Network Manager"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by kid1000002000 on 2013-01-30
Hello,

I have written a python script (packable in a bash wrapper if needed) capable of starting an openvpn server. This script will release the shell (correct wording?) once the server is accessible. Is there a way that I can have this script run automatically when I go to connect to the VPN via the Network Manager interface?

---

### Post by ahallubuntu on 2013-01-30
Let me guess: you'd like to VPN to a server remotely but wake it up first?  Sorry, you'll have to wake it up without using its VPN.  Or, leave it on.   (And just leave your OpenVPN - software - server running all the time too.   Why would you want to enable it and then disable it?)  Or, leave some other server on on your network and open an SSH port for it so you can get to it remotely or something.

The approach I use is to have OpenVPN running my router, which is always on.  I have DD-WRT firmware on my router, and my router has enough RAM and NVRAM that I can run the full version of DD-WRT that has OpenVPN built in.  Then, I don't have to run OpenVPN on any dedicated machine - I can use the router.  And I can wake up my local machine once I've connected to the VPN.  (DD-WRT has Wake-On Lan support built in, too.)

If you can find an old Linksys WRT54G version 4 or older (or WRT54GL) you can run the full version of DD-WRT with OpenVPN and use that as your network firewall/gateway.  It has only G wireless but you could disable that and use another router (802.11n) if need be for wireless if it's better.  If you have a cable or DSL modem, dump the output to the WAN of the DD-WRT router and use the DD-WRT router for your local network.  Forward port 1194 through your modem's (router's) firewall to the DD-WRT router so you can do OpenVPN.

---

### Post by kid1000002000 on 2013-01-30
Yes, good guessing. To rephrase "capable of starting an openvpn server," "start up the PC from a cold shutdown via a Wake On Lan script." OpenVPN of course initiates automatically server-side, on it's own, during boot.

My current situation is to start the machine via this script, then initiate the VPN via NM. I want to combine these steps into a single action: clicking on the NM's VPN menu item.

The reason I am not using openVPN directly in my router is because my Netgear WNR3500v2 is not capable of running openvpen. It has already been flashed to DD-WRT. If I had the cash, I would probably invest it in a 2nd Raspberry Pi to leave on 24/7 instead (a better investment to me), but as I don't want to foot the electric bill of running my headless desktop server all the time, it (headless desktop server) stays off. It [said machine] is used infrequently enough that this method works for me.

You are right, the right way to do things is to get a better router. Unfortunately, I have to work with what I've got for now, and instead of clicking two buttons (1 to run the script, 1 to connect in NM) I was hoping to link the two via the NM interface.

---

