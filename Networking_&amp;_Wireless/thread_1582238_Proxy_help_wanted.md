---
title: "Proxy help wanted"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by limotux on 2010-09-26
Hi...
I hope you can help or guide me wit this issue.
My service  provider is closing almost all VoIP and censoring lots of websites (even  google translated search). I've been researching for a long time to try  overcome this.

Please correct me if I'm wrong.
The solution  might be setting up a proxy on my laptop to redirect all my traffic  through it in a "shielded" tunnel that my ISP can't restrict, so I can  use the internet as it should be used freely.
Is my conclusion right?

If so, how can I do that.

I'll appreciate any help in this.

p.s.  I'm not interested in proxy websites, because it does not enable me to  use VoIP and some other websites and services, downloads... etc., the  main thing is that I want to beat my ISP

---

### Post by HermanAB on 2010-09-26
Howdy,

If you want full control then you need to rent a Linux server in a free country.  Run sshd on it and set up a Sox proxy with ssh from your laptop.  Then tell your browser and Skype to use the proxy.

So your first problem is that you got to get a server.  If you want details for soxifying Skype, send me a message.

---

### Post by limotux on 2010-09-26
thanks HermanAB

This might be a good solution for browsing. There are lots of free websites for such purpose.

I remember some time ago a friend gave me a small app that runs under windoze and it just puts the computer out of the control of the ISP.

From my readings for quite some time I found lots about setting up a proxy on your box to do the same... is this right? how-to?

---

### Post by SeijiSensei on 2010-09-26
> **HermanAB said:**
> If you want full control then you need to rent a Linux server in a free country.  Run sshd on it and set up a Sox proxy with ssh from your laptop.  Then tell your browser and Skype to use the proxy.

A cheaper solution is to rent a virtual machine.  Take a look at [www.linode.com](www.linode.com).  You can set up a 512M Linux machine for $20/month.

I'd use OpenVPN as a solution.  Set up a tunnel between your computer and the VM, then make the remote host's tunnel address your default gateway.  All traffic will then go through the tunnel to the remote VM, then out onto the Internet.

Perhaps your friend had a copy of the [Tor]("http://www.torproject.org/") client?  If so, please don't use Tor for personal browsing and the like (and *never* for torrents).  Tor was designed to help human rights activists in authoritarian regimes communicate anonymously with the outside world.

---

### Post by limotux on 2010-10-01
Thanks a lot SeijiSensei,

This really sounds great, reasonable price and good features. I had a quick look at the link!
I'll study it thoroughly.

I'll look as well for other virtual servers/machines **hoping to find something free to experiment with. If you have any free please let me know**.

I'll be considering to use it for online backup, get my own domain name and have my own email server.

By the way, what you think if I used an old pc at a friend in a free country, get a fixed IP and use it for that purpose? Of course the upload speed there should be 256 at least to be able to enjoy that speed as a minimum on my laptop wherever I get a connection.

By the way, I don't use TOR. The software I mentioned was a different windoze software but I don't remember it's name, and I really don't care because I'm on linux.

Thanks again for your help.

---

