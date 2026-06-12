---
title: "Network Manager VPN connect not available (11.04)"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by exactiv on 2011-05-16
I've just installed Ubuntu 11.04 and am in the process of installing applications etc. I've just configured two PPTP VPN connections, but there is no option to connect them once configured. If I click on the network manager icon, select VPN Connections, I only have the option of Configure VPN. Disconnect VPN in greyed out. See images for examples.

Any ideas on how I go about connecting the VPN? I'm pretty new to Linux as you can probably make out.

Thanks in advance! :)

[IMG]http://dl.dropbox.com/u/3384529/Workspace%201_002.png[/IMG]

[IMG]http://dl.dropbox.com/u/3384529/Workspace%201_004.png[/IMG]

---

### Post by exactiv on 2011-05-16
Ok, after a reboot the VPN connections have appeared. Any reason why they weren't there to start?

---

### Post by exactiv on 2011-05-16
Looks like it's a bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/748486](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/748486)

---

### Post by syslin on 2011-06-09
Hello,
Right, you won't see the new VPN configuration if you had or changed the VPN connections you'll still the old configuration.
 
As a workaround I found that you don't need to rebbot your machine, just click on the NetworkManager icon remove the "Enable Network..." and then re-enable it and it will show you the up to date VPN connections.
 
Good luck,
Miki
[http://www.jaya.co.il](http://www.jaya.co.il)

---

### Post by exactiv on 2011-06-09
Hi syslin,

Thanks for the workaround - it works a treat.  I also found that ```
pkill nm-applet; nm-applet &
``` works too. Though, sometimes you have to execute it a couple of times to make it work.

Thanks again, your workaround it much easier.

-ex

---

