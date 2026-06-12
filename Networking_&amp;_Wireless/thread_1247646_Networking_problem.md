---
title: "Networking problem"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by ezrahoch on 2009-08-23
Hi,  I have my linux up and running for a long time. I have no idea what happened, but suddenly it doesn't connect to the network.  When I run /etc/init.d/networking restart I get many &quot;Permission denied&quot; errors.  Any ides?  Thanks! Ezra

---

### Post by 505 on 2009-08-23
Run the commena with sudo:

sudo /etc/init.d/networking restart

---

### Post by ezrahoch on 2009-08-23
I get the following:
[some copyright stuff]

SIOCSFADRR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listinging on LPF/eth1/00:50:fc:c4:fd:4d
Sending on LPF/eth1/00:50:fc:c4:fd:4d
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
...

Thanks,
Ezra

---

### Post by cutterjohn on 2009-08-23
OOC I just did a reboot into Ubuntu this morning and ended up with networking down, and tracked it down to somehow bridge & ipmasq packages got installed on Friday morning.

I don't recall specifically installing them, and see no reason why I would have as I don't have a use for either functionality ATM, but I can't help but wonder if some update on Friday may have had erroneous depencies, but I couldn't see where ipmasq or bridge were reqiured by any other package.  (Of I had done package db updates since they were installed, guess that I should pay more attention to what updates want to do in the future now...)

So, if you see ipmasq & bridge installed you might want to remove them then try re-starting networking...

(I wish that the package db had a way to query install time and what triggered installation of individual packages, but here I could tell that it was friday morning my modification times on if-pre-up.d and the modification time on the ipmasq directory in /etc .  Unfortunately the package cache directory maintains original package creation date rather than download time, so that was no help, only the mod times on those 2 directories...)

Might also want to check and see if anything was added that change iptable rules, maybe grep iptables in the /etc directory...  (ipmasq messes with iptables of course...)

---

### Post by ezrahoch on 2009-08-23
Thanks for you suggestions.

I don't have bridge or ipmsaq.
Also, my computer had this problem starting from Thr, so on Friday it was disconnected...

I wrote:
sudo iptables --list

and I get and empty list. Is that a problem?
If so, what should I do to fix it?

Thanks,
Ezra

---

### Post by cutterjohn on 2009-08-23
Sorry, not really sure other than ipmasq/bridge getting installed were my problem.

It looks like your network card is being brought up as it appears to be trying to contact the DHCP server.  Is your router/DHCP server setup correctly?  Did you make any changes to it recently?  If you've got a hub or switch on the network, is it still working? Your ethernet cables good/plugged in? Checked your configuration in network manger?

If all of that seems OK, the quickest way to get help would be to try the IRC channel...

---

### Post by ezrahoch on 2009-08-23
My router seems to work ok, as my windows station connects to the internet fine.  I changed my ISP just before the linux stopped seing the router. However, the windows sees it, so I assume the linux should see it as well.  The ethernet cables seem to be ok, as the lights are on (both on the network card and on the router).   One more thing, the router lists the linux as getting an IP. That is, the linux is listed on the router's client list.  The linux network manager never worked on my machine very well, so I'm not sure what I should check there.  What is the IRC channel?  Thanks, Ezra

---

### Post by cutterjohn on 2009-08-23
[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

It's probably becuase you changed ISPs, so you might have to adjust your router's configuration... (Do you have any other computers connecting to the internet now? i.e. how are you able to access the forums ATM?)

Try the #ubuntu channel first, do a /join #ubuntu

If you've only got access to Windows(of some type) ATM mIRC is a decent Windows IRC client.... otherwise if you're on linux somehow online use one of the ones listed on the above page... if you're using something else for net access you're on your own, i.e. you'll have to search for a client yourself...

---

