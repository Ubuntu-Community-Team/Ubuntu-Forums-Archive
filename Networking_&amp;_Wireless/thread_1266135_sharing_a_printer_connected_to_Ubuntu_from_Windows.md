---
title: "sharing a printer connected to Ubuntu from Windows XP on VirtualBox"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by Bensky5012 on 2009-09-14
I have recently installed Ubuntu and really like it, but I have one problem.  My printer, a Dell All In One 946, isn't supported by linux, so I was trying to connect my printer to my Windows xp guest os on VirtualBox.  I have followed this [guide]("http://www.giannistsakiris.com/index.php/2007/11/01/host-only-networking-for-virtualbox/") to set up a private network connection between the host and guest os.  My problem comes near the end of the directions, where it says:

"When Windows is started, go to Start &#8594; Settings &#8594; Network Connections.  Find the connection you previously added and open its Properties window. Highlight Internet Protocol (TCP/IP) and click Properties. Check the Use the following IP address option. In IP address enter 10.0.1.2. In Subnet mask enter 255.255.255.0. Leave Default gateway empty. It should look like this:"

I don't know what they are trying to say.  I didn't add any connections, so the only connection is the one for connecting to the internet. When I change it's IP and Subnet mask to what they say to change it to, my internet connection no longer works.  If I go back in and check "Obtain an IP address automatically." I can again access the internet.

Also, after turning off the firewall, I can not ping the guest os.

I'm trying to set this up on my laptop, and am accessing the internet through a router that is connected to my desktop downstairs.

Anyone have a clue as to what I am doing wrong?

---

