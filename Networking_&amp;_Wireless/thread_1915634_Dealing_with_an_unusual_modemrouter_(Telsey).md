---
title: "Dealing with an unusual modem/router (Telsey)"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by soundcore on 2012-01-26
Hi folks,

The modem/router my ISP provided me with assigns an external IP address to every device in the home network. Every computer/phone etc. that connects to it either via network cable or wireless gets a static external IP.

When I check what is the gateway I get the same result - an external address (85.91.X.XXX - ifconfig, ipconfig) It doesn't do anything when entered in the browser address bar, neither does 192.168.1.1.

I understand when most people look up their gateway address, they get a local number; they also have a browser utility for configuring their device.

I'm trying to connect my Dreamcast console to the internet. It doesn't have a network adapter, only a phone line modem. In order for the console to access the web I have to connect it back-to-back to a computer with a phone line modem; Then configure the computer to share it's internet connection with the dreamcast via modem. Essentially I'm turning my Linux machine into an ISP.



These are the tutorials I'm following:

[http://www.dreamcast-scene.com/guides/pc-dc-server-guide-win7/](http://www.dreamcast-scene.com/guides/pc-dc-server-guide-win7/)
[http://www.youtube.com/watch?v=J6e4jYR9bLI#t=7m19s](http://www.youtube.com/watch?v=J6e4jYR9bLI#t=7m19s)
[http://ragol.homeunix.net/3.html](http://ragol.homeunix.net/3.html)
[http://www.ryochan7.com/blog/2009/07/11/pc-dc-server-guide-part-1-pc-side-configuration/](http://www.ryochan7.com/blog/2009/07/11/pc-dc-server-guide-part-1-pc-side-configuration/)


I have everything set up, the modem is detected on "ttyLS0". Mgetty, gnome-ppp installed correctly. I created a user account for the Dreamcast as well.

However I'm having difficulty figuring out what IP addresses I should enter in the following two files:



"/etc/ppp/options"
> 
debug
login
default-asyncmap
require-pap
proxyarp
ktune
#IP Addresses. Uncomment whichever one you wish to use
#router IP for internet browsing
ms-dns 192.168.1.1
#sylverant PSO server
#ms-dns 67.222.144.120


Where the line "ms-dns 192.168.1.1" (third from the bottom) should be my gateway, the INTERNAL address of my router.




The second file is
"/etc/ppp/options.ttyLS0"
> 192.168.1.101:192.168.1.105
netmask 255.255.255.0

Here I need to provide the internal address of the computer giving the connection **[SIZE="4"]:[/SIZE]** the IP address I would like to create for the Dreamcast which has to be "within the same subnet" as my PC.

The problem here is that the computer has an EXTERNAL address within the home network, therefore I can't create an address for the console. Or can I?


I'm a casual GNU/Linux user, so please correct me if I got something wrong.

---

