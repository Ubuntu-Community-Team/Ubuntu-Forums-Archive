---
title: "Iptables is not a service"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by johnny_ on 2011-05-22
Hi,
Last time I installed iptables on my ubuntu 8.04 (remote server). I installed it using apt-get install iptables. Installation has been completed but If I try to start iptables as service I get this prompt: iptables: unrecognized service. How can I add iptables to services? The point is I can add some rules to iptables but there is no file in /etc/init.d/*   /etc/network/* Nowhere. Its very important for me becouse I try to run another application and these show me that my ip tables is not running.  ( Sorry for my language skill [;)

---

### Post by AugustinMa on 2012-11-21
You get this error message because iptables is not set up as a service with ubuntu. 

I know this is an old question, but I found this thread a while ago while searching for the same problem. Since I now found the solution, I post it here hoping it will help others.

To start/stop the firewall, check out this tutorial, with script included:
[http://linux.overshoot.tv/wiki/server/setting_your_first_firewall_ssh](http://linux.overshoot.tv/wiki/server/setting_your_first_firewall_ssh)

---

### Post by Lars Noodén on 2012-11-22
You'd have to make an [upstart](http://upstart.ubuntu.com/cookbook/) script to load your iptables configurations.

However, the way that is officially recommended is to use UFW:

[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
[https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html)

---

### Post by AugustinMa on 2012-11-22
> **Lars Noodén said:**
> You'd have to make an [upstart](http://upstart.ubuntu.com/cookbook/) script to load your iptables configurations.

However, the way that is officially recommended is to use UFW:

[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
[https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html)

Does the latest ubuntu use upstart instead of init, now? 

About UFW, other people on another thread in this very board advised me to use iptables instead of the UFW frontend. I am glad I did. First, I learned about the underlying technology. Secondly, if I had followed the UFW tutorials, I would have locked myself out of my remote server. See the linked article above for details. Once I understand iptables much more, I may reconsider using UFW.

Thanks. :)

---

### Post by Lars Noodén on 2012-11-22
> **AugustinMa said:**
> Does the latest ubuntu use upstart instead of init, now? 

About UFW, other people on another thread in this very board advised me to use iptables instead of the UFW frontend. I am glad I did. First, I learned about the underlying technology. Secondly, if I had followed the UFW tutorials, I would have locked myself out of my remote server. See the linked article above for details. Once I understand iptables much more, I may reconsider using UFW.

Thanks. :)

I also prefer iptables to UFW, even if the official way is now UFW.

About Upstart, yes, the new versions of Ubuntu use it instead of System V scripts.  Overall it is probably an improvement even if it does require reading documentation instead of just editing a familiar shell script.  Reading the Upstart cookbook helps.  'emit' and some of the other concepts become clearer after that.

---

### Post by AugustinMa on 2012-11-22
> **Lars Noodén said:**
> 
About Upstart, yes, the new versions of Ubuntu use it instead of System V scripts.  Overall it is probably an improvement even if it does require reading documentation instead of just editing a familiar shell script.  Reading the Upstart cookbook helps.  'emit' and some of the other concepts become clearer after that.

Thanks. I'll check the cookbook when I start using upstart. I had already read good things about upstart.

---

