---
title: "Having trouble Browsing a DHCP Network"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by jguillory on 2009-05-06
When I first install Ubuntu 9.04 I can click on Places->Network as a first order of business and I can see all of the computers on my small network.  We have a DHCP server from a router that just doles out IP address as they are needed (nothing special).  Hell, I get my IP address from the same server.  So, later on, I install Apache, MySQL, and PHP.  Now I'm no longer able to see the computers in the browser

I can add their IP addresses to my hosts file and give them a name, and then use that name to ping/browse to their share folders, if any.  That works fine.

But when I try to browse the network, no more computers pop up within Network - File Browser anymore.

It's getting late, I've been working on this all night and have even installed samba4 to make sure it wasn't anything within it's .conf file.  Below is the result of my [COLOR=Navy]testparm[/COLOR] result:

[COLOR=DarkRed]Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[/COLOR][COLOR=DarkRed]Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    interfaces = eth0
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = wins lmhosts bcast host
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    winbind enum users = Yes
    winbind enum groups = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers[/COLOR]

If there is any more information I can give I'll gladly do it.  Tomorrow I'm going to uninstall MySQL, Apache, and PHP.  See if I can get my browser back up and running.  If not.  Then darn!.  If so! Then I'll install one at a time until it doesn't work anymore.  I'm leaning towards apache though.

If anyone has any ideas, it would be greatly appreciated.

---

### Post by whewell on 2009-05-06
I'm having dns issues with Jaunty. And it was working fine for a while when I first installed it. I had no idea what's causing the problem. 

But thinking back now, I did install Apache2 a couple of days ago, among other things like wicd, java jdk, eclipse, etc. 

I'm gonna go home and uninstall apache later today. 

Looking forward to your results.

---

### Post by jguillory on 2009-05-06
Wow!  Its amazing how many more net issues have been posted in the last eight hours.   Oh well, I'm sure this post will get lost in the shuffle.

First off, thanks whewell for replying.

Well, I have uninstalled all things Apache, MySQL, PHP, and Samba (except for what is needed by Nautilus for viewing window's shares).  Nothing has improved.  I can now see a Mac computer that is on the network but not within the Windows Network (See Picture below)
[IMG]http://lh3.ggpht.com/_3QS48qxHMeo/SgGVl7B2nGI/AAAAAAAAAm0/Nc0B0DUiDz8/Screenshot-Network%20-%20File%20Browser.png[/IMG]
[http://lh3.ggpht.com/_3QS48qxHMeo/SgGVl7B2nGI/AAAAAAAAAm0/Nc0B0DUiDz8/s912/Screenshot-Network%20-%20File%20Browser.png](http://lh3.ggpht.com/_3QS48qxHMeo/SgGVl7B2nGI/AAAAAAAAAm0/Nc0B0DUiDz8/s912/Screenshot-Network%20-%20File%20Browser.png)

And if I try to browse the Windows Network I get the message below:
[IMG]http://lh3.ggpht.com/_3QS48qxHMeo/SgGVl8qmtHI/AAAAAAAAAm8/ASJkNc5Cb68/UnableToMount.png[/IMG]
[http://lh3.ggpht.com/_3QS48qxHMeo/SgGVl8qmtHI/AAAAAAAAAm8/ASJkNc5Cb68/UnableToMount.png](http://lh3.ggpht.com/_3QS48qxHMeo/SgGVl8qmtHI/AAAAAAAAAm8/ASJkNc5Cb68/UnableToMount.png)

What I'm beginning to think is that maybe I'm no longer in a Workgroup?  Could that be a possibility?

Any ideas would be greatly appreciated.  I sure would hate to have to back up  everything and re-install from scratch the op system and then install app / check network all over again.

Thanks for your help

---

