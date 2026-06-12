---
title: "Cisco vpnc 'yes/no' prompt connection problems"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by ben@kietzman.org on 2010-06-10
Quite a while back I tried using the network-manager-vpnc, but at the time it didn't support IP compression.  So up until a few days ago I had been using the Cisco VPN Client, and it worked fine.  Lately however, it has been causing the system to freeze up.  So I decided to try the vpnc route again.  I was pleased to find that it now supports IP compression.  However, I am still running into a problem with it.

Under the Cisco VPN client it asks for my username/password and then displays a connect banner followed by a "Do you wish to continue? (y/n):" prompt.  That's all fine and dandy with the Cisco VPN client.  You answer Y and you are up and running.

When running vpnc, I do it from the command prompt so I can see more information.  It asks for my username/password and displays a connect banner, but it does not display the y/n prompt.  The software then hangs for a little bit (around 20 - 30 seconds).  Then it displays "vpnc-connect: no response from target" and puts me back at the prompt.  During that time it did swap out the contents of /etc/resolv.conf with the VPN information.  So I know it is getting partially there.  My hunch is that it doesn't know how to handle the y/n prompt and then the remote end times out and drops the connection.

Any help would be appreciated.  I would prefer to figure out the vpnc prompt issue rather than figure out the Cisco VPN Client freezing issue.

But in case anyone wants to know.  The Cisco VPN client can run beautifully for any random amount before freezing the whole system. I've seen it freeze up after 5 minutes and up to 2 hours.  I'm not sure what's causing it.

---

### Post by adolbr on 2011-01-10
I have the exact same issue that "ben@kietzman.org" has. The connection just hangs waiting for an answer to the prompt "Do you wish to continue? (y/n):" So, I'm working with Cisco Systems VPN Client Version 4.8.01 (0640) on Ubuntu Lucid (10.04), Linux 2.6.32-26-generic (without the freeze issue though =)).

---

### Post by adolbr on 2011-01-10
Repeated reply... Edited/Deleted. (Messages #3, #4 and #5 were the same as message #2. It doesn't allow me to delete)

---

### Post by adolbr on 2011-01-10
Repeated reply... Edited/Deleted.

---

### Post by adolbr on 2011-01-10
Repeated reply... Edited/Deleted.

---

### Post by ben@kietzman.org on 2011-05-11
Looks like the Cisco VPN client no longer works under the new Ubuntu 11.04 Natty Narwhal release.  I'm going to see if I can patch the vpnc package to correctly handle a prompt.

---

### Post by ben@kietzman.org on 2011-10-17
The Cisco VPN client stopped working under Ubuntu 11.10 due to the new 3.* kernel release.  However, it was an easy fix.  You must update the driver_build.sh, vpnclient_init and vpn_install scripts.  You will find "2.[56].*)" defined in each file.  Simply change those lines to be "2.[56].* | 3.*)" in order to implement the new 3.* kernel.

---

### Post by unkemptwolf on 2011-11-03
Did you ever have any luck getting the network-manager-vpnc working with the prompt? I'm having the same issue, and I didn't see a bug report about it in Launchpad. I wanted to make sure there wasn't an easy fix before I reported it.

---

### Post by ben@kietzman.org on 2012-03-27
Sorry for getting back to you so late on this.  I just tried it again and the network-manager-vpnc still does not work with the prompt.

---

