---
title: "Is there a default firewall installed"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by swerdna on 2009-06-26
I'm having trouble understanding the Ubuntu firewall. Can someone please correct my elementary understanding as I've set it out below:

[LIST=1]
[*]I think there's a firewall built into the kernel involving something called netfilter and iptables.
[*]Then I think there's only the userspace package "iptables" installed as a default mechanism to manipulate the kernel-based firewall.
[*]Most ppl install Firestarter to help them manipulate iptables and thus the firewall.
[/LIST]

Is it something like that?

Thanks
Swerdna

---

### Post by mcduck on 2009-06-26
Yes, all the tools and features to control network traffic are built into the kernel, you just need to give them some rules to work with to get a working firewall. This can be done by hand, but since the rules need to be loaded on every boot people usually either write a script to do the job, r use some existing firewall configuration tool.

But Firestarter isn't really recommended any more, it's been without any support for a while now. If you need a firewall you'd better use UFW (command-line tool, included by default) or Gufw (graphical interface for UFW).

Also it should be mentioned that unless you install some server software yourself, Ubuntu doesn't have any services running that would respond to incoming network connections and thus a firewall isn't needed.

---

### Post by swerdna on 2009-06-26
> **mcduck said:**
> Yes, all the tools and features to control network traffic are built into the kernel, you just need to give them some rules to work with to get a working firewall. This can be done by hand, but since the rules need to be loaded on every boot people usually either write a script to do the job, r use some existing firewall configuration tool.

But Firestarter isn't really recommended any more, it's been without any support for a while now. If you need a firewall you'd better use UFW (command-line tool, included by default) or Gufw (graphical interface for UFW).

Also it should be mentioned that unless you install some server software yourself, Ubuntu doesn't have any services running that would respond to incoming network connections and thus a firewall isn't needed.
Thanks for the reply and the clear explanation. I have Samba as a server and will be sharing for files and a printer. I will have a web server and vsftpd, plus I need to have xrdp and vnc servers running from time to time. I could have no firewall, but that would be a little incautious I think. So I'll look at UFW and Gufw. I had a peek at man ufw and was set back on my heels. I've apt got gufw and will see if that's a bit easier on my newbies nerves.

Thanks again

Swerdna

---

