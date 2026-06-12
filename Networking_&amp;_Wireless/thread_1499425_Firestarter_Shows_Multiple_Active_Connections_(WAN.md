---
title: "Firestarter Shows Multiple Active Connections (WANTED: Adv. Technical Explaination)"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by jackthechemist on 2010-06-01
Hello all,

So, I searched the forum for "Firestarter Active Connections". Several threads mention it but don't adequately addressed.

When I open Firefox (homepage is still the default [http://start.ubuntu.com/9.10/](http://start.ubuntu.com/9.10/)) Firestarter shows the following two connections:

C1
Dest: 91.189.90.40 Host: avocado.canonical.com Port: 80

C2
Dest: 209.85.225.147 Host: iy-in-f147.1e100.net Port: 80

And after about 15 seconds of starting at my homepage two more appear:

C3
Dest: 209.85.225.190 Host: iy-in-f190.1e100.net Port: 443

C4
Dest: 209.85.225.138 Host:iy-in-f138.1e100.net Port: 80

Then after about 45 seconds the the first two terminate.

If anyone out there can give me an advanced verbose wordy highly technical explanation of why this all happens I would we very grateful. If you can explain this without using metaphors or analogies even better!

I've tested this several times. Sometimes the low level domains (the 'avacado' and 'iy-in-fxxx' parts in my example above) change but all else is generally the same. I've also noticed that other websites will often cause 6+ active connections to appear!

My guess is that the different parts of the webpage are coming from different servers, thus the various connections...

Thanks in advance!

Jack

---

### Post by capscrew on 2010-06-01
Read about it [**_here_**]("http://www.pcmech.com/article/the-mysterious-1e100-net/").

---

### Post by jackthechemist on 2010-06-05
Yes, it appears that 1e100 is a google domain and is probably harmless. Interesting post.

I've managed to gather that a single website allows multiple connections so that separate page resources can be downloaded via individual channels, but what I would like to know is:

1) How to I know which host is sending me which resource? Knowing who the 1e100 domain belongs to does not inform me of its exact purpose. What am I downloading from it? Is it javascript? css? something else?

2) I would like to configure my firewall to include the specific resource I'm getting from each host and to color code each active connection according to the webpage they belong to. I think I could handle the GUI programming but how can I find this information? A whois lookup doesn't tell me what I need to know :\ I hope packet sniffing is NOT the only answer, I would prefer to conserve my resources.

???

---

### Post by capscrew on 2010-06-06
> **jackthechemist said:**
> Yes, it appears that 1e100 is a google domain and is probably harmless. Interesting post.

I've managed to gather that a single website allows multiple connections so that separate page resources can be downloaded via individual channels, but what I would like to know is:

1) How to I know which host is sending me which resource? Knowing who the 1e100 domain belongs to does not inform me of its exact purpose. What am I downloading from it? Is it javascript? css? something else?

The article did explain what the Google "resources" are.  The article also explains how to turn the resources off if you want to.  These appear to be enhancements to the basic browser.

These types of connections can also be from scripts embedded in the web page you have requested.  These can be Java or javascript or even embedded graphics files.  CSS is really only used for formatting the web page.> 

2) I would like to configure my firewall to include the specific resource I'm getting from each host and to color code each active connection according to the webpage they belong to. I think I could handle the GUI programming but how can I find this information? A whois lookup doesn't tell me what I need to know :\ I hope packet sniffing is NOT the only answer, I would prefer to conserve my resources.

???
If you want the services off then turn them off.  If you don't want any scripts then turn off Java and javascript.  Remember that what you are seeing are outbound connections (e.g the script is "calling home").  I don't see any danger other than your lack of control.

I think it is important to note that the ports in question are for HTTP and HTTPS. By blocking these ports you will not be able to request web pages. So while it might achieve your goal, it will stop you from using the internet also.

---

### Post by jackthechemist on 2010-06-10
Hm. Well I ended up removing Firestarter. Reason being that even when it displayed zero policies entered, ufw showed 2 rules and iptables showed multiple pages of rules!    I couldn't justify using a GUI that doesn't accurately display system information and promptly removed it.    Besides, there are other ways to query active connections (netstat I believe) whose output I can pipe wherever I please, which is more flexible anyways.  I am having some difficulty interpreting the output from nmap with regard to the ufw rules. I've got ufw set to deny by default except for TCP and UDP for port 80 and 443 (needed for web browsing) but nmap is indicating that I have other ports open... I think I will make a plea for elucidation in a new thread though :P as the multiple connections in Firestarter is no long a concern to me.    Thanks for your input.

---

