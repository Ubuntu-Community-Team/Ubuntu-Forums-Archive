---
title: "user with no internet access"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by bwv539 on 2010-11-17
I would like to set up a user account with no network access. Reason is that sometimes my little daughter plays with the computer (for example watching movies on dvd's) and I want to prevent internet access in case she plays unattended. 
Is there a simple way to do that? 
I am using ubuntu 10.04.
Thank you

---

### Post by uncaspi on 2010-11-17
There are may ways to do it. You could put a rule in iptables and turn on the firewall. And maybe someone out there have a shell script that blocks for internet. I think the easiest way is to log in to her account and remove the firefox icon on the panel. Right click icon and remove.

---

### Post by SeijiSensei on 2010-11-17
Assuming that the box isn't set up to obtain an IP at startup or uses a static IP, I'd just remove network-manager from the panel on her desktop.  You might want to make some files read-only in her configuration if you think she has the smarts to turn the network on manually or restore network-manager using a Terminal.   I use KDE so I can't tell you which files you'd need to lock down for GNOME, though.  Perhaps others can help with that.

---

### Post by sedawk on 2010-11-17
I guess when you say network access you mean surfing the
web with a browser.

What you can try is to configure the browser of our
daughter's account (e.g. firefox) to use a proxy server.
Then try to set the files to read only (or even change
ownership of the files but keep them world readable).
Now try to disable the proxy and see if the browser allows
to change that setting although the config file is write protected.

What you can do is to really setup a proxy on the local machine
that uses a whitelist, so your daughter can browse the web but
only sites that are "whitelisted" in the file.

---

### Post by spiky001 on 2010-11-17
Could you just set up a user account with no network/internet

---

