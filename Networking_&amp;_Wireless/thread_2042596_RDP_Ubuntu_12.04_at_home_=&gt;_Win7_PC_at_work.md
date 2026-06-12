---
title: "RDP Ubuntu 12.04 at home =&gt; Win7 PC at work"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by The Bright Side on 2012-08-14
Hey guys,

this is driving me nuts. I'm about to spend a couple of months working from home, and for that, I need to log into my PC at work (or at least the company's terminal server) remotely.

My company's IT guy gave me the following to work with:

- A Remote Desktop Gateway (aka "TS Gateway") I can set up in Windows as follows:
[https://espace.cern.ch/winservices-help/Terminal%20Services/Remote%20Desktop%20Gateway/PublishingImages/RDG-image004.png](https://espace.cern.ch/winservices-help/Terminal%20Services/Remote%20Desktop%20Gateway/PublishingImages/RDG-image004.png)
[https://espace.cern.ch/winservices-help/Terminal%20Services/Remote%20Desktop%20Gateway/PublishingImages/RDG-image005.png](https://espace.cern.ch/winservices-help/Terminal%20Services/Remote%20Desktop%20Gateway/PublishingImages/RDG-image005.png)

- The name of the PC to connect to - to set up in Windows as follows:
[http://www.neowin.net/images/uploaded/remote-desktop-client-win7.PNG](http://www.neowin.net/images/uploaded/remote-desktop-client-win7.PNG)

Then, all I need are my user name and password. I tried this from my Windows 7 partition using mstsc and it worked without a single problem. Out of the box. Hats off to Windows.

But from Ubuntu? Forget it. I have the following problems:

[LIST]
[*]Remmina doesn't allow me to set the remote gateway, it only has an "SSH" tab where I can enable an SSH tunnel.
[*]On the "Basic" tab, I can define Server (I guess that's the PC name), user name and password as expected, but it also asks me for a domain. Is that the part before my user name? Like DOMAIN\username?
[*]No matter what data I feed into Remmina, it never, ever connects. When I only specify the target PC, I get "Unable to connect to RDP server [name]". When I specify the gateway in the SSH tab, I get a timeout.
[*]I tried vinagre and one other program (xrdp I think) and they give me the same options or less.
[*]My problem is that the Linux programs don't have the same options as mstsc, and I'm a dunce when it comes to network admin stuff. Is SSH the same as Remote Gateway Server?
[*]I can't even ping the two gateway servers our IT guy gave me. Is there something wrong with my ports? Why does it work flawlessly in Windows?
[/LIST]

Hope you can help me! I don't want to be stuck using Windows to accomplish this, but I have to say, it does work so much better than Ubuntu in this case. :-(

---

### Post by The Bright Side on 2012-08-14
Aaaaand solved. Turns out there's only one Linux app so far that supports TS Gateway.

[http://itap-mobile.com/desktop/rdp](http://itap-mobile.com/desktop/rdp)

Just tried. Works like a charm. Also affordable enough, at 20 Euros.
Thanks!

---

