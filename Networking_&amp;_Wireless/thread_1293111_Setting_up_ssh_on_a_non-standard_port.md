---
title: "Setting up ssh on a non-standard port"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by sideburns on 2009-10-16
I run Fedora on a home LAN, and have my router set to forward Port 22 for ssh to my box so that I can safely move files in and out of my laptop when I'm not home.  Now, my sister wants the same access for her Ubuntu box.  After a bit of looking around, I've decided on a safe port that's not used for anything else as far as I can tell.  I know how to do the port forwarding, and that I've got to move her to a static IP on the LAN, but that's it.  What files on her box need editing, and how do I restart ssh to get it working, without rebooting?

---

### Post by sprouty on 2009-10-16
/etc/init.d/sshd reload

---

### Post by falconindy on 2009-10-16
You'll need to edit /etc/ssh/sshd_config. The port directive is right near the top of the file. After that, you can use the command sprouty posted (with sudo, of course) to restart the server.

---

### Post by sideburns on 2009-10-25
I tried restarting the service as suggested, but the command isn't there.  In fact, she didn't have the sshd server installed.  I've installed opensshd (I think; I'm not at that box right now.) but /etc/init.d/sshd still isn't there.  I've turned the server off with Services and restarted it and it kinda works.  That is, I can use ftp over the proper port from this box and connect, but it never gives me a list of files in her home directory as it should.  It just shows that it's connecting.  This is with gFTP, and I can see the message down at the bottom that it's connected, but it never gets the file list and I know this works, because I use it between my laptop and my desktop, both running Fedora, although that shouldn't be an issue.

---

### Post by Lars Noodén on 2009-10-26
> **sideburns said:**
>  but /etc/init.d/ssh[s]d[/s] still isn't there.


Strangely, it's **/etc/init.d/ssh**, not **/etc/init.d/ssh_d_**
I mistype that all the time myself, too. 

You can specify a non-standard port, if you *really* want to deviate from standards, by looking for the directives **Port** or **ListenAddress** in [/etc/ssh/sshd_config](http://manpages.ubuntu.com/manpages/jaunty/en/man5/sshd_config.5.html).  If your reason for wanting a non-standard port is that there are too many scans, then consider also throttling using the linux kernel's packet filter IP Tables or whitelisting using TCPd.

---

### Post by sideburns on 2009-10-26
I've got it working now.  Turns out there was a glitch on my end when I tested it.  I'm using a non-standard port, as I mentioned, because Port 22 is already forwarded to my Fedora box.  Setting that part up was, of course, trivial.  Alas, the command needed to restart the daemon is different in Ubuntu and I dislike rebooting for something so simple -- that's one of the things that drove me away from Windows, after all.

---

### Post by gnuisancev3 on 2009-10-26
They way you're working works jsut fine, but if i were you i'd handle this at the router level.

For so if i was at work or school and i ssh'd whatever.the.public.ip-is -p 222 

that port would forward to port 22 of my computer.

then whatever.the.public.ip-is -p 333 would forward to port 22 of my sister's computer.

This way all your settings are centralized on your router and you don't have to maintain a bunch of special config files on multiple boxes as your networking needs grow.

---

### Post by sideburns on 2009-10-26
Interesting, and a good idea in the general case.  I'll keep it in mind.  In this case, however, there's never going to be a reason for more than two boxes to need ssh access, so setting it up this way is easier.

---

