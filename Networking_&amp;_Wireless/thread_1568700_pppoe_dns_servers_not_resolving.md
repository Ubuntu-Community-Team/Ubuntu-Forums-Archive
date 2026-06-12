---
title: "pppoe dns servers not resolving"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by mur2 on 2010-09-05
Hi

I'm using ubuntu server edition (currently in virtualbox). I have set virtualbox network adapter to bridge mode, so I can connect directly to my ISP with pppoe. I used pppoeconf to set up the connection, connection worked fine... Until reboot.

I have set pppoeconf to connect pppoe at boot. It connects fine. I can ping ip addresses outside my network(so pppoe works). 
But if I try to do eg. ping google.com it cannot resolve hostname to ip address. 

The contents of /etc/pppoe/resolv.conf remain same after restart, that is:

nameserver [my isp dns server ip 1]
nameserver [my isp dns server ip 2]

If I run pppoeconf again, the connection works until another reboot.

How can I fix this?

---

### Post by mur2 on 2010-09-06
bump

any ideas?

---

### Post by Iowan on 2010-09-06
I haven't used pppoeconf, so I'm guessing...
Have you tried editing (or copying information to) */etc/resolv.conf*?

---

### Post by mur2 on 2010-09-06
Thanks for reply. I added my nameservers from /etc/ppp/resolv.conf to /etc/resolv.conf. I then rebooted. I still wasn't able to resolve hostnames and my nameservers were automatically wiped  from /etc/resolv.conf. I guess this resolv.conf is for main network interface only, not for pppoe.

Later I found out that if I reset the connection with poff and then pon dsl-provider, hostnames resolve properly. 

I think something is wrong with initializing pppoe connection at boot. 

Where is the script for starting pppoe at boot located?

Any other ideas how to fix this?

---

### Post by treesurf on 2011-01-23
I'm having this same issue.  I have to run pppoeconf every time I reboot to regain a working internet connection.  Is there any workaround for this?

---

### Post by dineshs on 2011-01-24
treesurf,
If you are using network manager try step-I  in
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
Reboot and see if [COLOR="Blue"]sudo pon dsl-provider[/COLOR] works fine

---

### Post by treesurf on 2011-01-24
dineshs, thanks for the suggestion.  I actually have found another tutorial on the web for manually editing the /etc/network/interfaces in a different way.

Here: [http://kvegroeg.wordpress.com/2010/07/02/command-pppoeconf-problem-at-reboot/](http://kvegroeg.wordpress.com/2010/07/02/command-pppoeconf-problem-at-reboot/)

Now I only need to "sudo pon dsl-provider" on reboot.  However, it would be nice not to have to do anything at all.  It's too bad the reboot option in pppoeconf doesn't work properly.

---

### Post by treesurf on 2011-01-24
OK, I tried editing /etc/network/interfaces as per your suggestion and the effect is the same as in the tutorial I linked (interesting!).  I then rebooted and tried to configure Network Manager to connect to the internet using the DSL connection but had no luck.  So I did sudo pon dsl-provider and I'm reconnected again.

Is there no way to make Network Manager do this automatically?


EDIT:  OK, figured out I was making a mistake with Network Manager.  Got it sorted out now, many thanks!!!

---

