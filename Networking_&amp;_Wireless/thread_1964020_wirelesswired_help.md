---
title: "wireless/wired help"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by Fenris_rising on 2012-04-23
Hello there.

I am currently bouncing off the walls with frustration and am about to start spitting blood!

I have read and tried a couple of methods to try and do the following to no avail.

What makes it worse is I once managed to do this with my old, soft modded xbox, with no problems but now I seem to be floundering.

OK the setup-

One PC wirelessly connected to the net.
Next to it a second PC not connected to the net.

I have used a crossover cable to connect the two with the hope to access the internet as well as set up an ssh link etc.

I can ping each PC from the other successfully but I cannot establish a functional internet link or ssh despite this tenuous link.

I have set the NIC cards to manual IP. My router runs on a 192.168.1.254 setting so the 2 static addresses are 192.168.0.x. This is how I did it with the xbox set up and I was able to browse the web and stream movies from the PC to the box as well as access the xbox files.

I've installed dnsmasq as well due to the method above not working to no avail. So I'm stuck. Please help before I bust a major bloodvessel :lolflag:

Both PC's are running ubuntu and I am able to swap files via ssh between my ubuntu laptop and the wireless PC with ease.

EDIT: ssh via terminal does work in both directions. Surely its a minor thing to get the internet shared then?

regards

Fenris...runing out of O neg even as I type!

---

### Post by Fenris_rising on 2012-04-23
Hi there.

Sorted.

One the wireless PC - Leave the wireless as is. For the wired connection (ethx) set this to 'Shared to other computers'. Reboot! I missed this.

On the PC you have wired to the wireless PC - Set the wired connection (ethx) to DCHP. Reboot! I missed this.

With these settings I have shared internet, SSH works and as an aside Synergy works great.

With Synergy, it uses wireless by default, on the client PC enter the IP of the Synergy server in the 'name of server' entry box and the jobs a gooden!

regards

Fenris

---

