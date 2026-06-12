---
title: "Choice for server firewall ?"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by wildem on 2006-06-20
Hi every1, 
I have a task of automating a linux server and have chosen the Ubuntu Dapper.
So far it's going great and I will have a task of choosing a firewall administration tool to run on the server. 
I have researched the lower level tools such as ipchains, iptables , netfilter and have the following question:

Which of these is a best fit to a command line/script driven environment where the admin can add/delete/change maybe archive rules? 
This tool eventually will be webform driven and accessed thrugh a shell script interface on the backend. It would have to be compatible with a possible Cable/Dsl/Ethernet connection and the server will most likely have multiple ethernet cards.

Any favorites and why? Maybe some suggestions of what to look for and such?

---

### Post by Ctrl+Alt+Del on 2006-06-20
ipchains is obsolote nowadays it was used in times of 2.2 kernels
iptables and netfilter is actually the same thing, or more specific they are two integral parts which work together.
what you are looking for is mostlikely a frontend for iptables, because iptables itself isn't all that comfy to use. It works like a charm but can be quite confusing at times.
I have used shorewall in the past which has always worked fine for me. It can be administrated through a webinterface via a webmin module. There are a more choices, i am sure; but my quest ended when i found shorewall.

---

### Post by encompass on 2006-06-20
iptables and ipchains should be ab le to do any of your needs when it comes to managing your firewall.
According to my understanding all firewall tools use ipchains and iptables at the source.  If you want to keeps things slim and powerful just use those too.  But you could install firestarter or netfilter.  It is all your option, that is the great thing about linux.

---

### Post by wildem on 2006-06-20
Great, I have went ahead and installed shorewall v3.0 from amongst other choices..
I have noticed a web admin module for webmin. This would be a good reference point to look further into this choice. 

Does anyone know if the webmin module for shorewall will be able to administer a the firewall on a remote computer, or will i have to install webmin and module on the remote computer as well?

Thanks,

---

### Post by Ctrl+Alt+Del on 2006-06-20
webmin has to run on the same computer as shorewall for the module to work.

---

### Post by encompass on 2006-06-20
ssh is the best way to manage this kind of information.  Heck... you could ssh in, then run w3m and view the sitein text mode.  Hahaha, I don't think I am the first person that had to do that.:grin:

---

### Post by jvl on 2006-06-21
You could give a shot to FwBuilder at [http://www.fwbuilder.org/](http://www.fwbuilder.org/) There's also a package in the apt repository. 

It's a GUI (checkpoint fw-1 like fwiw) that could generate iptables rules (as well as ipfilter etc.)

---

### Post by wildem on 2006-06-21
Thanks for the insights - I have chosen the shorewall approach and will be covering as much ground as possible to make the most use of it.
My current setup will not use the webmin package; i opted to simply edit the rules/policies files and own web forms for top level access.

I have noticed some great/simple things about the way it sets up and its access  editibility from sell scripts. I might post some question later on managing it.

thnx again,

---

### Post by Cyber Dog on 2006-06-21
I stumbled across this thread just now.  Not to toot my own horn, but I've written a tutorial on custom firewalls.  Its based on Debian, so you will need to make minor alterations to some of the examples for it to work with the latest Ubuntu releases, but most of the information still applies.

[http://www.cyberdogtech.com/firewalls/](http://www.cyberdogtech.com/firewalls/)

---

