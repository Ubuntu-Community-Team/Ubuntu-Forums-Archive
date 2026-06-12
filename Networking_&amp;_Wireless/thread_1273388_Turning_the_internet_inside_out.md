---
title: "Turning the internet inside out"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by mikeym on 2009-09-23
Ever since reading William Gibson's *Idoru* I've been interested in the concept of turning the internet inside out by filtering out everything except the bits you want to create a haven for friends away from everyone else. The idea has been coming back to me lately with the worldwide crackdown on P2P and the introduction of laws in my own country (the UK) which leave decisions about your rights up to faceless members of your ISP and probably worse to machines.

So I was wondering if anyone knew anything about what good software there is to do this sort of thing? Ideally something to share files and documents maybe chat or post webpages, probably involving the sharing of keys in some way. 

From my limited success in researching this WASTE seemed like the closest kind of thing, but it appears to be completely dead to linux.

---

### Post by rafemonkey on 2009-09-23
Have you checked out [TOR]("http://www.torproject.org/")? It won't make a private network, but it will make it very hard for anyone to tie your data and activities to your computer/location. Otherwise you could create a VPN. Which would be like your own private network, but distributed over the internet. Check out [http://www.faqs.org/docs/Linux-HOWTO/VPN-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/VPN-HOWTO.html") for more info.

---

### Post by mikeym on 2009-09-23
VPN is much closer to what I was getting at. I'm not so interested in being able to share things anonymously with other internet users but rather share things with my friends. But I was hoping to find some form of cross platform application that would make that sort of thing easy.

---

### Post by rafemonkey on 2009-09-23
VPN is pretty cross-platform... But easy? Not so much. You could always host your own jabber(XMPP) server, then people could connect to it with an IM client. That way you could chat and share files and links. I don't know how secure jabber is from eavesdropping but it would be private. See [http://xmpp.org/]("http://xmpp.org/") for info. It looks like a couple of the servers are in the Ubuntu repositories, so installing one should be pretty easy.

---

### Post by badger_fruit on 2009-09-23
> **rafemonkey said:**
> Have you checked out [TOR]("http://www.torproject.org/")? It won't make a private network, but it will make it very hard for anyone to tie your data and activities to your computer/location. 


+1 for TOR

Using it last night to watch the CW shows which are only available to americans.

I live in the UK too and think the whole Digital Britain, 50p Broadband tax and now the proposed "micropayments" for the BBC iPlayer are all disgusting.

---

### Post by mikeym on 2009-09-24
I'm really not that interested in TOR or such like (if I was I would probably be going for something like freenet or for files oneswarm) I'm more interested in a space for friends to make the internet how it should be. 

So VPN has piqued my interest a bit but looks terribly hard to set up. Does anyone know if it can be set up to run in a distributed fashion so that it doesn't matter if I have my computer on or not as long as my friends do? I suppose I'm extending the same question to running chat servers / clients, webhosting, file sharing / transfer.

---

### Post by badger_fruit on 2009-09-24
VPN creates a virtual tunnel from one network to another across the internet. You will need to have the "host" network up/turned on for someone to be able to join in/connect.

The internet works because it comprises of hundreds of thousand of "always on" machines.

If you want to simulate that then you need an always on machine for you and your friends to connect into.

However, once you have an always on server, that same server can be configured to do whatever else you want - IM server (not a client, that's the person who connects not hosts the server), web-host and so on.

---

### Post by mikeym on 2009-09-24
Wow... creating a VPN (with openVPN) is not just hard it's really really hard.

Thousands of questions and keys all of which appear to matter and only a text editor and some flaky documentation to suss it out. 

Been at it all day and I'm nowhere.

---

### Post by mikeym on 2009-09-24
OK I'm trying the [community guide again]("https://help.ubuntu.com/community/OpenVPN")

Now it says:

*"Commonly, you have a linux server behind a NAT firewall, and you want to provide access to a small network. Your /etc/network/interfaces probably looks something like"*

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
## This device provides internet access.
iface eth0 inet static
  address 192.168.1.10
  netmask 255.255.255.0
  gateway 192.168.1.1
```

Now this is a stupid problem but I don't have a bit like:

```

# The primary network interface
## This device provides internet access.
iface eth0 inet static
  address 192.168.1.10
  netmask 255.255.255.0
  gateway 192.168.1.1

```

I assume this is because I'm using dhcp. But I've assigned my mac address to a static IP on my router. 

So what do I put?

---

### Post by aesis05401 on 2009-09-24
You need the auto line to tell the system to attempt to load the interface automatically, then you need a one line definition for the interface like this:
```

iface eth0 inet dhcp

```

Your card should attempt to acquire an IP address from the dhcp server on boot.

---

### Post by mikeym on 2009-09-24
OK from what you said I've guessed that the next step in setting up the interfaces was:

```
auto lo
iface lo inet loopback

iface br0 inet dhcp
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down 
```

But unfortunately that doesn't appear to be it.

---

### Post by aesis05401 on 2009-09-24
Hello again, 

I don't fully understand what you want to accomplish, but it is better to break this project into smaller pieces.  We should make your experiment modular.. easily changed.  First, let's make a plain interfaces file that will bring lo & eth0 up in a working state when you boot your machine:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

```

Now open a terminal and download the following packages if you do not already have them:
```

sudo apt-get install bridge-utils
sudo apt-get install uml-utilities

```

Now you can create a simple script for each type of configuration you want to try.  Don't spend too much time making the scripts nice until you know they are accomplishing what you want.  Copy the following into a text file named 'bridge-up.sh' :
```

#!/bin/bash
# Create a bridge using brctl utility from bridge-utils package
brctl addbr br0

# Prepare eth0 to join bridge
ifconfig eth0 0.0.0.0 promisc

# Connect eth0 & br0
brctl addif br0 eth0

# Create whatever tunnels you want/assign IP address information.
# You can use dhclient <device> to apply for dhcp addressing.
# You can use 'tunctl' from the uml-utilities package to create tunnels
# ... but that is another topic.

```

From a terminal make this file executable by doing :
```

chmod +x bridge-test.sh

```

Your script must be run with sudo permissions in order to complete without errors.  If the bridge setup gives you the functionality you desire, then either expand the script to accept up/down flags, or create a second script reversing the network change:
```

#!/bin/bash
# Destroy bridge, return eth0 to default state
brctl delif br0 eth0

# you must repeat 'delif' for each device on the bridge before you 
# can delete the bridge in the next step
brctl delbr br0

# Take eth0 out of promisc mode, apply for dhcp addressing
ifconfig eth0 -promisc
dhclient eth0

# Insert instructions here to clean up any other objects you create in 
# your bridge-up.sh script...

```

Again, use the chmod command to make your script executable.  If you decide you want to boot up into your bridged state, then you can link to your script from the 'rc' directories in /etc to get them run at the proper startup stage.

Does this help?

---

### Post by mikeym on 2009-09-28
My problem is that I don't really understand what [the tutorial]("https://help.ubuntu.com/community/OpenVPN") on setting up a VPN is trying to do at this stage either. 

```

## This is the network bridge declaration
auto lo br0  ## start on boot

iface lo inet loopback

iface br0 inet static 
  address 192.168.1.10 
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down 

```

Your 2 scripts run fine but since I'm not sure what I'm hopping to achieve (well... generally I imagine it is to create a network bridge then attach the internet to it and a VPN on a virtual IP range) I don't know how to check it's worked or finish it off.

---

### Post by ajaustin on 2010-03-14
> **badger_fruit said:**
> +1 for TOR

Using it last night to watch the CW shows which are only available to americans.

I live in the UK too and think the whole Digital Britain, 50p Broadband tax and now the proposed "micropayments" for the BBC iPlayer are all disgusting.

I live in Spain and can't get any of the online TV from UK, eg iPlayer.

I set up Tor but that didn't help me.  I suspect because the end IP wasn't in the UK either.  I know that I can pay for a UK proxy but they are very expensive for what I want to do.

Could I may Tor look like it's coming from the UK?  Or are there any other options?

Tony

---

### Post by mikeym on 2010-03-23
TOR is really for hiding your location behind a series of server 'hops', so it all depends on where the last 'hop' is located. 

I'm afraid I don't know how you would do this. Sorry.

Also not sure I approve as a UK licence fee payer :)

---

### Post by ajaustin on 2010-03-23
I take your point about UK licence fees.  I would be happy to pay them but that would not give me access to iPlayer. BTW, the BBC's web site carries advertising so maybe the licence fee isn't really an issue - even though I block their advertising with AdZapper.  <g>

I watch BBC, etc, on Sky here in Spain which actually isn't illegal for me to do.  But again, I would be happy to pay a licence fee if "they" could sort out a way to do it.

Thanks for your reply on Tor.

Tony

---

### Post by mikeym on 2010-03-24
No Worries. I was kidding about the license fee by the way. The government here seems to be determined to siphon as much of the license fee away from the BBC as possible anyway. 


I'm surprised that they carry advertising though. Do they do it on non-UK IP's? As far as I was aware the BBC were only allowed to advertise their own stuff - didn't know that they could advertise to non-UK people.

---

### Post by ajaustin on 2010-03-24
[http://news.bbc.co.uk/](http://news.bbc.co.uk/) carries a banner ad and other embedded ones and many, if not all, of the Watch videos have ads before you get to see the video.

Tony

---

