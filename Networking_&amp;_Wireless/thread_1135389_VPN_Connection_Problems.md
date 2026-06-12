---
title: "VPN Connection Problems"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by hafbaked on 2009-04-24
Currently running jaunty, with vpnc version 0.5.3-1. 

When I had gnome's network manager setup, I installed its vpnc plugin, and setup my vpn connection.  It worked, and I was able to connect no problems, from both wireless and wired connections.   I also setup a vpnc config manually, and was not able to connect.  At the time I didn't think much of it, as I was happy with using nm. 

After a week or so, nm stopped being able to connect to my wireless network.  No changes had been done, to either my laptop or network.  So I decided to switch to wicd.  Wicd connects to my wireless network without problems.  Unfortunately it doesn't have vpn support. So I've got to run vpnc manually.   At this time, it is still not working. 

I do the following: 

sudo vpnc-connect work.conf
Enter password for xxx@xxxxxxxxx: 
vpnc-connect: no response from target

I see the following in syslog:

 kernel: [ 5241.419063] tun: Universal TUN/TAP device driver, 1.6
 kernel: [ 5241.419070] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
 kernel: [ 5241.420590] tun0: Disabled Privacy Extensions

Entries in my work.conf file:

IPSec gateway xxx
IPSec ID xxxx
IPSec secret xxxx
Xauth username xxxx

Exact same details as I had entered into nm-vpnc and worked.  After some searching, it was suggested to also add: 

NAT Traversal Mode cisco-udp

To the conf file. Which I also did, but it is the same result.  Any ideas what the nm plugin might be doing that would be different?  Perhaps more options like the "NAT Traversal" one?

Edit:    I've also installed a couple of older versions from source, no luck though.

---

### Post by svaens on 2009-04-24
I don't know much about it all myself (being just a user), 
but i use shrew soft vpn for my vpn needs. 

As of jaunty (coming from Hardy) I can also no longer connect. 

Related?

---

### Post by SabreWolfy on 2009-04-24
PPTP VPN works for me in Hardy but is broken in Intrepid and Jaunty.

Edit: For what it's worth, I found a solution to PPTP VPN in Jaunty (and presumably Intrepid too). Link [here]("http://ubuntuforums.org/showthread.php?t=1136020").

---

### Post by gabrielson on 2009-06-26
Hello,

I have the very same problems with vpnc and all the solutions I googled didn't work.
I actually use Fedora but I joined this forum because this is really an important issue to me.

I send the logs I captured with "strace" to the vpnc-devel mailing list, still waiting for a response... 

There is a timeout signal before the response "vpnc: no response from target". I checked on another machine and the exchange of messages appears in a really different order. Maybe it is a stupid guess, maybe my current machine is to fast and the protocol is missing something... 

The problem seems to be tricky because other people with the same distribution and the same version of vpnc can actually use it.

Does any of you found out a solution? Off course I cannot rely on any of Ubuntu packages. If only this is a configuration problem...

---

### Post by gregh7470 on 2009-06-29
I'm currently using Jaunty and it took me forever to get the VPN in Network Manager to work.  This is what I did:
I went here and got the 'new' Network Manager:
[https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa)
I added the new sources.lst entries as well as the PGP Key  and updated the network manager - this called for a reboot..
Then I installed network-manager-pptp which called for pptp-linux as a dependency.
I'm VPN'ing to a MS network and configured the VPN connection as follows:
Checked  Connect Automatically, 
Filled in Gateway, user name and password.
Then I selected the Advanced button and removed the check mark from EAP and below it selected Use Point-to-Point Encryption (MPPE).
(thanks to [virkang]("http://ubuntuforums.org/member.php?u=822014") for this info - he posted the info on this [thread]("http://ubuntuforums.org/showthread.php?t=1136020"))
I've connected and disconnected several times and it works just fine.
Hope this helps.

---

