---
title: "HOW TO: get a Netgear WG311v3 to work"
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by ahlandberg on 2006-05-16
Subject to: Netgear WG311v3 54Mbp/s wireless ethernet card

What I have done so far:

Managed to establish a eth0 wired connection via my DHCP router which can connect to the internet.

Managed to install and configure my WG311v3 using ndiswrapper.

However, although the wlan0 is shown under 'Network Settings' and is active, I cannot connect to the internet nor can I ping any address: 'network unreachable'.

I have been elaborating on this problem for ages now and wondering if there's either a cure for the problem or whether it's simply impossible to get it up and running.

Another problem is that when I get the wlan0 connection set up and re boot the computer, it has disappeared. I then followed what several threads suggested and put these lines into my /etc/modules file:

sudo depmod -a
sudo modprobe ndiswrapper

But it didn't fix the problem, when re-booting, the wlan was disappeared.

I am totally new to linux and appreciate any help!

Cheers, Anders

---

### Post by slightly72 on 2006-05-16
Those lines in /etc/modules do not do anything (actually, they'll generate errors). That file should contain only the names of the modules that need to be loaded. "depmod -a" is a command, not a module, so it should be eliminated. The second line should read only "ndiswrapper". 

You should also try the solution posted here: [http://ubuntuforums.org/archive/index.php/t-76804.html]("http://ubuntuforums.org/archive/index.php/t-76804.html") 

You might want to start clean with ndiswrapper (uninstall it from Synaptic) and delete the subdirs in /etc/ndiswrapper.

---

