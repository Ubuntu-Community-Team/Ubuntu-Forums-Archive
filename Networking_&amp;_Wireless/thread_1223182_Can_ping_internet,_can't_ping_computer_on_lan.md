---
title: "Can ping internet, can't ping computer on lan"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by narnie on 2009-07-25
Hello,

I'm hoping someone here can help me with this.

I have a Linksys WRT160Nv2 with a wired Hardy box and a wireless Intrepid laptop box. From both boxes, I can ping the gateway (router) with a return. I can ping the net (ex: yahoo.com) just fine as well. Both are manually configured to have a static IP to the router. However, they can not ping each other. Also, my work laptop can only be set up as a DHCP client. It, too, can ping the net and the gateway (of course) but can't ping either the wired or wireless box nor can they ping it. Pinging 127.0.0.1 and pinging each computer's respective lan IP address returns a response. Just none of the other computers on the lan.

I have set the same thing up at my home with no problem, but this network (my sister's which I have set up myself) I can't get them talking.

I'm wanting to set them up so that I can ssh and vnc in as I do my home setup.

I have check to see if I can access one of these computers from the outside net address, but that is a no go (yes, port forwarding is set up appropriately) so no outside ssh nor vnc.

I can't ssh nor vnc from the lan (say the Hardy to the Intrepid box or the work windoz client vnc to the Hardy host).

What could be causing this isolation behavior? I have AP isolation turned off on the router, so that is not it.

It just seems so strange that they all access the net, but can't access each other nor can the net access them.

I'm not sure that it matters, but IP examples:
Gateway/router 192.168.1.1
Example Hardy 192.168.1.60
Example Intrepid 192.168.1.61
Windoz variable, but 192.168.1.100 to .109


UPDATE:
If I make the linux wireless laptop obtain IP info via DHCP and the same with the wired linux box, then all have the IP 192.168.1.100-102. The linux boxes can ping the windows computer, but the windows can't ping the linux boxes.

There are no firewalls set up on the linux boxes. The windoz computer works with my linux boxes at home no problem.

With thanks,
Nathan

---

### Post by dlmarti on 2009-07-25
tbh, this sounds like a router issue, but agreed its a little weird.

Here would be my suggestion:
1. install wireshark on the two Linux machines.
2. Disconnect from the router from the internet.
3. Shut off all firewall software.
4. run wireshark (as root, in promiscuous mode), on both machines
5. try pinging from both sides
6. try telneting to open ports from both sides
7. stop capture on the wireshark programs

Take a look at the files and see what you can see.  If your still stuck, upload the files to some site and post the links here.

Sorry I don't have an easier answer for you....

---

### Post by narnie on 2009-08-19
Turns out I stumbled on the solution for this myself. I had firehol installed for dansguardian/tinyproxy to filter the "nasties" for my sister's kids.

I was disabling firehol 3 weeks later for something and thought I'd test the computers' ability to be pinged. Lo and behold, it worked. It is because firehol was set to accept server traffic only for cups.

Please see this link for the solution and how to configure firehol to allow ping response, ssh, and other server requests.

[http://ubuntuforums.org/showthread.php?t=1242050]("http://ubuntuforums.org/showthread.php?t=1242050")

Narnie

---

