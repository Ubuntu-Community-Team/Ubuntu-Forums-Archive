---
title: "Cannot ping hostname on home network"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by The Ratman on 2011-02-23
I have a home network of computers which includes Ubuntu, Mac and Windows computers. My D-Link router has a DHCP server enabled. It has a configuration page with a list of computer names and IP addresses which I'm pretty sure I didn't enter, so it seems all the computers are broadcasting their names OK to the router. If I ping IP addresses I get responses, but if I ping computer names it seems to resolve to an unfamiliar external website. I've entered a local domain name in my router's settings, but it still doesn't work to ping computer_name.domain_name.

---

### Post by blakep2 on 2011-02-23
make sure the extension is .local unless you have a weird setup.
so hostname.local
Also check if AP Isolation is enabled on your router.

---

### Post by The Ratman on 2011-02-24
> **blakep2 said:**
> make sure the extension is .local unless you have a weird setup.
so hostname.local
Also check if AP Isolation is enabled on your router.

Thanks! Adding .local worked right away - I can access a web server using
[http://computer_name.local/]("http://hostname.local/")

I didn't think that would work because I set the local domain name to something else, so I thought it would be [http://computer_name.domain_name/]("http://hostname.domain/") - I learned something!

It seems to only work if samba is installed on the machine I'm trying to ping.

---

### Post by The Ratman on 2011-02-25
I have a Moodle server set up on an Ubuntu computer on my school Windows network. At the moment I'm accessing it using its IP address e.g. [http://10.20.30.40/](http://10.20.30.40/). The name of the computer is moodle, so I was really hoping [http://moodle.local/](http://moodle.local/) could be used to access it, but it doesn't work. What could I do to access it using a name instead of an IP address - do I need to include the domain name perhaps?

---

### Post by samgurung on 2011-02-25
You would need to get some sort of DNS working..that would resolve the hostname to IP address.. As a rudimentary setup you could put an entry of the hostname of your moodle server and its IP address in the /etc/hosts file... 

You could even look at dnsmasq for a simple dns setup

---

### Post by The Ratman on 2011-02-25
> **samgurung said:**
> You would need to get some sort of DNS working..that would resolve the hostname to IP address.. As a rudimentary setup you could put an entry of the hostname of your moodle server and its IP address in the /etc/hosts file... 

You could even look at dnsmasq for a simple dns setup

I was kind of hoping it would happen automatically the way it does on my home network. The computer broadcasts its name and other computers can find it. There are literally hundreds of computers on our school network - I don't want to edit the 'hosts' file on each one - particularly if the IP address changes. I just wondered if I need to configure samba in a particular way so it's broadcasting the computer name on a specific domain, or perhaps address the computer differently - not [http://moodle/](http://moodle/).

---

