---
title: "Hiding on a network"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2010-08-31
Just wondering, is there a way to hide my computer (at least in the graphical environment) so that even if someone managed to hack into my wireless (despite my password that would take "8 octillion years" to crack) and joined my network, they wouldn't see my comp in their network/network places window. Just to make it that little bit harder for them and buy me more time to catch them?

---

### Post by scorp123 on 2010-08-31
> **Jonny87 said:**
> so that even if someone managed to hack into my wireless  It would be better to prevent that step from ever happening, e.g. by using WPA and strong passwords.

> **Jonny87 said:**
>  they wouldn't see my comp in their network/network places window. They would only see your computer in that window if you were running services such as SAMBA. But seriously: if a hacker manages to get into your wireless network then he's probably sitting at a terminal anyway and won't even bother to look at a GUI. So it's utterly pointless whether or not your computer does show up in "Network Places" or not, as a hacker will not waste his time looking at that. And a hacker will use a port-scanner anyway, so he will sooner or later find your computer, "Network Places" or not.

> **Jonny87 said:**
>  Just to make it that little bit harder for them  You should prevent them from ever getting into your wireless and/or getting in from the outside via your Internet firewall/router. If they're inside your network then the only layer of defence that you have left is your username and password. And don't ever enable the "root" account, because that account is obviously the first a hacker will be looking for. Because it exists on all Unix-like OS all a hacker has to do is to guess the password somehow ... so it's safer to leave it disabled (as is the case in Ubuntu "out of the box").

> **Jonny87 said:**
>  and buy me more time to catch them? To do what then?? The only thing you really can do is unplug your wireless access point and then reconfigure it. If ever a hacker makes it into your WiFi network then this is the only measure that really helps, everything else --like trying "counterattacks" or such BS-- is just a waste of time and actually helps the hacker, e.g. with every TCP/IP packet you send his way he can gain more information about you, your OS and your network. Unplugging power and physically disconnecting the network is the only thing that really helps. And before you ever reconnect anything you will have to reconfigure your WiFi (new channel? new frequency? new and better complex password? ...) and maybe a few other things (e.g. Internet router?) or he will be back into your network in no time.

---

### Post by mickwombat on 2010-08-31
Change the workgroup on your Ubuntu machine to something random that can't be guessed easily.  The default is WORKGROUP which is the same on a lot of Windows PCs.
If someone*has* hacked into your router, then they could probably run a packet capture in Wireshark for example and see the name and workgroup of your computer.  Keep in mind, that this is generally only possible in Linux....unless you spend about £3000 on some funky software.  This by default eliminates about 99.5% of the population. ;-)
If you're really paranoid, setup a server and send all your traffic through an ssh tunnel to the server so that it can't be read by anyone.
Basically, your worries are needless, but setting up the above will give you a nice little practice and education in Linux.
Cheers

---

### Post by mickwombat on 2010-08-31
yep...completely agree with Scorp123.  Just put a really good WPA password on your router.

---

### Post by Jonny87 on 2010-08-31
Thanks guys.
I have wpa2 with a long complex password so I'm reasonably confident that it won't be hacked any time soon. It was just a thought really, I guess I overlooked that a true hacker would be at the command line.

---

